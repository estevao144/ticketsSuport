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
  
}
};

</script>

<template>
    <div class="container-ticket">
     <div class="primeiro-container"> 
      <span class="ticket-id">
        #{{ ticket.id }} 
      </span> 
      <span class="ticket-ticket">
        {{ ticket.ticket }} 
      </span >
     </div> 
      <div class="segundo-container"> 
      <span class="ticket-responsible">
      {{ ticket.responsible }} 
      </span>
      
      <button class="status-ticket" :class="ticket.status" 
      @click="changeStatusTicket(ticket)">
        {{ ticket.status }}
      </button>
      
      <div class="container-btn"> 
        <button class="editTicket" @click="openPopEdit(ticket)"> &#09998</button>
        <button class="delTicket" @click="popConfirmDel(ticket)"> &#10005</button>
      </div>
    </div>
    
</div>
</template>
<style scoped>

.container-ticket {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 100%;
        max-height: 26%;
        height: 30%;
        border: 1px solid rgb(199, 199, 199);
    }

    .container-btn {
        display: flex;
        justify-content: flex-end;
        width: 100%;
        align-items: center;
        padding: 1rem;
      }
  
    .primeiro-container {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        padding: 5px;
        font-size: 1.2rem;
        float:left
        
    }

    .segundo-container {
        display: flex;
        justify-content: space-between ;
        align-items: center;
        height: 0px;
        padding: 1rem;
        font-size: 1.5rem;
        float:left
    }
    .ticket-id {
        width: 50px;
        color: rgb(159, 156, 151);

    }
    .ticket-ticket {
        width: 400px;
    }
    
    .ticket-responsible {
    display: flex;
    justify-content: center;
    width: 50px;
    height: 40px;
    border: 1px solid rgb(199, 199, 199);
    border-radius: 100px;
    background-color: rgb(193, 214, 252);
    margin-right: 2%;
    margin-left: 3%;
    }
    .padrao-ticket {
        width: auto;
       
    }
    .Novo {
        width: auto;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(255, 52, 1);
        padding-right: 16px;
        padding-left: 16px;
    }

    .Em-andamento {
        width: 100px;
        height: 40px;
        border: 1px solid rgb(199, 199, 199);
        border-radius: 90px;
        background-color: rgb(231, 224, 38);
    }

    .Concluído {
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
        font-size: 35px;   

    }

    .delTicket {
        width: 50px;
        height: 50px;
        border:0ch;
        background-color: transparent;  
        font-size: 35px;   
    }
</style>