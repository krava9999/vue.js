<template>
     <div class="addNewPostForm visible">
        <input type="text" class="addNewPostForm__input" placeholder="Payment description" v-model="paymentDesc">
        <input type="number" class="addNewPostForm__input" placeholder="Payment amount" v-model="paymentAmount">
        <input type="date" class="addNewPostForm__input" placeholder="Payment date" v-model="paymentDate">
        <a href="#" class="addNewPostForm__btn" @click="onSaveClick">add</a>
      </div>
</template>

<script>
export default {
    name: 'addNewPostForm',
    data() {
        return {
            paymentDesc:'',
            paymentAmount:'',
            paymentDate:'',
        }
    },
    computed:{
          getCurrentDate () {
      const today = new Date();
      const d = today.getDate()
      const m = today.getMonth() + 1
      const y = today.getFullYear()
      return `${d}.${m}.${y}`
    },
    },
      methods: {
    onSaveClick () {
      const data = {
        paymentDesc: this.paymentDesc,
        paymentAmount: +this.paymentAmount,
        paymentDate: this.paymentDate || this.getCurrentDate,
      }
       if ((this.paymentDesc || this.paymentAmount || this.paymentDate) === ('') || (0) ){
           alert('заполните все поля')
       } else {
            this.$emit('addNewPayment', data);
             document.querySelector('.addNewPostForm').classList.toggle('visible');
       }
      
    }
  }

}
</script>