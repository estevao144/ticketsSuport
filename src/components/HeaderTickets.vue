<script>
export default {
  setup() {},
  props: {
    count: {
      type: Number,
      default: 0,
    },
    openPopup: {
      type: Function,
      default: () => {
        console.log("função nao detectada.");
      },
    },
  },
};
</script>
<template>
  <header>
    <h1 class="title">TICKETS DE SUPORTE</h1>
    <div class="count-tickets">
      {{ count }} ticket{{ count > 1 ? "s" : "" }} aberto{{
        count > 1 ? "s" : ""
      }}
    </div>
    <button class="btn-new-tickets" @click="openPopup(true)">
      Novo Ticket
    </button>
  </header>
</template>
<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 0;
  border-bottom: 1px solid #000;
}
.title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #000;
  margin-bottom: 0.5rem;
  margin-right: 3rem;
}

.count-tickets {
  font-size: 1rem;
  font-weight: 400;
  color: #000;
  margin-bottom: 1rem;
  margin-right: 3rem;
}

.btn-new-tickets {
  background-color: #000;
  color: #fff;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
}

.btn-new-tickets:hover {
  background-color: #333;
}
</style>
