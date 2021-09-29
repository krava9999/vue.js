 <template>
          <a href="#" class="content__btn" @click="showPostForm()">add new cost</a>
</template>


<script>
export default {
   name: 'addNewPostBtn',
   methods: {
     showPostForm() {
    document.querySelector('.addNewPostForm').classList.toggle('visible');
  }
   },
}


</script>