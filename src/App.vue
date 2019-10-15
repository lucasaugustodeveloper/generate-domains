<template>
  <div>
    <div id="slagon" class="text-center">
      <h1>NameGator</h1>
      <br />
      <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, GraphQL e Node.JS</h6>
    </div>

    <div id="main">
      <Domains />
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import Domains from "./components/Card/domainList";

export default {
  name: "app",
  components: {
    Domains
  }
};
</script>

<style>
#slogan {
  margin: 30px 0;
}
#main {
  background-color: #f1f1f1;
  padding: 30px 0;
}
</style>
