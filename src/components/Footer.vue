<template>
  <footer>
    <div class="container">
      <p>Por <span>Lucas Farias</span> 💜</p>
      <a class="imgLinkedin" href="https://www.linkedin.com/in/lucasfariasm/" target="_blank">
        <img  src="../assets/linkedin.png" alt="">
      </a>
    </div>
  </footer>
</template>

<script>
export default {

}
</script>

<style scoped>
footer {
  width: 100%;
  height: 20%;
  position: absolute;
  bottom: 0;
}

footer div {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

a {
  display: flex;
  align-items: center;
}

.imgLinkedin, .imgLinkedin img {
  height:70%;
  transition: .2s;
}

.imgLinkedin:hover {
  color: #fff;
  opacity: .5;
}

</style>