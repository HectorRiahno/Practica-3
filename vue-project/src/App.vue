<script setup>
import { ref } from 'vue';
let input=ref('')
let modelo=ref()
let array1=ref([{code:'XDCHH'},
{code:'XDCHH'},
{code:'XDCHH'},
{code:'XDCHH'}
,{code:'XDCHH'}])

let array2=ref([{code:'WW999S'},
{code:'XDCHH'}])

let array3=ref([{code:'LOJ7'},
{code:'NMKI'},
{code:'HUFJD'}])

function add() {
  if(modelo.value==1){
    array1.value.push({code:input.value})
    modelo.value=''
    input.value=''
  }else if(modelo.value==2){
    array2.value.push({code:input.value})
    modelo.value=''
    input.value=''
  }else   if(modelo.value==3){
    array3.value.push({code:input.value})
    modelo.value=''
    input.value=''
  }
}
function borrar(i,z){
  if(z==1){
    array1.value.splice(i,1)
  }else if(z==2){
    array2.value.splice(i,1)
  }else   if(z==3){
    array3.value.splice(i,1)
  }
}
</script>

<template>
  <div class="p-10">
    <div class="w-4/6 mx-auto  bg-slate-50 p-5">
      <div class="text-center bg-slate-50">
        <p>Sistema de turnos</p>
      </div>
      <div class="flex justify-between gap-5 mt-6">
        <div class="bg-neutral-100 w-2/5">
          <div class="bg-blue-400 p-3 rounded-md">
            <p class="text-center uppercase text-white font-semibold">modulo 1</p>
          </div>
          <!-- div de carga del arreglo -->
          <div v-for="(obj,i) in array1" :key="i" class="bg-white m-3 p-1 rounded-md flex justify-between">
            <p>{{ i+1 }}-{{ array1[i].code }}</p>
            <p @click="borrar(i,1)" class="bg-red-300 px-2 rounded-2xl">X</p>
          </div>
        </div>
        <div class="bg-neutral-100 w-2/5">
          <div class="bg-orange-400 p-3 rounded-md">
            <p class="text-center uppercase text-white font-semibold">modulo 2</p>
          </div>
          <!-- div de carga del arreglo -->
          <div v-for="(obj,i) in array2" :key="i" class="bg-white m-3 p-1 rounded-md flex justify-between">
            <p>{{ i+1 }}-{{ array2[i].code }}</p>
            <p @click="borrar(i,2)" class="bg-red-300 px-2 rounded-2xl">X</p>
          </div>
        </div>
        <div class="bg-neutral-100 w-2/5">
          <div class="bg-green-600 p-3 rounded-md">
            <p class="text-center uppercase text-white font-semibold">modulo 3</p>
          </div>
          <!-- div de carga del arreglo -->
          <div v-for="(obj,i) in array3" :key="i" class="bg-white m-3 p-1 rounded-md flex justify-between">
            <p>{{ i+1 }}-{{ array3[i].code }}</p>
            <p @click="borrar(i,3)" class="bg-red-300 px-2 rounded-2xl">X</p>
          </div>
        </div>
      </div>
      <div class="px-4 bg-neutral-200 mt-4 flex justify-evenly py-5">
        <!-- variable q se actualiza -->
        <h1>9 turnos</h1>
        <input v-model="input" class="px-2 " placeholder="Código" type="text">
        <input v-model="modelo" type="number" placeholder="de 1-3">
        <p @click="add" class="text-white bg-violet-400 p-1 px-6 rounded-lg">Agregar</p>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
