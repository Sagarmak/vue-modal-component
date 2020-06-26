<template>
  <div class="modal-component">
    <div class="modal">
      <div class="modal-content">
        <div class="header">
          <span class="title">{{ title }}</span>
          <button @click="$emit('modal-component', false)">
            <i class="fas fa-times"></i>
          </button>
        </div>
        <div class="body">
          <div v-if="body">
            {{ body }}
          </div>
          <div>
            <slot name="body"></slot>
          </div>
        </div>
        <div class="footer">
          <button> {{ successActionButtonTitle }} </button>
          <button @click="$emit('modal-component', false)"> {{ cancelActionButtonTitle }} </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComponent',
  props: {
    title: {
      type: String,
      default: 'Modal Title',
      validator: (value) => value.length > 0
    },
    body: {
      type: String
    },
    height: {
      type: String,
      default: '100%'
    },
    width: {
      type: String,
      default: '80%'
    },
    successActionButtonTitle: {
      type: String,
      default: 'Ok'
    },
    cancelActionButtonTitle: {
      type: String,
      default: 'Cancel'
    }
  }
}
</script>

<style>
button {
  background: transparent;
  cursor: pointer;
}
.modal {
  color: black;
  text-align: left;

  position: fixed;
  z-index: 1;
  background-color: rgba(0,0,0,0.4);
  
  overflow: auto;

  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
}
.modal-content {
  background: #fefefe;
  width: 80%;
  margin: 2rem auto;
  /* padding: 2rem; */
}
.modal-content .header {
  padding: 1.5rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: solid 1px whitesmoke;
}
.modal-content .body {
  padding: 2rem;
  border-bottom: solid 1px whitesmoke;
}
.modal-content .footer {
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.modal-content .footer button {
  background: whitesmoke;
  padding: 0.5rem 1rem;
  border-radius: 5%;
  box-shadow: 2px 2px 5px -1px rgba(0,0,0,0.25);
}
</style>