<template>
  <div class="modal" :class="isOpen ? 'modal_opened' : ''">
    <div class="modal__content">
      <span class="close" @click="close">&times;</span>
      <h3>{{ title }}</h3>
      <div class="modal__content-wrapper">
        <slot>

        </slot>
      </div>
      <basic-button label="Ok" @click="apply"/>
      <basic-button label="Закрыть" @click="close"/>
    </div>
  </div>
</template>

<script>
import BasicButton from './BasicButton.vue'

export default {
  name: "BasicModal",
  components: {BasicButton},

  props: {
    isOpen: {
      default: false,
      type: Boolean,
    },
    item: {
      type: Object,
    },
    close: {
      type: Function
    },
    apply:{
      type: Function
    },
    title: {
      type: String,
    },
  },
}
</script>

<style scoped>
.modal {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal_opened {
  display: block;
}

.modal__content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 70%;

  border-radius: 5px;
}

.modal__content-wrapper {
  min-height: 300px;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>