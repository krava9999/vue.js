<template>
       <div class="table">
      <div class="table__row">
        <div class="table__cell bold">#</div>
        <div class="table__cell bold">date</div>
        <div class="table__cell bold">category</div>
        <div class="table__cell bold">value</div>
      </div>

       <div class="table__row" v-for="(item, index) in items" :key="index"> 
        <div class="table__cell ">{{ index }}</div>
        <div class="table__cell ">{{ item.paymentDate }}</div>
        <div class="table__cell ">{{ item.paymentDesc }}</div>
        <div class="table__cell ">{{ item.paymentAmount }}</div>
      </div>

   
    </div>
</template>

<script>
export default {
   props: {
  items: {
    type: Array,
    default: [],
  }
},


}
</script>