<template>
  <div class="home">
    <Header>My Memos</Header>
    <ul>
      <li v-for="memo in newest" :key="memo.id">
        <router-link :to="{ name: 'Edit', params: { id: memo.id } }">{{ memo.body }}</router-link>
      </li>
    </ul>
  </div>
</template>

<style>
textarea {
  width: 100%;
  height: 10em;
}
button {
  border: 1px solid #333;
  background-color: #333;
  color: #fff;
  padding: 10px 20px;
  margin-top: 10px;
}
</style>

<script>
import Header from "@/components/Header.vue";

export default {
  name: "Home",
  components: {
    Header,
  },
  computed: {
    newest: function () {
      return this.$store.state.memos.slice().reverse();
    },
  },
};
</script>
