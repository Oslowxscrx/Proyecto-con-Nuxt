<template>

    <div>
        <NuxtLogo></NuxtLogo>
        <hr>
        <h1>{{ titulo }}</h1>

        <button >Abrir modal</button>
      
    </div>
  </template>
  <script lang="ts">
  import NuxtLogo from '~/components/NuxtLogo.vue';
  import Modal from '@/components/Modal.vue'
  import { defineComponent, ref } from 'vue';
import { data } from 'browserslist';
  export default defineComponent({
    components:{
        NuxtLogo,
        Modal
    },
    data(){
        return{
            titulo: 'CRUD NUEVO '

        }
    },
    methods:{
      agregarItem(){
        
      }
    },
  });

  </script>
  
  
<!-- <template>
    <div>
        <NuxtLogoVue></NuxtLogoVue>
        <hr>
        <h1>{{ titulo }}</h1>
        <button>abrir</button>
        <a-button type="primary" @click="abriModal">Open Modal</a-button>


        
    </div>
</template>

<script lang="ts">
import { file, LOGICAL_OPERATORS } from '@babel/types';
import Vue from 'vue';
import NuxtLogoVue from '~/components/NuxtLogo.vue';
// import Modal from '~/components/Modal.vue';
export default Vue.extend({ 

    components:{
        NuxtLogoVue,
        // ModalVue
    },
    data(){
        return{
            titulo: 'CRUD NUEVO '
        }
    }
})
</script> -->
<style scoped>
h1 {
    position: relative;
    left: 40%;
    font-family: fantasy;
    font-size: 500%;
}
div {
  margin: 25px auto;  
  width: 1210px;
  height: 800px;
  
}

</style>