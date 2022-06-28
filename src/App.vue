<template>
  <div class="app-flex">
    <MainPage msg="Welcome to Forum Sample App!" />
  </div>

</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+Antique:wght@300&display=swap');

#app {
  font-family: 'Zen Kaku Gothic Antique', sans-serif;
  text-align: center;
  color: #ebebeb;
  margin-top: 60px;
}

.app-flex {
  max-width: 50%;
  margin-left: auto;
  margin-right: auto;
}

img {
  position: bottom 10px right 20px;
}

h1:first-letter {
  color: rgb(255, 42, 42);
  font-size: 150%;
}
</style>
