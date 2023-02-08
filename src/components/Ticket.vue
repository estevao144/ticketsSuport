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
      default: () => {console.log("Função não detectada. chickets");},
    },
    popConfirmDel: {
      type: Function,
      default: () => {console.log("Função não detectada. chickets");},
    },
    changeStatusTicket: {
      type: Function,
      default: () => {console.log("Função não detectada. Ticket");},
    },
    classTicket: {
      type: String,
    },
}
};

</script>

<template>
    <div class="container-ticket">
      
      <span class="ticket-id">
        #{{ ticket.id }} 
      </span> 
      <span class="ticket-ticket">
        {{ ticket.ticket }} 
      </span>
      <span class="ticket-responsible">
      {{ ticket.responsible }} 
      </span>
      <button class="" @click="changeStatusTicket(ticket)">
        {{ ticket.status }}
      </button>
      <button class="editTicket" @click="openPopEdit(ticket)"> &#09998</button>
    <button class="delTicket" @click="popConfirmDel(ticket)"> &#10005</button>
</div>
</template>
<style scoped>

    .container-ticket {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;
        border-bottom: 1px solid #ccc;
        font-size: 1.5rem;
    }
    .ticket-id {
        width: 50px;
    }
    .ticket-ticket {
        width: 400px;
    }
    .ticket-responsible {
        width: 200px;
    }
    .status-ticket {
        width: 100px;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(193, 214, 252);
    }

    .status-novo {
        width: 100px;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(255, 52, 1);
    }

    .status-em-andamento {
        width: 100px;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(231, 224, 38);
    }

    .status-concluido {
        width: 100px;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(3, 226, 48);
    }
    .editTicket {
        width: 50px;
        height: 40px;
        border:0ch;
        background-color: transparent;   
    }

    .delTicket {
        width: 50px;
        height: 50px;
        border:0ch;
        background-color: transparent;  
    }
</style>