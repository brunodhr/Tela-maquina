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
            <img :style="needleStyle" src="./assets/needle.svg" alt="">
            <div class="inf-extremos">
              <span class="text-inf">0EE</span>
              <span class="text-inf">70%</span>
            </div>
            <div class="inf-curves">
              <img class="curve-right" src="./assets/curve.svg" alt="">
              <img class="curve-left" src="./assets/curve.svg" alt="">
            </div>
          </div>
          <div class="round-info"></div>
          <div class="info-boxes">
            <div class="single-box">
              <span class="text-box">DESEJADA</span>
              <span class="numbers-box">7000</span>
            </div>
            <div class="single-box">
              <span class="text-box">REALIZADA</span>
              <span class="numbers-box">4850</span>
            </div>
            <div class="single-box">
              <span class="text-box">REFUGO</span>
              <span class="numbers-box">150</span>
            </div>
          </div>
          <div class="box-grafico">
            <span class="graf-1"></span>
            <span class="graf-2"></span>
            <span class="graf-3"></span>
            <span class="graf-4"></span>
            <span class="graf-5"></span>
          </div>
          <div class="box-timer">
            <dir class="timers">
              <img class="clock-img" src="./assets/clock.svg" alt="">
              <div class="rets-imgs">
                <div class="single-box-timer">
                  <img class="ret-img" src="./assets/ret_green.svg" alt="">
                  <span class="timer-clock">20:00</span>
                  <span class="timer-ref">H</span>
                </div>
                <div class="single-box-timer">
                  <img class="ret-img" src="./assets/ret_orange.svg" alt="">
                  <span class="timer-clock">03:00</span>
                  <span class="timer-ref">H</span>
                </div>
                <div class="single-box-timer">
                  <img class="ret-img" src="./assets/ret_red.svg" alt="">
                  <span class="timer-clock">01:00</span>
                  <span class="timer-ref">H</span>
                </div>
              </div>
            </dir>
          </div>
          <div class="box-ruler">
            <dir class="rule">
              <img class="rule-img" src="./assets/rule.svg" alt="">
              <span class="rule-percent">100%</span>
            </dir>
          </div>
        </div>
      </div>
    </div>
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
      },
      needleStyle: {
        position: 'absolute',
        width: '40px',
        top: '56px',
        left: '70%',
        transform: 'rotate(25deg)'
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
          this.needleStyle = {
            position: 'absolute',
            width: '40px',
            top: '56px',
            left: '70%',
            transform: 'rotate(25deg)'
          }
          break
        case 2:
          this.nameStatus = 'Manutenção preventiva'
          this.stopStatus = 'PARADA'
          this.myStyle.backgroundColor = '#FABA18'
          this.bgStyle.backgroundColor = '#F89700'
          this.needleStyle = {
            position: 'absolute',
            width: '40px',
            top: '28px',
            left: '46%'
          }
          break
        case 3:
          this.nameStatus = 'Emergência acionada'
          this.stopStatus = ''
          this.myStyle.backgroundColor = '#F20000'
          this.bgStyle.backgroundColor = '#C10000'
          this.needleStyle = {
            position: 'absolute',
            width: '40px',
            top: '55px',
            left: '23%',
            transform: 'rotate(-23deg)'
          }
          break
      }
    }
  }

}
</script>

