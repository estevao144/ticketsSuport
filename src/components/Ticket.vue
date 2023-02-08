<script>
export default {
  name: "Ticket",
  setup() {},
props:{
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
}
};

</script>

<template>
    <div class="ticket-solo">
      #{{ ticket.id }} {{ ticket.ticket }} {{ ticket.status }} {{ ticket.responsible }}
      <button class="editTicket" @click="openPopEdit(ticket)"> &#09998</button>
    <button class="delTicket" @click="popConfirmDel(ticket)"> &#10005</button>
</div>
</template>
<style scoped>

    .ticket-solo {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;
        border-bottom: 1px solid #ccc;
        font-size: 1.5rem;
    }
    .ticket {
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