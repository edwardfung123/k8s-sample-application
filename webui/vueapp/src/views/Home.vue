<template lang="pug">
.home.section
  .container
    .columns.is-centered
      .column.is-full.has-text-centered
        h1 
          img(src='@/assets/icons8-xls-100.png')
          | Excel for the win!
    .columns.is-centered
      .column.is-full
        form(@submit.prevent="onSubmit")
          .field.is-horizontal
            .field-label.is-normal
              label.label Email:
            .field-body
              .control
                input(type="email", required=true, v-model="email")
          .field.is-horizontal
            .field-label.is-normal
              label.label File:
            .field-body
              .control
                input(type="file", required=true, ref="csvFile")
          .field.is-horizontal
            .field-label
            .field-body
              .control
                button.button.is-link(:disabled="isSubmitDisabled") Submit
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
const axios = require('axios');

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data() {
    return {
      email: '',
      isSubmitDisabled: false,
    };
  },
  methods: {
    onSubmit() {
      alert('submit form!');
      this.isSubmitDisabled = true;
      window.setTimeout(() => {
        let fd = new FormData();
        console.log(fd);
        console.log(this.$refs.csvFile);
        console.log(this.$refs.csvFile.files);
        fd.append('email', this.email);
        fd.append('csv', this.$refs.csvFile.files[0]);

        let req = axios.post('/apis/submit_request', {
          data: fd,
        });

        req.then((res) => {
            alert('Submitted');
          })
          .catch((err) => {
            alert('Failed to upload!');
          })
          .finally(() => {
            this.isSubmitDisabled = false;
          });
      }, 2000);
    }
  }
}
</script>

<style lang="scss">
form {
  width: 400px;
  margin-left: auto;
  margin-right: auto;
}
</style>
