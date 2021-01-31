<template>
  <div class="merge-signin__registration-link-wrapper">
    <a
      @click="showModal"
      class="merge-signin__registration-text merge-signin__registration-text--link"
    >
      Sign up now</a
    >
    <a-modal
      title="Sign up"
      :visible="visible"
      :confirm-loading="confirmLoading"
      @ok="handleOk"
      @cancel="handleCancel"
    >
      <p>{{ ModalText }}</p>
    </a-modal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ModalText: "Here can be some registration form or auth from google etc.(for example)",
      visible: false,
      confirmLoading: false,
    };
  },
  methods: {
    showModal() {
      this.visible = true;
    },
    handleOk() {
      this.ModalText = "Loading...";
      this.confirmLoading = true;
      setTimeout(() => {
        this.visible = false;
        this.confirmLoading = false;
      }, 2000);
    },
    handleCancel() {
      console.log("Clicked cancel button");
      this.visible = false;
    },
  },
};
</script>