<template>
  <div>
    <b-form @submit="onSubmit" style="width:450px; margin:auto; margin-top:120px; padding:50px; background-color:white">
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
  methods: {
    onSubmit (evt) {
      evt.preventDefault()
      alert(JSON.stringify(this.form))
      this.$router.push('/home') 
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
a {
  color: #42b983;
}
.container{
  width: 400px;
  margin-top:100px
}
body{
  background-color:
}
</style>
