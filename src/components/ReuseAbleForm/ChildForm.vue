<template>
    <form class="stylish-form" @submit.prevent="handleSubmit">
      <div v-for="field in fields" :key="field.name" class="form-group">
        <label :for="field.name" class="form-label">{{ field.label }}</label>
        <input
          v-if="field.type === 'text'"
          :type="field.type"
          :name="field.name"
          :placeholder="field.placeholder"
          v-model="formData[field.name]"
          class="form-input"
        />
        <select
          v-if="field.type === 'select'"
          :name="field.name"
          v-model="formData[field.name]"
          class="form-select"
        >
          <option v-for="option in field.options" :key="option" :value="option">
            {{ option }}
          </option>
        </select>
      </div>
      <button type="submit" class="form-submit-button">Submit</button>
    </form>
  </template>
  
  <script>
  export default {
    name: 'ChildForm',
    props: {
      fields: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
        formData: {},
      };
    },
    created() {
      this.fields.forEach((field) => {
        this.$set(this.formData, field.name, '');
      });
    },
    methods: {
      handleSubmit() {
        this.$emit('Form-Submit', this.formData);
      },
    },
  };
  </script>
  
  <style scoped>
  .stylish-form {
    background: #f9f9f9;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  .form-label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
    color: #333;
  }
  
  .form-input,
  .form-select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 1rem;
    box-sizing: border-box;
  }
  
  .form-input:focus,
  .form-select:focus {
    outline: none;
    border-color: #4CAF50;
    box-shadow: 0 0 3px #4CAF50;
  }
  
  .form-submit-button {
    display: block;
    width: 100%;
    padding: 10px;
    background: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .form-submit-button:hover {
    background: #45a049;
  }
  </style>
  