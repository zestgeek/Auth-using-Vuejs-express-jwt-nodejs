<template>
  <div>
    <b-form @submit="onSubmit" style="width:450px; margin:auto; margin-top:120px; padding:50px; background-color:#efebeb">
    <h1 style="text-align:center; margin-bottom:20px">Signup</h1>
      <b-form-group id="exampleInputGroup1">
        <b-form-input id="exampleInput1"
                      type="text" v-model="form.username" required
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
      <b-form-group id="exampleInputGroup2" >
        <b-form-input id="exampleInput2"
                      type="password" v-model="form.confirm_password" required
                      placeholder="Confirm_Password"
        ></b-form-input>
      </b-form-group>

        
      <b-form-group id="exampleGroup4">
        <b-form-checkbox v-model="form.checked" id="exampleInput4">
          Check me out
        </b-form-checkbox>
        <a style="float:right" href="/">login?</a>
      </b-form-group>
      
      <b-button  type="submit" variant="primary" style="width:100%">Submit</b-button>
      <b-modal id="modalsm" style="text-align:center" ref="modal" size="sm" hide-footer>
      <div style="color:#28a745; font-size:20px">
      <b>Register Successfully!</b>
      </div>
      <b-btn class="mt-3" variant="outline-success" style="float:right" @click="onClick">Login</b-btn>
    </b-modal>
      
      
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
        username: '',
        password: '',
        confirm_password:''
      },
     
    }
  },
  
  methods: {
    onSubmit (evt) {
      evt.preventDefault()
    axios.post(`http://localhost:3003/api/register`, this.form)
    .then(response => {
      // JSON responses are automatically parsed.
      this.form = response.data;
      if(this.form.status === 200)
      this.$refs.modal.show()
    })
    .catch(e => {
      console.log(e)
    })
    },
    onClick(e){
      e.preventDefault();
      this.$router.push('/')
    }
  }
  /*created(evt) {
  console.log(evt)
    evt.preventDefault()
    axios.post(`http://localhost:3003/api/register`, this.form)
    .then(response => {
      // JSON responses are automatically parsed.
      this.form = response.data
    })
    .catch(e => {
      console.log(e)
    })

    
  },*/
}
</script>


<style scoped>


a{
  text-decoration:none;
}
.container{
  width: 400px;
  margin-top:100px
}

</style>
