<template>
<div>
    <div class="nav">
        <h1>Contact Us Query</h1>
        <nav>
            <h3>Time(IST): {{timestamp}} </h3>
        </nav>
    </div>
    <hr id="line">
</div>
  
</template>

<script>
export default {
    data() {
        return{
            timestamp: null
        };
    },
    created() {
        
                const today = new Date();
                const date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
                const time = today.getHours() + ":" + today.getMinutes() ;
                const dateTime = date +' '+ time;
                this.timestamp = dateTime;
            
        },
}
</script>

<style scoped>
h3{
    font-size: 1.4em;
  color: #39b982; 
 
}
.brand {
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  font-size: 1.5em;
  color: #39b982;
  text-decoration: none;
}
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 60px;
}

#line{
  border: 2px solid lightblue;
  border-radius: 5px;
}
</style>