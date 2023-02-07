<script>
export default {
  name: "PopupDelet",
  setup() {},

  props: {
    delTicket: {
      type: Function,
      default: () => {},
    },
    closePopDel: {
      type: Function,
      default: () => {},
    },
    title: {
      type: String,
      default: "",
    },
    FormData: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<template>
  <div class="popup">
    <form class="popup-inner" @submit.prevent="validaForm">
      <h2>{{ title }}</h2>
      <p class="buttons">
        <button class="deleteTicket" @click="delTicket(), closePopDel">
          Delete Item
        </button>
        <button class="cancelPop" @click="closePopDel">Cancel</button>
      </p>
    </form>
  </div>
</template>
<style scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 99;
}
.popup-inner {
  width: 50%;
  height: 50%;
  background-color: #fff;
  border-radius: 10px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.buttons {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 1rem;
  border-bottom: 1px solid #ccc;
}
</style>
