<template>

  <div class="corpo">
    <div class="picture">
      <img :src="foto" height="710" width="700"/>
    </div>

    <div class="loader-wrapper">
      <span class="loader"><span class="loader-inner"></span></span>
    </div>

    <div class="buscador-cep">
      <h1>Busque seu CEP aqui.</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. {{input}}</p>
      <div class="buscador-cep-form">
        <input
          v-model="input"
          type="text"
          class="textInput"
          placeholder="Digite seu CEP aqui"
        />
        <input type="submit" class="btn" value="Buscar" @click='bringPhoto()'/>
      </div>
    </div>
  </div>

</template>

<script>

export default {
  data() {
    return {
      foto: {},
      input: ''
    };
  },

  methods: {

    bringPhoto: function () {
      
      if (this.input == "cachorro"){
        
        let promise = this.$http.get('https://dog.ceo/api/breeds/image/random');
    
        promise.then (res => {
         
          this.foto = res.body.message
          
          });

      } else if(this.input == "gato"){
          let promise = this.$http.get('https://api.thecatapi.com/v1/images/search');

          promise.then (res => {
            console.log(res.body)
            this.foto = res.body[0].url
          })
      }

    }
  }
};

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: coral;
  font-family: poppins, sans-serif;
}

.corpo {
  background-color: white;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

.picture {
  width: 50%;
  background-size: cover;
}

.buscador-cep {
  width: 50%;
  padding: 200px 8%;
}

.buscador-cep h1 {
  margin-bottom: 20px;
  font-weight: 900;
  color: #2c3a47;
}

.buscador-cep p {
  margin-bottom: 40px;
  font-size: 14px;
  color: #777;
}

.buscador-cep-form {
  height: 68px;
  background: coral;
  border-radius: 3px;
  display: flex;
  padding: 8px 0;
}

.textInput,
.btn {
  background: none;
  border: none;
  font-size: 15px;
  outline: none;
  transition: 0.2s linear;
}

.textInput {
  width: calc(100% - 120px);
  padding: 20px;
  color: #f1f1f1;
}

.textInput::placeholder {
  color: #f1f1f1;
}

.textInput:focus {
  padding-left: 30px;
}

.btn {
  width: 120px;
  text-transform: uppercase;
  color: #f1f1f1;
  cursor: pointer;
  border-left: 1px solid #777;
}

.btn:hover {
  color: #f1f1f1;
}

</style>
