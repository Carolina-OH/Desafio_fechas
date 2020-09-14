<template>
  <div id="app">
    <p id="titulo"> {{ message }}</p>
    <p id="tiempoatras">{{time}}</p>
    <button class="btn-white" @click="count(3)">3s</button>
    <button class="btn-white" @click="count(60)">1m</button>
    <button class="btn-white" @click="count(300)">5m</button>
    <button class="btn-white" @click="count(600)">10m</button>
    <button class="btn-white" @click="count(1800)">30m</button>

  </div>
</template>

<script>
let interval
  export default {
    name: "contador",
    data() {
      return {
        message: 'Cuenta Regresiva',
        time:"00:00"
      };
    },
    methods:{
        count:function(seg){
            const now= Date.now()          
            const end= now + ((seg+1)*1000)
            this.stopInterval(end)
            
        },
        stopInterval:function(end){
            interval=setInterval(()=>{
                const resto = Math.round((end-Date.now())/1000);
                if (resto<0){
                    clearInterval(interval);
                    return;
                }
                const minutes= Math.floor((resto % 3600)/60);
                const seconds= resto % 60;
                console.log(minutes, seconds)
                //this.time=`${minutes}:${seconds}`
                if ((String(seconds).length)===1 && (String(minutes).length)===1 ){
                    this.time=`0${minutes}:0${seconds}`
                }else if((String(seconds).length)===1 && (String(minutes).length)!=1 ){
                    this.time=`${minutes}:0${seconds}`
                }else if((String(seconds).length)!=1 && (String(minutes).length)===1 ){
                    this.time=`0${minutes}:${seconds}`
                }else{
                this.time=`${minutes}:${seconds}`
                }
                
            },1000)
            
        }
    },
    mounted:function(){
       // this.count()
    }
  }

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Knewave&family=Russo+One&display=swap');
  #app {
    font-size: 25px;
    font-family: 'Russo One', sans-serif;
    text-align:center;
    margin-top:5%;
  }
  #titulo{
      font-size:60px
  }
  button{
      font-family: Arial, Helvetica, sans-serif;
      font-size:15px;
      margin-top:20px;
      margin-left:10px;
  }

#tiempoatras{
    font-family:'Knewave', cursive;
    font-size:50px;
    color:brown;
}
</style>