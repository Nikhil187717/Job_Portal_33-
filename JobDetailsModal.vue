<template>
    <q-dialog v-model="open">
      <q-card style="width: 500px;">
        <q-card-section>
          <div class="text-h6">{{ job.title }}</div>
          <div class="text-subtitle2">{{ job.company }} - {{ job.location }}</div>
          <p>{{ job.description }}</p>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn flat color="primary" label="Apply Now" @click="applyNow" />
          <q-btn flat color="negative" label="Close" @click="close" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </template>
  
  <script>
  export default {
    name: "JobDetailsModal",
    props: ["job"],
    data() {
      return {
        open: true,
      };
    },
    methods: {
      close() {
        this.$emit("close");
      },
      applyNow() {
        this.$emit("apply", this.job);
      },
    },
  };
  </script>
  