<template>
<div>
  <form @submit.prevent="formSubmit()">
    <Input
      v-model="email"
      label="Ton mail"
      id="mail"
      type="email"
      name="email"
      :required="true"
    />
    <Input
      v-model="cgu"
      label="J'ai lu et accepte les CGU"
      id="cgu"
      type="checkbox"
      name="cgu"
      :required="true"
    />
    <!-- your other form fields go here -->
    <button type="submit">S'inscrire à la newsletter</button>
  </form>
  </div>
</template>
<script>
export default {
  data(){
      return{
        email:"",
        cgu:false
      }
  },
  methods:{
    formSubmit(){
      fetch("https://formspree.io/f/mnqwvkne", {
        method: 'POST',
        body: JSON.stringify({
          'email' : this.email,
          'cgu' : this.cgu,
        }),
        headers: {
            'Accept': 'application/json',
            'Content-type' :'application/json'
        }
      }).then(response => {
        if (response.ok) {
          console.log("Thanks for your submission!")
        } else {
          response.json().then(data => {
            if (Object.hasOwn(data, 'errors')) {
              console.log( data["errors"].map(error => error["message"]).join(", "))
            } else {
              console.log("1:Oops! There was a problem submitting your form")
            }
          })
        }
      }).catch(error => {
        console.log("Oops! There was a problem submitting your form")
      });
    }
  }
}
</script>
