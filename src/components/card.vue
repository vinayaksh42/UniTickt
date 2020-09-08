<template>
    <div class="-shadow" id="box" :class="{ done: status }">
      <h4 class="title">
        {{ name }}
      </h4>
      <span class="eyebrow">
        email: {{ email }}
      </span>
      <br>
      <span class="eyebrow">
        Message: {{ msg }}
      </span>
      <br>
        <div>
            <b-button v-if="status" variant="danger" @click="submit(id)">Mark Uncomplete</b-button>
            <b-button v-else variant="success" @click="submit(id)">Mark Complete</b-button>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    props: ['email','name','msg','status','id'],
    methods: {
        submit(node) {
            this.status = !this.status
            axios.put(`https://hack-the-mountain.firebaseio.com/hackathon/${node}/status.json`,this.status)
            .then(()=>console.log('updated'))   
      },
    }
}
</script>

<style scoped>
.done{
    border-top: 4px solid lightcoral !important;
}
#box {
  padding: 20px;
  margin-bottom: 24px;
  transition: all 0.2s linear;
  border-top: 4px solid lightgreen;
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.2), 0 1px 5px 0 rgba(0, 0, 0, 0.19);
}
#box:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
}
.title {
  margin: 0;
  color: black;
}
a {
  text-decoration: none;
}
#switch{
    display: block;
    margin: 0 auto;
}
h4{
    text-align: center;
}
#time{
    float: right;
}
h6{
    text-align: center;
}
button{
    margin: 5px;
}
</style>