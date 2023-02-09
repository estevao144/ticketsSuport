<script>
export default {
  setup() {},
  props: {
    formData: {
      type: Object,
      default: () => {},
    },
    responsibles: {
      type: Array,
      default: () => [],
    },
    title: {
      type: String,
      default: "",
    },
    closePopup: {
      type: Function,
      default: () => {},
    },
    validaForm: {
      type: Function,
      default: () => {},
    },
    statusTicket: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<template>
  <div class="popup">
    <div class="popup-inner">
      
      <h1 class="title-pop">{{ title }}</h1>
      
      <form class="form-input" @submit.prevent="validaForm">
        <div class="container-input">
          <p class="title-input">Informe o motivo da abertura do ticket:</p>
          <input class="input-pop" type="text" placeholder="Exemplo: Meu excel não abre."  v-model="formData.newTicket" />
        </div>

        <p>O ticket está:</p> 
        <div class="container-status">
          <div class="button"  id="verde"> 
            <input class="Novo"  type="radio" value="Novo" v-model="formData.status" />
            Novo
            <label class="btn-default">
          </label>
          </div>
          
          <div class="button" id="amarelo"> 
            <input class="Em-andamento"  type="radio" value="Em-andamento" v-model="formData.status" />
            Em-andamento
            <label class="btn-default">
          </label>
          </div>

          <div class="button" id="vermelho"> 
            <input class="Concluído"  type="radio" value="Concluído" v-model="formData.status" />
            Concluído
            <label class="btn-default">
          </label>
          </div>
        </div>
        <p>Responsável pela análise:</p>
        <div class="container-status">
        

          <div class="button"  id="blue"> 
            <input class="Novo"  type="radio" value="E" v-model="formData.responsible" :id="responsible" name="responsible" />
            E
            <label class="btn-default">
          </label>
          </div>

          <div class="button"  id="blue"> 
            <input class="Novo"  type="radio" value="N" v-model="formData.responsible" :id="responsible" name="responsible" />
            N
            <label class="btn-default">
          </label>
          </div>

          <div class="button"  id="blue"> 
            <input class="Novo"  type="radio" value="V" v-model="formData.responsible" :id="responsible" name="responsible" />
            V
            <label class="btn-default">
          </label>
          </div>
          
        </div>

        <div class="buttons-pop">
          <button class="btn-cancel" @click="closePopup">Cancelar</button>
          <button class="btn-save" type="submit">Salvar ticket</button>
        </div>
      </form>
    </div>
  </div>
</template>
<style scoped>
#blue {
  background-color: rgb(176, 176, 245);
  border-radius: 20px;
}

#verde {
 background-color: green;
 border-radius: 20px;
}

#amarelo {
background-color: yellow;
border-radius: 20px;}

#vermelho {
background-color: red;
border-radius: 20px;}
.form-input {
  width: 100%;

}
.Novo {
  background-color: #3c81ee;
  color: #fff;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin: 10px;
}
.btn-save {
  background-color: #3c81ee;
  color: #fff;
  border: none;
  padding: 0.5rem 45px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin: 10px;
}
.btn-cancel {
  border: none;
  padding: 0.5rem 45px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin: 10px;
}
.title-pop {
  width: 100%;
  text-align: start;
  margin-bottom: 20px;
  text-transform: uppercase;
  font-size: 20px;
  padding-bottom: 10px;
  font-weight: 600;
  color: rgb(191, 191, 191);
  border-bottom: 1px solid #d6d1d1;;
}

.title-input {
  text-align: start;
  width: 100%;
  min-width: 300px;
  margin-bottom: 10px;
  font-size: 16px;
  height: 50%;
}

.input-pop {
  width: 100%;
  height: 30px;
}

.select-pop {
  width: 100%;
  height: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
}
.container-input {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: flex-start;
  justify-content: start;
  margin-bottom: 20px;
}

.container-status {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: start;
  margin-bottom: 20px;
}

.res-radio {
  margin-right: 10px;
}

.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 99;
}
.popup-inner {
  width: 50%;
  background-color: #fff;
  border-radius: 10px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* apagar */

.button {
  padding: 8px;
  padding-right: 16px;
  padding-left: 16px;
  float: left;
  margin: 0 5px 0 0;
  height: 40px;
  position: relative;
}

.button label,
.button input {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.button input[type="radio"] {
  opacity: 0.011;
  z-index: 100;
}

.button input[type="radio"]:checked + label {
  border: 1px solid #000;
  border-radius: 20px;
}

.button label {

  cursor: pointer;
  z-index: 90;
  line-height: 1.8em;
}

</style>
