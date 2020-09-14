<template>
  <div id="app">
   <p> {{ message }}</p>
    <p>{{time}}</p>
    <button @click="count(3)">3s</button>
    <button @click="count(60)">1m</button>
    <button @click="count(300)">5m</button>
    <button @click="count(600)">10m</button>
    <button @click="count(1800)">30m</button>

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
                this.time=`${minutes}:${seconds}`
                
            },1000)
            
        }
    },
    mounted:function(){
       // this.count()
    }
  }

</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    background: lightblue;
    text-align:center
  }
</style>