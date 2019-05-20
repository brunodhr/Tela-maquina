<template>
  <div id="app">
    <button @click="changeColors()">Trocar status</button>
    <div class="content-geral">
      <div class="content-timer" :style="myStyle">
        <span class="title-timer">00:15</span>
        <span class="title-min">MIN</span>
        <span class="title-stop">{{this.stopStatus}}</span>
      </div>
      <div class="content-wrapper" :style="bgStyle">
        <div class="content-inside">
          <div class="content-title" :style="myStyle">
            <span class="title-text" >
              {{this.nameStatus}}
            </span>
          </div>
          <div class="content-tela">
            <img src="./assets/gauge.svg" alt="">
            <img class="needle" src="./assets/needle.svg" alt="">
            <div class="inf-extremos">
              <span class="text-inf">0EE</span>
              <span class="text-inf">70%</span>
            </div>
            <div class="inf-curves">
              <img class="curve-right" src="./assets/curve.svg" alt="">
              <img class="curve-left" src="./assets/curve.svg" alt="">
            </div>
          </div>
        </div>
      </div>
    </div>
  <!-- <img src="./assets/modelo/Conceito.png" alt=""> -->
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      status: 1,
      nameStatus: 'Próxima parada às 22:00h',
      stopStatus: 'PARADA',
      myStyle: {
        backgroundColor: '#00C84F'
      },
      bgStyle: {
        backgroundColor: '#006E30'
      }
    }
  },
  methods: {
    changeColors () {
      this.status = this.status === 3 ? 1 : this.status + 1
      switch (this.status) {
        case 1:
          this.nameStatus = 'Próxima parada às 22:00h'
          this.stopStatus = 'PARADA'
          this.myStyle.backgroundColor = '#00C84F'
          this.bgStyle.backgroundColor = '#006E30'
          break
        case 2:
          this.nameStatus = 'Manutenção preventiva'
          this.stopStatus = 'PARADA'
          this.myStyle.backgroundColor = '#FABA18'
          this.bgStyle.backgroundColor = '#F89700'
          break
        case 3:
          this.nameStatus = 'Emergência acionada'
          this.stopStatus = ''
          this.myStyle.backgroundColor = '#F20000'
          this.bgStyle.backgroundColor = '#C10000'
          break
      }
    }
  }

}
</script>

<style>
.inf-curves{
  position: relative;
  bottom: 45px;
  display:flex;
  justify-content:space-between;
}
.curve-left{
  width:15%;
  transform: rotateY(180deg);
}
.curve-right{
  width:15%;
}
.text-inf{
  font-family:Arial;
  font-size:25px;
  font-weight: 900;
  color:white;
  background-color:black;
}
.needle{
  position: absolute;
  width:40px;
  top: 28px;
  left: 46%;
}
.inf-extremos{
  position: relative;
  bottom: 38px;
  padding: 0 15px;
  display:flex;
  justify-content:space-between;
}
.content-timer{
  height: 30%;
  width: 28%;
  position: absolute;
  left: 50%;
  top: 11%;
  transform: translate(-50%);
}
.title-timer{
  position:absolute;
  font-family:Arial;
  font-weight: bold;
  font-size:25px;
  left:5px;
  color:white;
}
.title-min{
  position:absolute;
  font-family:Arial;
  font-weight: bold;
  font-size:20px;
  left:14%;
  color:white;
}
.title-stop{
  position: absolute;
  font-family: Arial;
  font-weight: bold;
  font-size: 13px;
  left: 1%;
  color: white;
  top: 10%;
}
.title-text{
  position: absolute;
  top: 5%;
  right: 23%;
  color: white;
  font-family: Arial;
  font-weight: bold;
  font-size: 22px;
}
.content-title{
  height:200px;
  width:100%;
  position:absolute;
  clip-path: polygon(0% 0, 90% 0%, 82% 25%, 0 25%);
}
.content-inside{
  position: absolute;
  top: 1%;
  left: 50%;
  background-color: white;
  height: 690px;
  width: 98%;
  transform: translate(-50%);
  clip-path: polygon(30% 0%, 100% 0, 100% 100%, 0 100%, 0% 30%);
}
.content-tela{
position: absolute;
  top: 25%;
  left: 50%;
  height: 300px;
  width: 98%;
  transform: translate(-50%);
}
.content-wrapper{
  height:700px;
  width: 30%;
  position: absolute;
  left: 50%;
  transform: translate(-50%);
  clip-path: polygon(30% 0%, 100% 0, 100% 100%, 0 100%, 0% 30%);
}
#app {
  margin-top: 60px;
}
</style>
