<template>
<div class="project">
  <header class="header">
    <h1 class="header__heading">
      My personal costs
    </h1>
  </header>

  <div class="content">

      <!--Обернуть в шаблон кнопку-->
        <addNewPostBtn/>
      <!-- обернуть в шаблон всплывающую форму -->
        <addNewPostForm @addNewPayment="addNewPayment"/>
      <!-- обернуть в шаблон форму с данными -->
         <tableContent :items="paymentsList"/>
    </div>   


</div>
</template>
 
<script>
 import addNewPostBtn from './components/addNewPostBtn.vue'
 import addNewPostForm from './components/addNewPostForm.vue'
 import tableContent from './components/tableContent.vue'
export default {
  components: {
    addNewPostBtn,
    addNewPostForm,
    tableContent
  },
  data() {
    return {
      paymentsList: [], // массив трат
    }
  },
  methods: {
    fetchData(){
      return [
      {
            paymentDesc:'Sport',
            paymentAmount:3000,
            paymentDate:'23-09-2021',
      },
      {     
            paymentDesc:'Food',
            paymentAmount:1500,
            paymentDate:'25.09.2021',
      },
      {
        paymentDesc:'Transport',
            paymentAmount:1000,
            paymentDate:'25-09-2021',
      },
    ]
    },

    addNewPayment (data) {
      this.paymentsList = [...this.paymentsList, data]
    }

  },
  // как только шаблон создается на странице, заполняем массив
  created () {
  this.paymentsList = this.fetchData()
},

}

</script>

<style lang="scss">
$fontStyle:  'Lucida Sans';
 
  .project{
    margin: 0 auto;
    width: 50%;
    border: 1px solid black;
  }
  .header{
    &__heading{
      font-family: $fontStyle;
    }
  }
  .content{
    position: relative;
    .content__btn{
      width: 30%;
      text-decoration: none;
      color: white;
      text-align: center;
      padding: 10px;
      text-transform: uppercase;
      font-family: $fontStyle;
      display: block;
      background-color: #23A79A;
      box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);
      &:hover{
        box-shadow: 0px 5px 5px -5px rgba(34, 60, 80, 0.6) inset;
      }
    }
  }
  .addNewPostForm{
    width: 300px;
    background-color: white;
    height: 200px;
    border: 1px solid black;
    margin: 0 auto;
    top: 100%;
    left: 50%;
    transform:translate(-50%, -50%);
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: center;
    &__input{
      width: 250px;
      height: 30px;
      margin-top: 5%;
    }
    &__btn{
      margin-top: 5%;
      margin-left: 50%;
      width: 30%;
      text-decoration: none;
      color: white;
      text-align: center;
      padding: 10px;
      text-transform: uppercase;
      font-family: $fontStyle;
      display: block;
      background-color: #23A79A;
      box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);
      &:hover{
        box-shadow: 0px 5px 5px -5px rgba(34, 60, 80, 0.6) inset;
      }
    }
  }
    .table{
      display: flex;
      flex-direction: column;
      &__row{
        display: flex;
        justify-content: space-around;
        border-bottom: 1px solid grey;
        height: 30px;
        align-items: center;
      }
      &__cell{
        text-align: center;
        width: 25%;
      }
    }

   .bold{
     font-weight: bold;
     font-family: $fontStyle;
     text-transform: uppercase;
   }
   .visible{
    display: none;
  }
</style>