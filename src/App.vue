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
    status: "open",
  },
  {
    id: 2,
    ticket: "Não consigo acessar o sistema",
    responsible: "N",
    status: "open",
  },
  {
    id: 3,
    ticket: "Não consigo acessar o sistema",
    responsible: "V",
    status: "open",
  },
  {
    id: 4,
    ticket: "Não consigo acessar o sistema",
    responsible: "E",
    status: "open",
  },
]);
let count = ref(tickets.value.length);
const selectResponsible = ""; // aqui eu quero que seja um objeto com os valores de responsibles.
const statusTicket = ["aberto", "pendente", "concluido"];
const responsibles = ["E", "N", "V"];
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

const filterTicket = computed(() => {
  if (!selectResponsible.value) {
    return tickets.value;
  }
  return tickets.value.filter((ticket) => {
    return ticket.responsible === selectResponsible.value;
  });
});
</script>

<template>
  <div class="container">
    <HeaderTickets
      :createNewTicket="createNewTicket"
      :count="count"
      :openPopup="openPopup"
      :showPop="showPop"
    />
    <div class="res-option">
      <h2>Responsável:</h2>
      <label
        class="resp-radio"
        v-for="responsible in responsibles"
        :key="responsible.valueOf"
      >
        <input
          type="radio"
          v-model="selectResponsible"
          :id="responsible"
          name="responsible"
          :value="responsible"
        />
        {{ responsible }}
      </label>
    </div>
    <ListTickets
      :popConfirmDel="popConfirmDel"
      :openPopEdit="openPopEdit"
      :delTicket="delTicket"
      :tickets="tickets"
      :showConfirmDialog="showConfirmDialog"
    />
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
</template>

<style scoped>
.res-option {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 0 20px 0;
}
resp-radio {
  display: block;
  margin: 0 0 0 20px;
}
header {
  line-height: 1.5;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 60vw;
  height: 100vh;
  background-color: #f5f5f5;
}
</style>
