<script>
export default {
  
  name: "ListTickets",
  
  setup() {},
  props: {
    findTicket: {
      type: Function,
      default: () => {console.log("Função não detectada. ListTickets");},
    },
    tickets: {
      type: Array,
      required: true,
    },
    delTicket: {
    type: Function,
    default: () => {console.log("Função não detectada. ListTickets");},
  },
  openPopEdit: {
    type: Function,
    default: () => {console.log("Função não detectada. ListTickets");},
  },
  popConfirmDel: {
    type: Function,
    default: () => {console.log("Função não detectada. ListTickets");},
  },
  },
};
</script>
<template>
  <li v-for="ticket in tickets" :key="ticket.id">
    {{ ticket.id }} {{ ticket.ticket }} {{ ticket.status }} {{ ticket.responsible }}
      <button class="editTicket" @click="openPopEdit(ticket)"> &#09998</button>
    <button class="delTicket" @click="popConfirmDel(ticket)"> &#10005</button>
  </li>
</template>
<style scoped>
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 1rem;
  border-bottom: 1px solid #ccc;
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
