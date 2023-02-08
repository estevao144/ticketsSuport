<script>
export default {
  
  name: "ListTickets",
  
  setup() {},
  props: {
    tickets: {
      type: Array,
    },
    ticket: {
      type: Object,
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
  
    #{{ ticket.id }} {{ ticket.ticket }} {{ ticket.status }} {{ ticket.responsible }}
      <button class="editTicket" @click="openPopEdit(ticket)"> &#09998</button>
    <button class="delTicket" @click="popConfirmDel(ticket)"> &#10005</button>
  
</template>
<style scoped>
.list-ticket{
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
