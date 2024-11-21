<template>
    <q-page padding>
      <div class="q-gutter-md">
        <q-card
          v-for="job in jobs"
          :key="job.id"
          class="my-card hoverable"
          @click="viewJobDetails(job)"
        >
          <q-card-section>
            <div class="text-h6">{{ job.title }}</div>
            <div class="text-subtitle2">{{ job.company }} - {{ job.location }}</div>
            <div class="text-caption">{{ job.description }}</div>
          </q-card-section>
          <q-card-actions align="right">
            <q-btn flat color="primary" label="View Details" />
          </q-card-actions>
        </q-card>
      </div>
  
      <JobDetailsModal
        v-if="selectedJob"
        :job="selectedJob"
        @close="selectedJob = null"
      />
    </q-page>
  </template>
  
  <script>
  import JobDetailsModal from "components/JobDetailsModal.vue";
  
  export default {
    name: "HomePage",
    components: { JobDetailsModal },
    data() {
      return {
        jobs: [
          {
            id: 1,
            title: "Frontend Developer",
            company: "Tech Corp",
            location: "Goa, India",
            description: "Build responsive web UIs using Vue.js.",
          },
          {
            id: 2,
            title: "Backend Developer",
            company: "Innovate Ltd",
            location: "Remote",
            description: "Develop and maintain RESTful APIs.",
          },
        ],
        selectedJob: null,
      };
    },
    methods: {
      viewJobDetails(job) {
        this.selectedJob = job;
      },
    },
  };
  </script>
  
  <style>
  .hoverable {
    cursor: pointer;
    transition: transform 0.2s;
  }
  .hoverable:hover {
    transform: scale(1.03);
  }
  </style>
  