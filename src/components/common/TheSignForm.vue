<template>
  <a-form
    layout="horizontal"
    :form="form"
    @submit="handleSubmit"
    class="merge-signin__form"
  >
    <a-form-item
      class="merge-signin__form-item"
      :validate-status="emailError() ? 'error' : ''"
      :help="emailError() || ''"
      label="Email"
    >
      <a-input
        class="merge-signin__input"
        :class="{ approved: (getEmailValue() === undefined || '' || null ) ? emailComplete : !emailComplete }"
        v-decorator="[
          'email',
          {
            rules: [
              {
                type: 'email',
                message: 'Invalid email',
              },
              {
                required: true,
                message: 'Please input your E-mail!',
              },
            ],
          },
        ]"
      />
    </a-form-item>
    <a-form-item
      class="merge-signin__form-item"
      :validate-status="passwordError() ? 'error' : ''"
      :help="passwordError() || ''"
      label="Password"
    >
      <a-input
        class="merge-signin__input merge-signin__input--pass"
        :class="{ approved: (getPassValue() === undefined || '' || null ) ? passComplete : !passComplete }"
        v-decorator="[
          'password',
          {
            rules: [
              {
                required: true,
                message: 'Please input your Password!',
              },
              {
                message: 'Invalid format too short',
                min: 5,
              },
            ],
          },
        ]"
        type="password"
      >
      </a-input>
      <a href="#" class="merge-signin__forget-link">Forgot your password?</a>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        :disabled="hasErrors(form.getFieldsError())"
        class="merge-signin__login-btn"
      >
        Sign in
      </a-button>
    </a-form-item>
  </a-form>
</template>

<script>
function hasErrors(fieldsError) {
  return Object.keys(fieldsError).some((field) => fieldsError[field]);
}
export default {
  data() {
    return {
      hasErrors,
      form: this.$form.createForm(this, { name: "horizontal_login" }),
      emailComplete: false,
      passComplete: false,
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.form.validateFields();
    });
  },
  methods: {
    emailError() {
      const { getFieldError, isFieldTouched } = this.form;
      return isFieldTouched("email") && getFieldError("email");
    },
    passwordError() {
      const { getFieldError, isFieldTouched } = this.form;
      return isFieldTouched("password") && getFieldError("password");
    },
    getEmailValue() {
      const { getFieldValue } = this.form;
      return getFieldValue("email");
    },
    getPassValue() {
      const { getFieldValue } = this.form;
      return getFieldValue("password");
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log("Received values of form: ", values);
        }
      });
    },
  },
};
</script>