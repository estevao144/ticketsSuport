<script>
import Ticket from "./Ticket.vue";
export default {
  components: { Ticket },

  name: "ListTickets",

  setup() {},
  props: {
    filterBy: {
      type: Function,
      default: () => {
        console.log("Função não detectada. ListTickets");
      },
    },

    responsibles: {
      type: Array,
    },

    filteredTicket: {
      type: Array,
    },
    tickets: {
      type: Array,
    },
    ticket: {
      type: Object,
    },
    openPopEdit: {
      type: Function,
      default: () => {
        console.log("Função não detectada. ListTickets");
      },
    },
    popConfirmDel: {
      type: Function,
      default: () => {
        console.log("Função não detectada. ListTickets");
      },
    },
    changeStatusTicket: {
      type: Function,
      default: () => {
        console.log("Função não detectada. ListTickets");
      },
    },
    classTicket: {
      type: String,
    },
  },
};
</script>
<template>
  <div class="res-option">
    <h2 class="title-option"> Responsaveis:</h2>
    <div class="resp-container"> 
      <button
      class="resp-filter"
        v-for="responsible of responsibles"
        :key="responsible"
        @click="filterBy(responsible)"
      >
        {{ responsible }}</button
      >
    </div>
  </div>

  <Ticket
    v-for="ticket of filteredTicket"
    :key="ticket.id"
    :classTicket="classTicket"
    :ticket="ticket"
    :openPopEdit="openPopEdit"
    :popConfirmDel="popConfirmDel"
    :changeStatusTicket="changeStatusTicket"
  />
</template>
<style scoped>

.resp-container {
  display: flex;
  justify-content: start;
  gap: 10px;
  align-items: center;
  width: 100%;
  height: 60px;
  
}
.resp-filter {
  display: flex;
  justify-content: center;
  padding: 10px;
  align-items: center;
  width: 45px;
  height: 40px;
  border: 1px solid rgb(199, 199, 199);
  border-radius: 90px;
  background-color: rgb(193, 214, 252);
}
.res-option {
  display: flex;
  justify-content: start;
  align-items: center;
  width: 100%;
  gap: 10px;
  height: 60px;
  padding: 1rem;
}
.title-option {
  color: rgb(159, 156, 151);
}
button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
  color: #000;
}
button:hover {
  color: #333;
}

.editTicket {
  color: #000;
}

.delTicket {
  color: #f00;
}
</style>
