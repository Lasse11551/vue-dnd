<template>
    <nav class="navbar">
      <div class="navbar-content">
        <img src="@/assets/fysiofresh-logo-text.png" alt="Logo" class="logo">
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    name: 'NavbarItem'
  }
  </script>
  
  <style scoped>
  .navbar {
    width: 100%;
    background-color: white; /* Adjust background color as needed */
    padding: 10px 0; /* Padding for some breathing room */
  }
  
  .navbar-content {
    width: 100%;
    display: flex;
    justify-content: center; /* Center the content horizontally */
    align-items: center; /* Align vertically center */
  }
  
  .logo {
    height: 50px; /* Set the size of your logo */
  }
  </style>
  