<template>
    <q-dialog v-model="open">
      <q-card style="width: 400px;">
        <q-card-section>
          <div class="text-h6">Apply for {{ job.title }}</div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="submitForm" ref="form">
            <q-input
              v-model="formData.name"
              label="Name"
              required
              class="q-mb-md"
            />
            <q-input
              v-model="formData.email"
              label="Email"
              type="email"
              required
              class="q-mb-md"
            />
            <q-uploader
              v-model="formData.resume"
              label="Upload Resume"
              accept=".pdf,.docx"
              class="q-mb-md"
              required
            />
            <q-btn label="Submit" type="submit" color="primary" />
          </q-form>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn flat color="negative" label="Close" @click="close" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </template>
  
  <script>
  export default {
    name: "JobApplicationForm",
    props: ["job"],
    data() {
      return {
        open: true,
        formData: {
          name: "",
          email: "",
          resume: null,
        },
      };
    },
    methods: {
      close() {
        this.$emit("close");
      },
      submitForm() {
        if (this.$refs.form.validate()) {
          alert("Application Submitted Successfully!");
          this.close();
        }
      },
    },
  };
  </script>
  