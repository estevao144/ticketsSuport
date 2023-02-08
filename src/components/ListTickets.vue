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
  },
};
</script>
<template>
  <div class="res-option">
    <h2> Responsaveis:</h2>
    <button
    class="resp-filter"
      v-for="responsible of responsibles"
      :key="responsible"
      @click="filterBy(responsible)"
    >
      {{ responsible }}</button
    >
  </div>

  <Ticket
    v-for="ticket of filteredTicket"
    :key="ticket.id"
    :ticket="ticket"
    :openPopEdit="openPopEdit"
    :popConfirmDel="popConfirmDel"
  />
</template>
<style scoped>
.res-option {
 display: flex;
 justify-content: right;
 width: 0px;
  
}
.resp-filter {
  display: flex;
  justify-content: center;
  padding: 10px;
  align-items: center;
  width: 100px;
  height: 40px;
  border: 1px solid rgb(199, 199, 199);
  border-radius: 90px;
  background-color: rgb(193, 214, 252);
  

}
.list-ticket {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  border-bottom: 1px solid #ccc;
  font-size: 1.5rem;
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
