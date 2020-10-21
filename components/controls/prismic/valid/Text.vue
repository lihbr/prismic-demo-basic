<!-- HEALTH:UNKNOWN prismic-valid-text -->
<template>
  <prismic-valid-wrapper
    v-if="$prismic.isPreview && hasViolations"
    class="prismicValidText"
  >
    {{ message }}
  </prismic-valid-wrapper>
</template>

<script>
import PrismicValidWrapper from "~/components/controls/prismic/valid/wrapper.vue";

const messages = {
  NOT_EMPTY: ctx => "should not be empty",
  /* eslint-disable-next-line prettier/prettier */
  MIN_LENGTH: ctx => `should be longer or equal to ${ctx.minLength} character${ ctx.minLength > 1 ? "s" : ""}`,
  /* eslint-disable-next-line prettier/prettier */
  MAX_LENGTH: ctx => `should be shorter or equal to ${ctx.maxLength} character${ ctx.maxLength > 1 ? "s" : ""}`
};

export default {
  components: {
    PrismicValidWrapper
  },
  props: {
    field: {
      type: [String, Array],
      default: ""
    },
    fieldName: {
      type: String,
      default: "Field"
    },
    notEmpty: {
      type: Boolean,
      default: false
    },
    maxLength: {
      type: Number,
      default: -1
    },
    minLength: {
      type: Number,
      default: -1
    }
  },
  computed: {
    parsedField() {
      if (!this.field) {
        return "";
      } else if (typeof this.field === "string") {
        return this.field.trim();
      } else {
        return this.$prismic.asText(this.field).trim();
      }
    },
    violations() {
      const violations = [];

      if (this.notEmpty) {
        if (!this.parsedField) {
          violations.push("NOT_EMPTY");
        }
      }

      if (this.minLength >= 0 && !violations.includes("NOT_EMPTY")) {
        if (this.parsedField.length < this.minLength) {
          violations.push("MIN_LENGTH");
        }
      }

      if (this.maxLength >= 0) {
        if (this.parsedField.length > this.maxLength) {
          violations.push("MAX_LENGTH");
        }
      }

      return violations;
    },
    message() {
      return `${this.fieldName} ${this.violations
        .map(violation => messages[violation](this))
        .join(", ")}.`;
    },
    hasViolations() {
      return !!this.violations.length;
    }
  }
};
</script>
