<template>
  <form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
      <label for="finishedReading">
        Finished Reading:
        <input v-model="bookData.finishedReading" type="checkbox"/>
      </label>
    </div>
    <div>
      <label for="bought" >
        Bought:
        <input type="radio" v-model="bookData.ownership" value="bought"/>
      </label>
      <label for="borrowed">
        Borrowed:
        <input type="radio" v-model="bookData.ownership" value="borrowed"/>
      </label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style>
</style>
