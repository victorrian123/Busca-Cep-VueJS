<template>
  <div>
    <body>
    <div class="app">
        <div class="card">
            <h1>Busca CEP</h1>
            <div class="card-body">
                <form>
                    <div class="fields">
                        <label for="cep">CEP:</label>
                        <input name="cep" maxlength="8" v-model="cep"/>
                    </div>
                    
                    <div class="fields">
                        <label for="adress">Endereco:</label>
                        <input type="text" name="adress" v-model="resultCep.logradouro"/>
                    </div>

                    <div class="fields">
                        <label for="complement">Complemento:</label>
                        <input type="text" name="complement" v-model="resultCep.complemento"/>
                    </div>

                    <div class="fields">
                        <label for="neighborhood">Bairro:</label>
                        <input type="text" name="neighborhood" v-model="resultCep.bairro"/>
                    </div>
                    
                    <div class="fields">
                        <label for="city">Cidade:</label>
                        <input type="text" name="city" v-model="resultCep.localidade"/>
                    </div>

                    <div class="fields">
                        <label for="state">Estado:</label>
                        <input type="text" name="state" v-model="resultCep.uf"/>
                    </div>

                </form>

                </div>
            </div>
        </div>
    </body>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
      return {
          cep: "",
          resultCep: ''
      }
  },
  watch: {
      cep(cepForm) {
          if (cepForm.length === 8) {
              fetch(`https://viacep.com.br/ws/${cepForm}/json`)
              .then(response => response.json())
              .then(response => {
                  console.log(response)
                    this.resultCep = response
                  }
              )
                  
          }
      }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600&family=Ubuntu:wght@700&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html, body {
    height: 100%;
}

body {
    background-color: #6ecfe7;
    display: flex;
    align-items: center;
    justify-content: center;
}

.app {
    display: flex;
    align-items: center;
}

.card {
    background-color: white ;
    padding: 30px 70px ;
    border-radius: 20px;
}

.card h1 {
   font-family: Poppins; 
}

.fields {
    margin-bottom: 15px;
}

label {
    display: block;
    font-family: Poppins;
    font-size: 15px;
    margin-bottom: 5px;

}

input {
    background-color: #f0f0f0;
    outline: 0;
    font-size: 18px;
    padding-left: 15px;
    width: 100%;
    height: 45px;
    border-radius: 10px;
    border: 0;
}



</style>
