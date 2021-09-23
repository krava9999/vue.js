<template>
   <div>
       <input id="operand1" v-model.number="operand1" @focus="checkRadio = 'left'" >
       <input id="operand2" v-model.number="operand2" @focus="checkRadio = 'right'"> = {{result}}
        <div v-if="error">Ошибка! {{ error }}</div> <br>
          <label for="showKeyboard">
          <input id = "showKeyboard" type="checkbox"
          v-model="show"
          > Включить клавиатуру
          </label>
        <div class="keyboard"
        v-show="show">
        <button v-for="operand in operands" 
         v-bind:key="operand" 
         v-bind:title="operand"
         @click="calculate(operand)"
         v-bind:disabled="operand1 === '' || operand2 === ''"
         >
          {{ operand }}
        </button>
        
       
        <br>
        <button v-for="(item,index) in myCollection" 
        v-bind:key="index"
        :value="item"
        @click="innerInt(item)"       >
          {{ item }}
        </button>
        </div>
  
      <div class="focused-box">
         <input type="radio" id="one" value="left" v-model="checkRadio" name="checkedRadio" >
        <label for="one">Левое поле</label>
    
        <input type="radio" id="two" value="right" v-model="checkRadio" name="checkedRadio">
        <label for="two">Правое поле</label>
        <br>
      

      </div>
   </div>
</template>
 
<script>
 export default {
   name: 'Calculator',
   data(){
       return {
           operand1: '',
           operand2: '',
           result: 0,
           error:'',
           myCollection: [0,1,2,3,4,5,6,7,8,9,"del"],
           operands: ['+', '-', '/', '*','~','**'],
           show: false,
           checkRadio:"left",

       }
   },
   methods: {
      calculate (operation = '+') {
        this.error = ''
     switch (operation) {
       case '+':
         this.sum()
         break;
       case '-': 
         this.minus()
         break;
       case '*':
         this.multi()
         break;
       case '/':
         this.div()
         break;
         case '~':
         this.int()
         break;
         case '**':
         this.intPow()
         break;
     }
   },

     sum(){
       return this.result = this.operand1 + this.operand2
     },
     minus(){
      return this.result = this.operand1 - this.operand2
     },
      div() {
    const { operand1, operand2 } = this
    if (operand2 === 0) {
      this.error = 'Делить на 0 нельзя!'
    } else {
      this.result = operand1 / operand2
    }

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
     },
     innerInt(item){
       switch (this.checkRadio) {
         case "left":
           if (item === "del"){
            let btn = document.getElementById("operand1").value;
             this.operand1 = +(btn.slice(0,-1));
           } else{
           this.operand1 = +(string(btn) + `${item}`)
           break;
           }

          case 'right':
           if (item === "del"){
            let btn = document.getElementById("operand2").value;
             this.operand2 = +(btn.slice(0,-1));
           } else{
           this.operand2 = +(string(btn) + `${item}`)
           break;
           }
       }

      }

     
   },
 
 }
</script>