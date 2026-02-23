<template>
  <header class="header">
    <div class="logo">
      <h2>Student Information System</h2>
      <span>Academic Dashboard</span>
    </div>

    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/students">Students</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent"
};
</script>

<style scoped>
.header {
  background: linear-gradient(90deg, #1f3a8a, #4f46e5);
  padding: 20px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo h2 {
  color: #ffffff;
  font-size: 22px;
}

.logo span {
  color: #dbeafe;
  font-size: 13px;
}

nav a {
  color: #ffffff;
  margin-left: 25px;
  font-weight: 500;
  position: relative;
}

nav a::after {
  content: "";
  width: 0;
  height: 2px;
  background: #ffffff;
  position: absolute;
  left: 0;
  bottom: -4px;
  transition: width 0.3s;
}

nav a:hover::after,
nav a.router-link-active::after {
  width: 100%;
}
</style>
