<template>
  <div id="app">
    <Navigation />
    <router-view class="container" :user="user" />
  </div>
</template>

<script>
import Navigation from "@/components/Navigation";
import db from "./db.js";

export default {
  name: "app",
  data: function() {
    return {
      user: null
    };
  },
  mounted() {
    db.collection("users")
      .doc("fFtkMh8DnlpkwcNg25yb")
      .get()
      .then(snapshot => {
        this.user = snapshot.data().name;
      });
  },
  components: {
    Navigation
  }
};
</script>

<style lang="scss">
$primary: #05b2dd;
@import "node_modules/bootstrap/scss/bootstrap";
</style>