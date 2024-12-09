<template>
    <div class="parent-form-container">
      <h1 class="form-title">Stylish Dynamic Form</h1>
      <ChildForm :fields="formFields" @Form-Submit="HandleformSubmit" />
    </div>
  </template>
  
  <script>
  import ChildForm from './ChildForm.vue';
  
  export default {
    name: 'ParentForm',
    components: { ChildForm },
    data() {
      return {
        formFields: [
          { name: "username", label: "Username", type: "text", placeholder: "Enter your username" },
          { name: "email", label: "Email", type: "text", placeholder: "Enter your email" },
          { name: "role", label: "Role", type: "select", options: ["Admin", "User", "Guest"] },
        ],
      };
    },
    methods: {
      HandleformSubmit(formData) {
        console.log("Form submitted:", formData);
        alert(JSON.stringify(formData, null, 2));
      },
    },
  };
  </script>
  
  <style scoped>
  .parent-form-container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
  }
  
  .form-title {
    font-size: 2rem;
    margin-bottom: 20px;
    color: #4CAF50;
    font-family: 'Arial', sans-serif;
  }
  </style>
  