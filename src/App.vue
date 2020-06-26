<template>
  <div id="app">
    <div class="img vue-image">
      <img alt="Vue logo" src="./assets/logo.png">
    </div>
    <div class="button">
      <button class="default" @click="showModal=!showModal">Click here to enable modal</button>
    </div>


    <!-- Modal -->
    <ModalComponent 
      v-if="showModal"
      :title="modalTitle"
      :body="modalBody"
      :height="'50rem'"
      :width="'50rem'"
      :successActionButtonTitle="successActionButtonTitle"
      :cancelActionButtonTitle="cancelActionButtonTitle"
      @modal-component="modalComponentActionHandler" 
    >
      <!-- <template v-slot:body>
        Slot Body
      </template> -->
    </ModalComponent>

    <div class="form">
      <div class="form-item form-title">
        <p>Enter Modal Title:</p>
        <input v-model="modalTitle" type="text" name="modalTitle" placeholder="Enter modal title here...">
      </div>
      <div class="form-item form-body">
        <p>Enter Modal Body:</p>
        <textarea v-model="modalBody" name="modalBody" placeholder="Enter modal body here..." cols="30" rows="10"></textarea>
      </div>
      <div class="form-item form-success-button">
        <p>Enter Modal Success Button Name:</p>
        <input v-model="successActionButtonTitle" type="text" name="successActionButtonTitle" placeholder="Enter modal success button name here...">
      </div>
      <div class="form-item form-cancel-button">
        <p>Enter Modal Cancel Button Name:</p>
        <input v-model="cancelActionButtonTitle" type="text" name="cancelActionButtonTitle" placeholder="Enter modal cancel button name here...">
      </div>
    </div>
  </div>
</template>

<script>
import ModalComponent from './components/ModalComponent';
export default {
  name: 'App',
  components: {
    ModalComponent
  },
  data() {
    return {
      showModal: false,
      modalTitle: `Modal title as a prop`,
      modalBody: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.`,
      successActionButtonTitle: 'Success',
      cancelActionButtonTitle: 'Close'
    };
  },
  methods: {
    modalComponentActionHandler(e) {
      if(!e) {
        // close modal
        this.showModal = false;
      }
    }
  }
}
</script>

<style>
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  vertical-align: baseline;
  box-sizing: border-box;
}

body {
  background: #3c369a;
  color: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 1rem;
}
.img, .button, pre {
  text-align: center;
}
button.default {
  margin: 1rem 0;
  border-radius: 5px;
  border: 1px solid black;
  padding: 0.5rem 1rem;
  background: #241f73;
  color: white;
  cursor: pointer;
}
.form {
  margin: auto;
  width: 20%;
}
.form .form-item {
  margin-top: 1rem;
  font-family: monospace;
}
.form .form-item p {
  text-align: left;
  padding: 0.5rem 0;
}
.form .form-item input, textarea {
  width: 115%;
  padding: 0.5rem;
  border-radius: 6px;
}
</style>
