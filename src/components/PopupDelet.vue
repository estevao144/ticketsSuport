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
    formData: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<template>
  <div class="popup">
    <form class="popup-inner" @submit.prevent="validaForm">
      <h2 class="title-pop">{{ title }}</h2>
      <p class="buttons">
        <button class="btn-save" @click="delTicket(formData), closePopDel">
          Delete Item
        </button>
        <button class="btn-cancel" @click="closePopDel">Cancel</button>
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
}

.btn-save {
  background-color: #3c81ee;
  color: #fff;
  border: none;
  padding: 0.5rem 45px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin: 10px;
}
.btn-cancel {
  border: none;
  padding: 0.5rem 45px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin: 10px;
}

.title-pop {
  width: 100%;
  text-align: center;
  margin-bottom: 20px;
  text-transform: uppercase;
  font-size: 20px;
  padding-bottom: 10px;
  font-weight: 600;
  color: rgb(191, 191, 191);
  border-bottom: 1px solid #d6d1d1;
}
</style>
