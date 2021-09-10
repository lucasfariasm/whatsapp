<template>
  <section>
    <div class="color"></div>
    <div class="color"></div>
    <div class="color"></div>
    <div class="card">
      <div class="square" style="--i:0"></div>
      <div class="square" style="--i:2"></div>
      <div class="square" style="--i:3"></div>
      <div class="content">
        <div class="inputs">
          <div class="inputCode">
            <img 
              :src="code.image" 
              alt="Country Image" 
              width="30" 
              height="100%">
            <select v-model="code" >
              <option 
                v-for="(country, index) in country" 
                :key="index" 
                :value="country"
              >
                {{country.name}} | +{{country.callingCode}}
              </option>
            </select>
            <input
              type="number"
              placeholder="DDD" 
              maxlength="3"
              oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);"
              v-model="ddd">
          </div>
          <div class="inputNumber">
            <input 
              type="number"
              maxlength="10"
              oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);"
              placeholder="Número" 
              v-model="number"
              @keyup.enter="sendMessage">
          </div>
          <div class="btn">
            <button :title="'(' + ddd +') ' + number.replace(/(\d)(\d{4})$/, '$1-$2')" @click="sendMessage">
              <img src="../assets/send.png" alt="">
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      country: [],
      code: {
        name: "Brazil",
        callingCode: '55',
        image: 'https://restcountries.eu/data/bra.svg',
      },
      ddd: '',
      number: '',
    }
  },
  methods: {
    sendMessage(){
      window.open(`https://api.whatsapp.com/send?phone=+${this.code.callingCode}${this.ddd}${this.number}`);
    },
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
      .then( response => response.json())
      .then( response => {
        const countries = response.map( item => (
          {
            name: item.name,
            callingCode: item.callingCodes[0],
            image: item.flag
          }
        ));

        this.country = countries;
      })
  }
}
</script>

<style scoped>
  section{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  section .color {
    position: absolute;
    filter: blur(200px);
  }

  section .color:nth-child(1) {
    top: -350px;
    width: 600px;
    height: 600px;
    background: #ffb8b8;
  }

  section .color:nth-child(2) {
    bottom: -150px;
    left: 100px;
    width: 500px;
    height: 500px;
    background: #3dc1d3;
  }

  section .color:nth-child(3) {
    bottom: 50px;
    right: 100px;
    width: 300px;
    height: 300px;
    background: #4BFF33;
  }

  .card {
    position: relative;
    max-width: 650px;
  }

  .card .square {
    position: absolute;
    border-radius: 50%;
  }

  .card .square:nth-child(1) {
    background: linear-gradient(#f00, #f0f);
    top: -130px;
    right: -80px;
    width: 200px;
    height: 200px;
    animation: animate1 10s linear infinite;
    animation-delay: calc(-1s * var(--i));
  }

  .card .square:nth-child(2) {
    background: linear-gradient(rgb(0, 152, 240), rgb(4, 87, 211));
    bottom: 120px;
    left: -80px;
    width: 180px;
    height: 180px;
    animation: animate2 10s linear infinite;
    animation-delay: calc(-1s * var(--i));
  }

  .card .square:nth-child(3) {
    background: linear-gradient(#4BFF33, #48963D);
    bottom: -100px;
    right: 100px;
    width: 185px;
    height: 185px;
    animation: animate3 10s linear infinite;
    animation-delay: calc(-1s * var(--i));
  }

  .content {
    padding: 100px 10px;
    border-radius: 20px;
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
    background-color: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(5px);
  }

  .inputs {
    width: 82%;
    margin: 0 auto;
  }

  .inputs input, .inputs select, .btn button {
    width: 100%;
    height: 60px;
    border-radius: 30px;
  }

  .inputs input, .inputs select {
    outline: none;
    border: 1px solid #000;
    background: rgba(0, 0, 0, .4);
    color: rgba(255, 255, 255, .7);
    font-size: 17px;
    margin: 15px 0;
    text-align-last: center;
  }

  option {
    background-color: #000;
    color: rgba(255, 255, 255, .7);
  }

  .inputCode {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .inputCode input, .inputs select {
    width: 45%;
  }

  .btn {
    max-width: 200px;
    margin: 20px auto 0;
  }

  .btn button {
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    cursor: pointer;
    transition: .2s; 
    background:  #4BFF33;
    box-shadow: 0 0 10px #4BFF33 ,6px 12px 25px rgba(72,150,61,.64);
  }

  .btn button:hover {
    opacity: .7;
  }

  .btn img {
    max-height: 20px;
  }

  input:focus, select:focus {
    border-color: #4BFF33;
  }

  input[type="number"]::-webkit-outer-spin-button,
  input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  input[type="number"] {
    -moz-appearance: textfield;
  }


  @keyframes animate1 {
    0%,100% {
        transform: translateY(-80px) translateX(-50px);
    }

    50% {
        transform: translateY(100px) translateX(50px);
    }
  }

  @keyframes animate2 {
    0%,100% {
        transform: translateY(-200px);
    }

    50% {
        transform: translateY(180px);
    }
  }

  @keyframes animate3 {
    0%,100% {
        transform: translateY(100px) translateX(-50px);
    }

    50% {
        transform: translateY(-100px) translateX(100px);
    }
  }

  @media (max-width: 500px) {
    .inputs, .btn{
      width: 90%;
    }

    .inputCode {
      display: flex;
      flex-direction: column;
    }

    .inputCode select, .inputCode input {
      width: 100%;
    }
  }
</style>