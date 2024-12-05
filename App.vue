<template>
  <div id="app">
    <h1>Lessons</h1>
    <ul>
      <li v-for="lesson in lessons" :key="lesson._id">{{ lesson.title }}</li>
    </ul>
  </div>
</template>

<script>
import apiClient from './axiosConfig';

export default {
  name: 'App',
  data() {
    return {
      lessons: [],
    };
  },
  methods: {
    async fetchLessons() {
      try {
        const response = await apiClient.get('/collections/Lessons');
        this.lessons = response.data;
      } catch (error) {
        console.error('Error fetching lessons:', error);
      }
    },
  },
  mounted() {
    this.fetchLessons();
  },
};
</script>

<style scoped>
</style>