<style>
.single-box-timer{
  position: relative;
}
.timer-clock{
  position:absolute;
  left:20%;
  top:30%;
  font-family:Arial;
  font-size:25px;
  font-weight: bold;
  color:white;
}
.timer-ref{
    position: absolute;
    right: 11%;
    top: 10%;
    font-family: Arial;
    font-size: 15px;
    font-weight: bold;
    color: white;
}
.rets-imgs{
  display:flex;
}
.clock-img{
  top: 1px;
  height: 55px;
  z-index: 1;
  left: 6%;
  position: absolute;
}
.ret-img{
  height:40px;
}
.timers{
  width:100%;
  display:flex;
  justify-content: space-around;
}
.rule{
  border:3px solid black;
  border-radius:5px;
  width:70%;
  position:absolute;
  background-image: linear-gradient(to right,#00C84F 50%, #00C84F 70%, yellow 70%, yellow 95%, red 90%, red );
  height:35px;
}
.rule-img{
  width:100%;
  position: absolute;
  left: 0px;
  bottom: 1px;
}
.rule-percent{
  position: absolute;
  right: -10%;
}
.box-timer{
  background-color: white;
  position: absolute;
  width: 100%;
  height: 55px;
  bottom: 65px;
  display:flex;
  justify-content: center;
}
.box-ruler{
  background-color: white;
  position: absolute;
  width: 100%;
  height: 55px;
  bottom: 10px;
  display:flex;
  justify-content: center;
}
.box-grafico{
  background-color: white;
  position: absolute;
  width: 100%;
  height: 55px;
  bottom: 101px;
  padding: 34px 0px;
}
.graf-1{
  left: 140px;
  background-color: #F0FF00;
  position: absolute;
  width: 1%;
  height: 30px;
  bottom: 40px;
}
.graf-2{
  left: 150px;
  background-color: #59595C;
  position: absolute;
  width: 1%;
  height: 10px;
  bottom: 30px;
}
.graf-3{
  left: 160px;
  background-color: #00B756;
  position: absolute;
  width: 1%;
  height: 40px;
  bottom: 40px;
}
.graf-4{
  left: 170px;
  background-color: #F20000;
  position: absolute;
  width: 1%;
  height: 50px;
  bottom: 40px;
}
.graf-5{
  left: 180px;
  background-color: #59595C;
  position: absolute;
  width: 1%;
  height: 30px;
  bottom: 10px;
}
.round-info{
  position: absolute;
  width: 66%;
  height: 270px;
  top: 37%;
  right: 40px;
  border: double 55px transparent;
  border-radius: 100%;
  background-image: linear-gradient(white, white),
  radial-gradient(circle at top left, green 25%, green 25%, green 40%, red 40%, red 45% , yellow 45%, yellow 60%, #CFD1D2 60%, #CFD1D2);
  background-origin: border-box;
  background-clip: content-box, border-box;
}
.text-box{
  margin-bottom:10px;
  font-family:Arial;
  font-weight: bold;
  font-size:10px;
  text-transform: uppercase;
}
.numbers-box{
  font-family:Arial;
  font-weight: bold;
  font-size:25px;
  padding:15px 25px;
  background-color:#CFD1D2;
  border:3px solid #A5A6AA;
}
.info-boxes{
  display:flex;
  position:absolute;
  width: 100%;
  top:55%;
  justify-content: center;
}
.single-box{
  display:flex;
  flex-direction: column;
  align-items: center;
}
.content-geral{
  height:auto;
}
.inf-curves{
  position: relative;
  bottom: 50px;
  display:flex;
  justify-content:space-between;
}
.curve-left{
  width:10%;
  transform: rotateY(180deg);
}
.curve-right{
  width:10%;
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
.needle-red{
  position: absolute;
  width: 40px;
  top: 55px;
  left: 23%;
  transform: rotate(-23deg);
}
.needle-green{
  position: absolute;
  width: 40px;
  top: 56px;
  left: 70%;
  transform: rotate(25deg);
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
@media(min-width:1440px) and (max-width:1600px){
  .content-timer{
    left: 46%;
  }
  .title-min{
    left: 18% !important;
  }
}
@media(min-width:1024px) and (max-width:1439px){
  .content-timer{
    left: 41%;
  }
  .title-min{
    left: 25% !important;
  }
  .title-text{
    right: 17% !important;
  }
}
@media(min-width:768px) and (max-width:1023px){
  .content-timer{
    left: 32%;
  }
  .title-min{
    left: 33% !important;
  }
  .title-text{
    right: 18% !important;
  }
}
@media(min-width:425px) and (max-width:767px){
  .content-timer{
    left: 15%;
  }
  .title-min{
    left: 60% !important;
    font-size:15px !important;
  }
  .title-text{
    right: 18% !important;
    font-size:18px !important;
  }
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
@media(min-width:1440px) and (max-width:1800px){
  .content-wrapper{
    width:40%;
  }
}
@media(min-width:1024px) and (max-width:1439px){
  .content-wrapper{
    width:50%;
  }
}
@media(min-width:768px) and (max-width:1023px){
  .content-wrapper{
    width:70%;
  }
}
@media(min-width:320px) and (max-width:425px){
  .content-wrapper{
    width:100%;
  }
}
#app {
  margin-top: 60px;
}
</style>
