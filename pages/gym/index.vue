<template>
  <div class="container mt-5 contenedor">
    <link rel="stylesheet" href="https://bootswatch.com/5/vapor/bootstrap.min.css">
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css"
      integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"
      crossorigin="anonymous"
      
    />
    <center>
      <header>
        <h1 class="titulo">{{ titulo }}</h1>
      </header>
      <br>
      <NuxtLogo></NuxtLogo>
      <br>
      <br>

      <div>
        <a-input
          type="text"
          class="forma"
          v-model="nuevaTarea"
          placeholder="Ingrese un dato"
          v-on:keyup.enter="agregarTarea"
        />
        <a-button type="primary" ghost @click="agregarTarea">agregar</a-button>
      </div>
      <hr />
      <hr>
      
        <div  class="mt-3" v-for="(item, index) of tarea" v-bind:key="index">
        <div
          class="forma"
          role="alert"
          :class="['alert', item.estado ? 'alert-success' : 'alert-danger']"
        >
          <div class="d-flex justify-content-between align-items-center">
            <div>{{ index }} - {{ item.nombre }} - {{ item.estado }}</div>
            <div>
              <button
                class="btn btn-success btn-sm"
                @click="editarTarea(index)"
              >
                OKI
              </button>
              <button class="btn btn-danger btn-sm" @click="eliminar(index)">
                X
              </button>
            </div>
          </div>
        </div>
        <!-- <a-alert message="Success Tips" type="success" show-icon />
            <div>
                {{ index }} - {{ item.nombre }} - {{ item.estado }}
            </div> -->
      </div>
      
      
    </center>
  </div>
</template>
<script lang="ts">
import Vue, { Data } from "vue";
import NuxtLogo from '~/components/NuxtLogo.vue';
import { Button } from "ant-design-vue";
import { stringify } from "querystring";
export default Vue.extend({
  data() {
    return {
      titulo: "GYM - VUE",
      tarea: [] as any,
      nuevaTarea: "",
      estado: false,
      datosBD: "",
    };
  },
  methods: {
    agregarTarea: function () {
      this.tarea.push({
        nombre: this.nuevaTarea,
        estado: false,
      });
      this.nuevaTarea = "";
    },
    editarTarea: function (index: number) {
      this.tarea[index].estado = true;
      localStorage.setItem('gym', JSON.stringify(this.tarea));
      
    },
    eliminar: function (index: number) {
      this.tarea.splice(index, 1);
      localStorage.setItem('gym', JSON.stringify(this.tarea));
    }
  }
  ,
  created: function () {
    if (typeof window !== 'undefined') {
      const datosBD = JSON.parse(localStorage.getItem("gym") as any );
      if (datosBD === null) {
        this.tarea = [];
      } else {
        this.tarea = datosBD;   
      }
    }
  },
});
</script>
<style>

.forma {
  width: 700px;
  
}
.tareas {
  background: #ffffff;
  width: 400px;
  height: 35px;
  border: 1px solid #525252;
  border-radius: 7px;
  margin-top: 10px;
}
.h1{
font-family: fantasy;
}
.titulo{
  font-family: fantasy;
  font-size: 500%;
}
hr{
  background-color: purple;
}
.div{
  border: 2px solid #525252;
  background-color: #525252;
}

</style>
