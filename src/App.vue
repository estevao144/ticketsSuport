<script setup>
import { computed, ref } from "vue";
import HeaderTickets from "./components/HeaderTickets.vue";
import ListTickets from "./components/ListTickets.vue";
import PopupTickets from "./components/PopupTickets.vue";
import PopupDelet from "./components/PopupDelet.vue";
// variaveis.
let showConfirmDialog = ref(false);
let showPop = ref(false);
let title = ref("");
let tickets = ref([
  {
    id: 1,
    ticket: "Não consigo acessar o sistema",
    responsible: "E",
    status: "Novo",
  },
  {
    id: 2,
    ticket: "Não consigo Ligar o computador",
    responsible: "N",
    status: "Em-andamento",
  },
  {
    id: 3,
    ticket: "Meu linux não inicia",
    responsible: "V",
    status: "Em-andamento",
  },
  {
    id: 4,
    ticket: "Windo",
    responsible: "E",
    status: "Concluído",
  },
]);
let count = ref(tickets.value.length);
const selectResponsible = ref(''); 
const statusTicket = ref(["Novo", "Em-andamento", "Concluído"]);
const responsibles = ref(["E", "N", "V"]);
let formData = ref({
  newTicket: "",
  status: "",
  responsible: "",
});
// funções.

const createNewTicket = () => {
  count.value = tickets.value.length + 1;
  console.log(formData.value);
  tickets.value.push({
    id: tickets.value.length + 1,
    ticket: formData.value.newTicket,
    responsible: formData.value.responsible,
    status: formData.value.status,
  });
  closePopup();
};
const openPopup = () => {
  title.value = "Novo Ticket de Suporte";
  showPop.value = true;
  formData.value = {
    id: ref(0),
    newTicket: "",
    status: "",
    responsible: "",
  };
};
const closePopup = () => {
  showPop.value = false;
};

const findTicket = (id) => {
  return tickets.value.find((ticket) => ticket.id === id);
};

const delTicket = (ticket) => {
  tickets.value = tickets.value.filter((t) => t.id !== ticket.id);
  verificaTicket(tickets.value);
  count.value = tickets.value.length;
  showConfirmDialog.value = false;
};

const popConfirmDel = (ticket) => {
  showConfirmDialog.value = true;
  title.value = `Deletar Ticket de Suporte [${ticket.id}]`;
  findTicket(ticket.id);
  formData.value = {
    id: ticket.id,
    newTicket: ticket.ticket,
    status: ticket.status,
    responsible: ticket.responsible,
  };
  console.log(formData.value);
};

const openPopEdit = (ticket) => {
  showPop.value = true;
  title.value = `Editar Ticket de Suporte [${ticket.id}]`;
  findTicket(ticket.id);
  formData.value = {
    id: ticket.id,
    newTicket: ticket.ticket,
    status: ticket.status,
    responsible: ticket.responsible,
  };
  delTicket(ticket);
  console.log(tickets);
};

const editTicket = (ticket) => {
  tickets.value.push({
    id: ticket.id,
    ticket: ticket.ticket,
    responsible: ticket.responsible,
    status: ticket.status,
  });

  closePopup();
};

const validaForm = () => {
  if (formData.value.newTicket === "") {
    alert("Preencha o campo Ticket");
    return false;
  }
  if (formData.value.status === "") {
    alert("Preencha o campo Status");
    return false;
  }
  if (formData.value.responsible === "") {
    alert("Preencha o campo Responsavel");
    return false;
  }

  return createNewTicket();
};

const verificaTicket = (tickets) => {
  for (let index = 0; index < tickets.length; index++) {
    tickets[index].id = index + 1;
  }
};

const closePopDel = () => {
  showConfirmDialog.value = false;
};
const filterBy = (select) => {
  selectResponsible.value = select;
  console.log(selectResponsible);
  
};

const changeStatusTicket = (ticket) => {
  

  if (ticket.status === "Novo") {
    ticket.status = "Em-andamento";
  } else if (ticket.status === "Em-andamento") {
    ticket.status = "Concluído";
  } else if (ticket.status === "Concluído") {
    alert("Ticket já está concluído");
  }
  console.log(ticket);
};

const filteredTicket = computed(() => {
  if (selectResponsible.value) {
    
    return tickets.value.filter((ticket) => ticket.responsible === selectResponsible.value);
  }
  return tickets.value;
});

</script>

<template>
  <div class="main-container">
    <div class="container">
      <HeaderTickets
        :createNewTicket="createNewTicket"
        :count="count"
        :openPopup="openPopup"
        :showPop="showPop"
      />
       <div class="container-tickets">    
        <ListTickets
        :classTicket="classTicket"
          :popConfirmDel="popConfirmDel"
          :openPopEdit="openPopEdit"
          :ticket="ticket"
          :tickets="tickets"
          :filteredTicket="filteredTicket"
          :responsibles="responsibles"
          :filterBy="filterBy"
          :changeStatusTicket="changeStatusTicket"
        />
      </div>

      <div>
        <PopupDelet
          v-if="showConfirmDialog"
          :tickets="tickets"
          :title="title"
          :delTicket="delTicket"
          :formData="formData"
          :closePopDel="closePopDel"
        />
      </div>
      <PopupTickets
        :validaForm="validaForm"
        :editTicket="editTicket"
        :formData="formData"
        :statusTicket="statusTicket"
        :responsibles="responsibles"
        :createNewTicket="createNewTicket"
        :title="title"
        :closePopup="closePopup"
        v-if="showPop"
      />
    </div>
    </div>
</template>

<style scoped>

.container-tickets {
  width: 100%;
  min-width: 300px;
  overflow-x: scroll;
  
}
.responsavel {
  margin: 0 0 0 20px;
  color: rgb(167, 162, 162);
}
.main-container {
  display: flex;
  align-items: center;
  padding: 40px;
  justify-content: center;
  width: 100vh;
  height: 100vh;
  background-color: rgb(218, 218, 218);
}
.container {
  display: flex;
  flex-direction: column;
  padding: 10px;
  align-items: center;
  justify-content: center;
  width: 100%;
  border-radius: 10px;
  height: 100%;
  background-color: white;
}
.res-radio {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 0 20px 0;
}
.resp-radio {
  align-items: center;
  margin: 20px 20px 0 20px;
}
header {
  line-height: 1.5;
}
</style>
