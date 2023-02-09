<script>
export default {
  setup() {},
  props: {
    formData: {
      type: Object,
      default: () => {},
    },
    responsibles: {
      type: Array,
      default: () => [],
    },
    title: {
      type: String,
      default: "",
    },
    closePopup: {
      type: Function,
      default: () => {},
    },
    validaForm: {
      type: Function,
      default: () => {},
    },
    statusTicket: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<template>
  <div class="popup">
    <div class="popup-inner">
      <h1>{{ title }}</h1>
      <p>Informe o motivo da abertura do ticket:</p>
      <form @submit.prevent="validaForm">
        <input type="text" v-model="formData.newTicket" />
        <p>O ticket está:</p>
        <p class="status-radio" v-for="status in statusTicket" :key="status">
          <input
            type="radio"
            v-model="formData.status"
            :id="status"
            name="status"
            :value="status"
          />
          {{ status }}
        </p>
        <p>Responsavel:</p>
        <span
          class="resp-radio"
          v-for="responsible in responsibles"
          :key="responsible"
        >
          <input
            type="radio"
            v-model="formData.responsible"
            :id="responsible"
            name="responsible"
            :value="responsible"
          />
          {{ responsible }}
      </span>

        <div class="buttons-">
          <button class="btn-cancel" @click="closePopup">Cancelar</button>
          <button class="btn-save" type="submit">Salvar</button>
        </div>
      </form>
    </div>
  </div>
</template>
<style scoped>
.status-radio {
  display: inline-block;
  width: 40px;
  height: 40px;
  text-align: center;
  line-height: 15px;
  padding: 0px;
  float: left;
}
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
</style>
