<script setup lang="ts">
import { ref } from 'vue'
import type {Ref}  from 'vue';
const nombre = ref('');
const apellido = ref('');
const edad = ref(0);
const genero = ref('');
const numero = ref(0);
const color = ref('rgb(21, 193, 79)');
const Tletra:Ref<number> = ref(50);
const animation:Ref<boolean>= ref(false);
const classAnimation = ref('');
const error = ref<{ [key: string]: string }>({});
console.log(animation);
console.log(animation.value);

const validationName = ()=>{

const msj = " Lo siento no se permite que el nombre o apellido sean iguales";
if(nombre.value == apellido.value && nombre.value.length > 0 && apellido.value.length > 0){
  error.value[msj] = msj;
  
}else{            
  delete error.value[msj];
}
}

const validationNum = () =>{
const msj = 'Lo siento el número no puede ser mayor a 10 digitos';

if(numero.value.toString().length > 10){
  error.value[msj] = msj;
  
}else{
  delete error.value[msj];
}            
}

const validationAge = () =>{
const msj ='Lo siento la edad no puede ser mayor a 60';
if(edad.value > 60){
  error.value[msj] = msj;

}else{
  delete error.value[msj];
}
}

</script>

<template>
   <main>
        <h2>Hola, bienvenido</h2>
        <h3>Este es un formulario, ingresa tus datos.</h3>
        <!-- <input type = "text" v-model="nombre"> -->
        <label for="name">Nombre:</label>
        <input :input=" validationName()" type="text" v-model="nombre" placeholder="Nombre">
        <h1 :class ="{'error':error}"> {{ nombre }}</h1>
        <label for="name">Apellido:</label>
        <input :input=" validationName()" type="text" v-model="apellido" placeholder="Apellido">
        <h1 :class ="{'error':error}"> {{ apellido }}</h1>
        <label for="name">Edad:</label>
        <input :input=" validationAge()" type="text" v-model="edad" placeholder="Edad">
        <label for="name">Genero:</label>                                 
        <select v-model="genero" placeholder="Genero">
            <option disabled value="">Seleccione genero</option>
            <option>Masculino</option>
            <option>Femenino</option>
            <option>Otro</option>
        </select>
        <label for="name">Número:</label> 
        <input :input=" validationNum()" type="text" v-model="numero" placeholder="Número">
        <!-- <h1 :class ="{'error':error}"> {{ error }}</h1> -->
   
        <h1 class="error" v-for="([clave, valor], index) in Object.entries(error)" :key="index">
        {{ valor }}
        </h1>

    </main>


</template>

<style scoped>
.error{
    color: #d03;
}



.form-container {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 10px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>