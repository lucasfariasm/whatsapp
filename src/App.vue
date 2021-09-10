<template>
  <div id="app" class="container">
    <SendMessage />
    <Footer />
  </div>
</template>

<script>
import SendMessage from './components/SendMessage';
import Footer from './components/Footer';

export default {
  name: 'App',
  components: {
    SendMessage,
    Footer,
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #1c1c25;
  overflow: hidden;
  color: #fff;
}

.container {
  width: 100%;
  max-width: 1200px;
  height: 100%;
  margin: 0 auto;
  padding: 0 10px;
}

a {
  text-decoration: none;
}

</style>
