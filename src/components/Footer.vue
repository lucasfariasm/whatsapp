<template>
  <footer>
    <div>
      <p>Design e código por <span>Lucas Farias de Moura</span> 💜</p>
      <a class="imgLinkedin" href="https://www.linkedin.com/in/lucasfariasm/" target="_blank" title="Linkedin">
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
    height: 50px;
    position: absolute;
    bottom: 0;
  }

  footer div {
    margin: 0;
    max-width: 1200px;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  a {
    display: flex;
    align-items: center;
  }

  .imgLinkedin, .imgLinkedin img {
    height:100%;
    transition: .2s;
  }

  .imgLinkedin:hover {
    opacity: .5;
  }

  @media (max-width: 500px){
    footer {
      width: initial;
      max-width: 100%!important;
      position: initial;
    }

    p {
      font-size: 14px;
    }
  }
</style>