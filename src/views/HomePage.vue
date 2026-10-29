<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="dark">
        <ion-title>Informatica</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <div id="container">
        <h2>Operaciones matemáticas</h2>
        <ion-list lines="none">
          <ion-item>
            <ion-label>Suma: {{ a }} + {{ b }} = {{ a + b }}</ion-label>
          </ion-item>
          <ion-item>
            <ion-label>Resta: {{ a }} - {{ b }} = {{ a - b }}</ion-label>
          </ion-item>
          <ion-item>
            <ion-label>Multiplicación: {{ a }} * {{ b }} = {{ a * b }}</ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              División: {{ a }} / {{ b }} = {{ b !== 0 ? Math.trunc(a / b) : 'No se puede dividir por 0' }}
            </ion-label>
          </ion-item>
        </ion-list>
        <h2>Entrada de datos</h2>
        <ion-list>
          <ion-item>
            <ion-input label="Introduce un número (A)" label-placement="stacked" type="number" v-model.number="a" />
          </ion-item>
          <ion-item>
            <ion-input label="Introduce otro número (B)" label-placement="stacked" type="number" v-model.number="b" />
          </ion-item>
        </ion-list>
        <ion-list lines="none">
          <ion-item v-if="a === 0" color="warning">
            <ion-label>a debe ser diferente a 0</ion-label>
          </ion-item>
          <ion-item v-if="b === 0" color="warning">
            <ion-label>b debe ser diferente a 0</ion-label>
          </ion-item>
        </ion-list>
        <h2>Datos del estudiante</h2>
        <ion-list>
          <ion-item>
            <ion-input label="Nombre del estudiante" label-placement="stacked" type="text" v-model="nombre" />
          </ion-item>
          <ion-item>
            <ion-input label="Edad del estudiante" label-placement="stacked" type="number" v-model.number="edad" />
          </ion-item>
        </ion-list>
        <ion-button expand="block" color="danger" @click="adicionarEst()">
          Adicionar estudiante
        </ion-button>
        <ion-button expand="block" color="warning" @click="AddStudent">
          Adicionar estudiante
        </ion-button>
        
        <!-- Aquí se añadió el contador dinámico -->
        <h1>Lista de estudiantes: {{ estudiantes.length }}</h1>
        
        <ion-list>
          <ion-item v-for="est in estudiantes" :key="est.nombre">
            <ion-label>
              <h2>{{ est.nombre }}</h2>
              <p>Edad: {{ est.edad }} años</p>
            </ion-label>
          </ion-item>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonItem, IonInput, IonList, IonLabel, IonButton } from '@ionic/vue';
import { ref } from 'vue';

const a = ref<number>(65);
const b = ref<number>(5);
const estudiantes = ref([
  { nombre: "1.Joel", edad: 20 },
  { nombre: "2.Esteban", edad: 15 },
  { nombre: "3.Abril", edad: 18 }
]);
const nombre = ref("");
const edad = ref<number>(0);

const AddStudent=()=>{
  estudiantes.value.push(
    {nombre: nombre.value, edad:edad.value, }
  );
  nombre.value="";
  edad.value=0;
  alert("Adiccionar estudiante");
}

function adicionarEst() {
  alert("adiccionar estudiantes");
}
</script>
