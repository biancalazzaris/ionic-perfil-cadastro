<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Cadastro</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <div class="container">
        <div class="form">
          <ion-col>
            <div class="avatar">
              <ion-fab-button href="/tabs/tab2">
                  <ion-avatar>
                    <img src="https://ionicframework.com/docs/demos/api/avatar/avatar.svg">
                  </ion-avatar>
              </ion-fab-button>
            </div>
            <ion-item class="input">
              <ion-label position="floating">Nome</ion-label>
              <ion-input
                type="text"
                v-model="inputNome"
                required="true"
              ></ion-input>
            </ion-item>
            <ion-item class="input">
              <ion-label position="floating">Data do seu aniversário</ion-label>
              <ion-datetime
                type="date"
                v-model="inputData"
                display-format="DD/MM/YYYY"
                min="1902-03-14"
                max="2021-12-09"
              ></ion-datetime>
            </ion-item>
            <ion-item class="input">
              <ion-label position="floating">Telefone</ion-label>
              <ion-input 
              type="number" 
              v-model="inputTel"></ion-input>
            </ion-item>
            <ion-button class="bt" color="success" @click="salvarInformacoes">Salvar
            </ion-button>
          </ion-col>
                                <!-- Validação de campos -->
            <p>
              Nome: {{ nome }} <br>
              Data de Nascimento: {{ data }} <br>
              Telefone: {{ telefone }}
            </p>
        </div>
      </div>

    </ion-content>

  </ion-page>
</template>

<script lang="ts">
import { personCircle } from "ionicons/icons";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCol,
  IonItem,
  IonLabel,
  IonInput,
  IonFabButton,
  IonButton,
  IonAvatar,
  IonDatetime
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Tab1",
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonCol,
    IonItem,
    IonLabel,
    IonInput,
    IonFabButton,
    IonButton,
    IonAvatar,
    IonDatetime
  },
  methods: {
    salvarInformacoes() {
      const nome = this.inputNome;
      this.nome = nome;
      const data = this.inputData;
      this.data = data;
      const telefone = this.inputTel;
      this.telefone = telefone;
    },
  },
  data() {
    return {
      inputNome: "",
      nome: "",
      inputData: "",
      data: "",
      inputTel: "",
      telefone: "",
    };
  },
  setup() {
    const customYearValues = [2020, 2016, 2008, 2004, 2000, 1996];
    const customPickerOptions = {
      buttons: [{
        text: 'Save',
        handler: () => console.log('Clicked Save!')
      }, {
        text: 'Log',
        handler: () => {
          console.log('Clicked Log. Do not Dismiss.');
          return false;
        }
      }]
    }

    return {
      customYearValues,
      customPickerOptions,
      personCircle
    }
  }
});

</script>

<style scoped>
.container {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.form {
  padding: 30px;
  background-color: rgb(214, 228, 222);
  border-radius: 25px;
}
.input {
  margin-bottom: 30px;
  border-radius: 25px;
}
.avatar,
.bt {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}

</style>