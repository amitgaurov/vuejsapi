<template>
    <div id="create">
        <h1>Doctor</h1>
        <input type="text" name="name" v-model="name" placeholder="name" />
        <input type="text" name="email" v-model="email" placeholder="email" />
        <input type="password" name="password" v-model="password" placeholder="Password" />
        <input type="text" name="specialist" v-model="specialist" placeholder="specialist" />
        <button type="button" v-on:click="create()">create</button>
    </div>
</template>

<script>
var axios = require('axios')
    export default {
        name: 'login',
        data() {
              return{
                    name: "",
                    email:"",
                    password: "",
                    specialist:""
                }
            },
        methods: {
                  create: function () {
                    alert(this.name)
                    axios.post(`http://localhost:3000/api/doctors`,
                      {
                        params:{
                            name:this.name,
                            email:this.email,
                            password:this.password,
                            specialist:this.specialist }

                      },
                      {
                        headers: {
                        'Content-Type': 'application/x-www-form-urlencoded',
                                         'Accept': 'application/json'
                                  }
                       }
                     )
                     .then(response => {this.data = response.data})
                     }
                   }
                }
</script>

<style scoped>
    #login {
        width: 500px;
        border: 1px solid #CCCCCC;
        background-color: #FFFFFF;
        margin: auto;
        margin-top: 200px;
        padding: 20px;
    }
</style>
