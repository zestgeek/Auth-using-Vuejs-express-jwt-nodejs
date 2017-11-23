
<template>
  <div>
    <b-form @submit="onSubmit" style="width:450px; margin:auto; margin-top:120px; padding:50px; background-color:#efebeb">
    <h1 style="text-align:center; margin-bottom:20px">Login</h1>
      <b-form-group id="exampleInputGroup1">
        <b-form-input id="exampleInput1"
                      type="text" v-model="form.username" required
                      placeholder="Username"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="exampleInputGroup2">
        <b-form-input id="exampleInput2"
                      type="password" v-model="form.password" required
                      placeholder="Password"
        ></b-form-input>
      </b-form-group>
      
      <b-form-group id="exampleGroup4">
        <b-form-checkbox v-model="form.checked" id="exampleInput4">
          Check me out
        </b-form-checkbox>
        <router-link to="signup" style="float:right">signup?</router-link>
      </b-form-group>
      <b-button type="submit" variant="primary" style="width:50%">Submit</b-button>
      <b-button type="reset" variant="secondary" style="width:48%">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data () {
    return {
        form: {
        username: '',
        password: '',
      },
    }
  },
  methods: {
    onSubmit (evt) {
      evt.preventDefault()
      // this.$router.push('/home')
    axios.post(`http://localhost:3003/api/login`, this.form)
    .then(response => {
      // JSON responses are automatically parsed.
      this.form = response.data
      sessionStorage.setItem('token',response.data.token);
      this.$router.push('/home')
    })
    .catch(e => {
      console.log(e)
    })
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}   
li {
  display: inline-block;
  margin: 0 10px;
}
a{
  text-decoration:none;
}
.container{
  width: 400px;
  
}


</style>
