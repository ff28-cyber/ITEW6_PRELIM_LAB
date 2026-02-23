<template>
  <div class="container">
    <h1>Student Directory</h1>

    <button @click="toggleMessage" class="btn">
      Display System Message
    </button>

    <p v-if="showMessage" class="message">
      System functioning normally.
    </p>

    <p v-if="loading" class="status">Loading student records...</p>
    <p v-if="error" class="error">{{ error }}</p>

    <StudentComponent
      v-for="student in students"
      :key="student.id"
      :name="student.name"
      course="Bachelor of Science in Information Technology"
      year="3rd Year"
    />
  </div>
</template>

<script>
import axios from "axios";
import StudentComponent from "../components/StudentComponent.vue";

export default {
  components: { StudentComponent },

  data() {
    return {
      students: [],
      loading: true,
      error: "",
      showMessage: false
    };
  },

  methods: {
    toggleMessage() {
      this.showMessage = !this.showMessage;
    }
  },

  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        this.students = response.data.map((student, index) => ({
          ...student,
          name: [
            "Juan Dela Cruz",
            "Maria Clara Santos",
            "Jose Rizal Mendoza",
            "Ana Patricia Reyes",
            "Mark Anthony Villanueva",
            "John Paul Bautista",
            "Kristine Mae Garcia",
            "Michael Angelo Cruz"
          ][index % 8]
        }));
        this.loading = false;
      })
      .catch(() => {
        this.error = "Failed to load student records.";
        this.loading = false;
      });
  }
};
</script>

<style scoped>
h1 {
  font-size: 28px;
  color: #1f3a8a;
  margin-bottom: 20px;
}

.btn {
  background: linear-gradient(90deg, #4f46e5, #6366f1);
  color: #ffffff;
  border: none;
  padding: 12px 18px;
  border-radius: 10px;
  font-size: 14px;
  cursor: pointer;
  margin-bottom: 15px;
  box-shadow: 0 6px 15px rgba(79, 70, 229, 0.4);
}

.btn:hover {
  opacity: 0.9;
}

.message {
  color: #065f46;
  margin-bottom: 15px;
}

.status {
  color: #374151;
}

.error {
  color: #b91c1c;
  font-weight: 500;
}
</style>
