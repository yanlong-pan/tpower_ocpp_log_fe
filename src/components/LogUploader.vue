<template>
    <div class="container">
      <textarea v-model="inputText" placeholder="Enter your text here"></textarea>
      <button @click="submitData">Submit</button>
      <div v-if="responseData" :class="['response', responseClass]">
        <h3>Response from API:</h3>
        <pre>{{ formattedResponse }}</pre>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        inputText: '',
        responseData: null,
        responseSuccess: null,
      };
    },
    computed: {
      formattedResponse() {
        return typeof this.responseData === 'object'
          ? JSON.stringify(this.responseData, null, 2)
          : this.responseData;
      },
      responseClass() {
        if (this.responseSuccess === true) {
          return 'success';
        } else if (this.responseSuccess === false) {
          return 'error';
        } else {
          return '';
        }
      },
    },
    methods: {
      async submitData() {
        try {
          const response = await fetch('http://localhost:3000/api/process-charger-sent-logs', {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json',
            },
            body: JSON.stringify(this.inputText),
          });
          const data = await response.json();
          this.responseData = data.message;
          this.responseSuccess = data.success;
        } catch (error) {
          console.error('Error:', error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px;
    max-width: 600px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  textarea {
    width: 100%;
    height: 100px;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    resize: none;
    font-size: 14px;
  }
  
  button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
    font-size: 16px;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  .response {
    margin-top: 20px;
    text-align: center;
    width: 100%;
    overflow: auto;
    white-space: pre-wrap;
    word-wrap: break-word;
  }
  
  pre {
    text-align: left;
    background-color: #f4f4f4;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    max-height: 400px;
    overflow-y: auto;
    white-space: pre-wrap;
    word-wrap: break-word;
  }
  
  .success pre {
    color: green;
  }
  
  .error pre {
    color: red;
  }
  </style>