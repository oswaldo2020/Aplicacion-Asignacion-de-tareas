<template>
<form @submit.prevent="procesarFormulario">
<Input :tarea="tarea" />

</form>
<hr>
<ListaTareas />
</template>

<script>

import Input from '../components/Input.vue'
import ListaTareas from '../components/ListaTareas.vue'
import {mapActions} from 'vuex'
const shortid = require('shortid');

export default {

  name: 'Home',
  components: {
    Input, ListaTareas
  },
  data(){
    return{
      tarea:{
        id: '',
        nombre: '',
        categorias:[],
        estado:"",
        numero: 0
      }
    }
  },
  methods:{
    ...mapActions(['setTareas']),
    procesarFormulario(){
        console.log(this.tarea)
        if(this.tarea.nombre.trim === ""){
          return
        }
        console.log('no esta vacio')

        //generar id
        this.tarea.id = shortid.generate()
        console.log(this.tarea.id)
        //envian los datos
        this.setTareas(this.tarea)

        //limpiar datos
        this.tarea = {
        id: '',
        nombre: '',
        categorias:[],
        estado:"",
        numero: 0
        }

    },

  },




}
</script>
