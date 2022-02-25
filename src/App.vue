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
      <h2>Your IP Address Info</h2>
      <div class="flex card">
        <div class="box">
          <p>IP:</p>
          <hr>
          <span>{{ ip }}</span>
        </div>
        <div class="box">
          <p>City:</p>
          <hr>
          <span>{{ city }}</span>
        </div>
        <div class="box">
          <p>Country:</p>
          <hr>
          <span>{{ country }}</span>
        </div>
        <div class="box">
          <p>Region:</p>
          <hr>
          <span>{{ region }}</span>
        </div>
        <div class="box">
          <p>Timezone:</p>
          <hr>
          <span>{{ timezone }}</span>
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
  width: 30%;
  border: 4px solid;
  border-left: 3px solid;
  border-right: 3px solid;
  border-radius: 10px 10px 0px 0px;
  margin: 0px 10px;
}

.box span:nth-child(1){
  font-weight: 800;
  font-size: 22px;
}
</style>
