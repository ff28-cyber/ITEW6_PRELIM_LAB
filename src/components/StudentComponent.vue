<template>
  <div class="student-card">
    <h3>{{ name }}</h3>
    <p><strong>Course:</strong> {{ course }}</p>
    <p><strong>Year Level:</strong> {{ year }}</p>
  </div>
</template>

<script>
export default {
  name: "StudentComponent",
  props: {
    name: String,
    course: String,
    year: String
  }
};
</script>

<style scoped>
.student-card {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(6px);
  border-radius: 14px;
  padding: 20px;
  margin-bottom: 18px;
  border-left: 6px solid #4f46e5;
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.12);
  transition: transform 0.3s, box-shadow 0.3s;
}

.student-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 18px 35px rgba(0, 0, 0, 0.2);
}

.student-card h3 {
  color: #1f2937;
  font-size: 20px;
  margin-bottom: 10px;
}

.student-card p {
  font-size: 14px;
  margin: 4px 0;
}
</style>
