<template>
<main>
<!-- Header  -->
<header class="flex justify-center items-center px-4" title="Introdução a compra">
    <div class="containerX flex flex-col sm:flex-row justify-between items-center">
    <section class="mb-3 sm:mb-0">
        <h2 class="text-white text-2xl mb-2">Formulário para compra de</h2>
        <h1 class="text-white text-poppins text-5xl font-bold">Pacote de Stickers</h1>
    </section>
    <section>
      <img src="../assets/box.svg" class="efect" alt="Caixas flutuantes">
    </section>
  </div>
</header>

<!-- Escolha os Sticks  -->
<article class="flex justify-center items-center p-4" title="Escolha os seus Sticker">
  <div class="containerX">
    <h2 class="text-blue-dark text-2xl mb-2 text-poppins font-semibold">Quais stickers?</h2>

    <form>
      <fieldset class="flex items-center mb-2" title="React">
        <input class="mb-1" type="checkbox" name="react" id="react" value="react" v-model="CheckedStickers">
        <label for="react" class="ml-4 text-xl">React</label>
      </fieldset>

      <fieldset class="flex items-center mb-2" title="Vue">
        <input class="mb-1" type="checkbox" name="vue" id="vue" value="vue" v-model="CheckedStickers">
        <label for="vue" class="ml-4 text-xl">Vue</label>
      </fieldset>

      <fieldset class="flex items-center mb-2" title="Angular">
        <input class="mb-1" type="checkbox" name="angular" id="angular" value="angular" v-model="CheckedStickers">
        <label for="angular" class="ml-4 text-xl">Angular</label>
      </fieldset>
    </form>
  </div>
</article>

<!-- Quantidade de Stickes  -->
<article class="flex justify-center items-center p-4" title="Escolha a quantidade de Stickers">
  <div class="containerX">
    <h2 class="text-blue-dark text-2xl mb-2 text-poppins font-semibold">Quantos stickers de cada?</h2>

  <section class="flex items-center counter">
    <button v-bind:class="{disabled: active}" @click="ContLess()" class="outiline-none flex items-center justify-center count" title="Subtrair">-</button>
    <input v-model="CountInput" class="outiline-none p-2 mx-3 rounded border border-indigo-500 bg-gray-50" type="text">
    <button @click="ContMore()" class="outiline-none flex items-center justify-center count" title="Somar">+</button>
  </section>

  </div>
</article>

<!-- Lista  -->
<article class="flex justify-center items-center p-4" title="Lista de itens">
  <div class="containerX">
    <h2 class="text-blue-dark text-2xl mb-2 text-poppins font-semibold">Observações:</h2>

    <textarea v-model="text" class="outiline-none border border-indigo-500 p-2 w-full sm:w-3/4 bg-gray-50 rounded text-2xl" name="" id="">
    </textarea>

  </div>
</article>

<!-- Resultado  -->
<footer class="flex justify-center items-center p-4 py-5 h-36 bg-gray-50" title="Resultado">
  <div class="containerX flex flex-col sm:flex-row justify-between items center">
    <p :v-model="result" v-bind:class="{errorColor: error, sucessColor: sucess}" class=" font-semibold text-2xl text-poppins">{{ result }}</p>
    <button @click="SendForm()" class="bg-blue-dark text-white rounded p-3 w-32 mt-3 sm:mt-0 outiline-none">Enviar</button>
  </div>
</footer>

</main>
</template>


<script>
export default {
  data() {
    return {
      CheckedStickers: [],
      More: 0,
      less: 0,
      CountInput: 0,
      active: true,
      text: '',
      result: '',
      error: false,
      sucess: false,
    }
  },methods: {
 
    ContMore(){
    this.CountInput += this.More + 1  
    this.active = false
    },
    ContLess(){
    if(this.CountInput >= 1){
    this.CountInput += this.less - 1
    }
    },
    SendForm(){
      if(!this.CheckedStickers.length){ 
      this.result = "Escolha pelo menos um Sticker"
      this.error = true
      this.sucess = false
      }
      if(this.CountInput < 1){
        this.result = "Coloque pelo menos 1 Sticker"
        this.error = true
        this.sucess = false
      }else{
        this.result = "Formulário Enviado com sucesso"
         this.error = false
         this.sucess = true

         this.CountInput = 0
         this.text = ''
         this.CheckedStickers = []
      }
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@200;300;400;600;700;900&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;1,100;1,200;1,300;1,400;1,500;1,600&display=swap');
/* font-family: 'Cairo', sans-serif; */
/* font-family: 'Poppins', sans-serif; */

*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body{
font-family: 'Cairo', sans-serif;
color: #2F3676;  
}


img{
  display: block;
  width: 100%;
  height: 100%;
}
ul, ol, a{
  text-decoration: none;
  list-style: none;
  color: #2F3676;
}
.containerX{
  width: 960px;
  margin: 0 auto;
  box-sizing: border-box;
}
.outiline-none{
  outline: none;
}
.text-poppins{
font-family: 'Poppins', sans-serif;
}
.text-blue-dark{
color: #2F3676;
}
.text-white{
color: #ffffff;
}
.text-black{
color: #101010;
}
.bg-gray{
  background-color: #DDE3E9;
}
.bg-blue-dark{
background-color: #2F3676;
}
/* ------------------------ */
header{
  height: 25.125rem;
  background-image: url("../assets/banner.svg");
  background-size: cover;
  background-position: bottom;
  background-repeat: no-repeat;
}
/* ------------------------ */
input[type="checkbox"]::before {
    content: " ";
    width: 1.25rem;
    height: 1.25rem;
    position: absolute;
    background-color: #fff;
    border: 0.125rem solid #2F3676;
    border-radius: 0.125rem;
  }
  
input[type="checkbox"]:checked::after {
  content: " ";
  width: 1.25rem;
  height: 1.25rem;
  border-color: #2F3676;
  background-color: #2F3676;
  border-style: solid;
  border-width: 0 0.1875rem 0.1875rem 0;
  border-radius: 0.125rem;
  position: absolute;
 }

  textarea{
    height: 12.5rem;
    resize: none;
  }
/* ------------------------------------ */
.count{
  width: 2.5rem;
  height: 2.5rem;

  border: 0;
  border-radius: 0.25rem;
  background-color: #2F3676;
  color: #fff;
  font-size: 1.5625rem;
  line-height: inherit;
  font-weight: 600;
}
.counter input{
  height: 2.5rem;
}
/* ------------------------------------ */

.efect{
  animation: Efect linear infinite 4s;
}
.disabled{
  background-color: #999999;
}
.errorColor{
  color: #700;
}
.sucessColor{
  color: #070;
}
@keyframes Efect{
  0% {
    transform: translateY(0%);
  }
  30%{
    transform: translateY(-10%);
  }
  60%{
    transform: translateY(0%);
  }
  80%{
    transform: translateY(10%);
  }
  100%{
    transform: translateY(0%);
  }
}
</style>
