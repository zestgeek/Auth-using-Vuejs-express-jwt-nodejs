<template>
  <div>
    <b-form @submit="onSubmit" style="width:450px; margin:auto; margin-top:120px; padding:50px; background-color:#efebeb">
    <h1 style="text-align:center; margin-bottom:20px">Signup</h1>
      <b-form-group id="exampleInputGroup1">
        <b-form-input id="exampleInput1"
                      type="text" v-model="form.name" required
                      placeholder="Name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="exampleInputGroup1">
        <b-form-input id="exampleInput1"
                      type="email" v-model="form.email" required
                      placeholder="Email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="exampleInputGroup2" >
        <b-form-input id="exampleInput2"
                      type="password" v-model="form.password" required
                      placeholder="Password"
        ></b-form-input>
      </b-form-group>

        
      <b-form-group id="exampleGroup4">
        <b-form-checkbox v-model="form.checked" id="exampleInput4">
          Check me out
        </b-form-checkbox>
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
        email: '',
        name: '',
        password: ''
      },
      foods: [
        { text: 'Select One', value: null },
        'Carrots', 'Beans', 'Tomatoes', 'Corn'
      ]
    }
  },
  created() {
    axios.get(`/api/register`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.form = response.data
    })
    .catch(e => {
      console.log(e)
    })

    
  },
  methods: {
    onSubmit (evt) {
      evt.preventDefault()
      this.$router.push('/home') 
    }
  }
}
</script>


<style scoped>


a {
  color: #42b983;
}
.container{
  width: 400px;
  margin-top:100px
}

</style>
