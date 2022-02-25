<script>
  import axios from 'axios'
  export default {
    methods: {
      async saveDate(){
        try{
          const getIp = await axios.get('https://api.ipify.org?format=json')
        } catch(error){
          console.error();
        }
      }
    },
    data() {
      return {
        ip: '',
        city: '',
        region: '',
        country: '',
        timezona: ''
      }
    },
  }
</script>

<template>
<br>
  <div class="container">
    <div class="card center">
      <h2>Your IP Address Info</h2>
      <div class="flex card">
        <div class="box">
          <p>Hello</p>
          <br>
          <span>111</span>
        </div>
        <div class="box">
          <p>Hello</p>
          <br>
          <span>111</span>
        </div>
        <div class="box">
          <p>Hello</p>
          <br>
          <span>111</span>
        </div>
        <div class="box">
          <p>Hello</p>
          <br>
          <span>111</span>
        </div>
        <div class="box">
          <p>Hello</p>
          <br>
          <span>111</span>
        </div>
      </div>
    </div>
  </div>

</template>

<style>
span{
  display: block;
  margin-bottom: 7px;
}

.flex{
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  text-align: center;
}

.box{
  width: 20%;
  border: 4px solid;
  border-left: 3px solid;
  border-right: 3px solid;
  border-radius: 18px 0px 18px 0px;
  margin: 0px 10px;
}

.box span:nth:nth-child(1){
  font-weight: 800;
  font-size: 22px;
}
</style>
