<template>
   <div>
       <input v-model.number="operand1" type="number"/>
       <input v-model.number="operand2" type="number"/> = {{result}}
        <div class="keyboard">
         <button @click="sum">+</button>
         <button @click="minus">-</button>
         <button @click="div">/</button>
         <button @click="multi">*</button>
          <button @click="int">int</button>
         <button @click="intPow">**</button>
     </div>

   </div>
</template>
 
<script>
 export default {
   name: 'Calculator',
   data(){
       return {
           operand1: 1,
           operand2: 1,
           result: 0,
       }
   },
   methods: {
     sum(){
       return this.result = this.operand1 + this.operand2
     },
     minus(){
      return this.result = this.operand1 - this.operand2
     },
     div(){
      return this.result = this.operand1 / this.operand2
     },
     multi(){
      return this.result = this.operand1 * this.operand2
     },
     int(){
        return this.result = Math.floor((this.operand1/ this.operand2))
      },
     intPow(){
       return this.result = this.operand1 ** this.operand2
     }
   },
 
 }
</script>