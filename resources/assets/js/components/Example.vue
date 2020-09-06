<template>
<main>
    <v-container>
<v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="nombres"
            :rules="nameRules"
            :counter="10"
            label="Ingrese Nombre"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="apellidos"
            :rules="nameRules"
            :counter="10"
            label="Ingrese Apellido"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
        <v-btn
        color="green"
        class="mr-4"
        @click="add()"
      >Agregar
        </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>

  <div v-for="(item,index) in lista">
    {{ index+" "+ item.nombre+" "+ item.apellido }} 
    <v-button 
    @click="deleteItem()">
      delete
    </v-button>
</div>
    </v-container>
</main>
</template>
<script>
import axios from 'axios'
    export default {
        data(){
            return {
                nombres: '',
                apellidos: '',
                lista:[],

      nameRules: [
        v => !!v || 'Campo requerido',
        v => v.length <= 10 || 'Name must be less than 10 characters',
      ],
        
      }
        },
        methods:{
            add(){
                var datos=[]
                datos.nombre= this.nombres
                datos.apellido= this.apellidos
                this.lista.push(datos)
            },
            deleteItem() {
            this.lista.shift();
            },
           
        },

    }
</script>
