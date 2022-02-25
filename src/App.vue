<script>
  import axios from 'axios'
  export default {
    created () {
      this.saveDate()
    },

    methods: {
      async saveDate(){
        try{
          const { data } = await axios.get('https://api.ipify.org?format=json')
          console.log(data)

          axios.get(`http://ip-api.com/json/${data.ip}`)
          .then(res => {
            console.log(res.data)
            this.ip = res.data.query
            this.city = res.data.city
            this.country = res.data.country
            this.region = res.data.region
            this.timezone = res.data.timezone
          })
        } catch(error){
          console.log(error)
        }
      }
    },
    data() {
      return {
        ip: '',
        city: '',
        region: '',
        country: '',
        timezone: ''
      }
    },
  }
</script>

<template>
<br>
  <div class="container">
    <div class="card center">
      <h2>Want to know your IP address?</h2>
      <button class="btn primary" @click="saveDate()">Click me</button>
      <br> <br>
      <div v-show="saveDate()" class="flex card">
        <div class="box">
          <p>IP:</p>
          <hr>
          <span v-if="this.ip !== ''">{{ ip }}</span>
           <small v-else>Loading..</small>
        </div>
        <div class="box">
          <p>City:</p>
          <hr>
          <span v-if="this.city !== ''">{{ city }}</span>
           <small v-else>Loading..</small>
        </div>
        <div class="box">
          <p>Country:</p>
          <hr>
          <span v-if="this.country !== ''">{{ country }}</span>
           <small v-else>Loading..</small>
        </div>
        <div class="box">
          <p>Region:</p>
          <hr>
          <span v-if="this.region !== ''">{{ region }}</span>
           <small v-else>Loading..</small>
        </div>
        <div class="box">
          <p>Timezone:</p>
          <hr>
          <span v-if="this.region !== ''">{{ timezone }}</span>
          <small v-else>Loading..</small>
        </div>
      </div>
    </div>
  </div>

</template>

<style>
span{
  display: block;
  margin-bottom: 10px;
}

.flex{
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  text-align: center;
}

.box{
  width: 45%;
  border-left: 3px solid;
  border-right: 3px solid;
  border-radius: 15px 15px 15px 15px;
}

.box span:nth-child(1){
  font-weight: 800;
  font-size: 22px;
}

small{
  color: #ff0000;
  font-size: 15px;
  font-weight: 700;
}
</style>
