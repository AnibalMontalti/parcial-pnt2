<template>

    <section class="src-components-caracteres">

        <h1>NT2 Parcial - Anibal Montalti</h1>

        <input type="text" id="texto" v-model.trim="texto" placeholder="Ingrese su texto aquí">

        <div v-if="caracteres.cantidad > 0">
            <p>Cantidad caracteres = {{ caracteres.cantidad }}</p>

            <p> 1 - {{ this.codificado() }} (codificado)</p>
            <p> 2 - {{ this.mayuscula() }} (mayuscula)</p>
            <p> 3 - {{ this.minuscula() }} (minuscula)</p>
            <p> 4 - {{ this.mayMin() }} (mayuscula / minuscula)</p>
            <p> 5 - {{ this.minMay() }} (minuscula / mayuscula)</p>
            
        </div>
        
        <hr/>
        <p>Respuestas: 1: C | 2: C | 3: A</p>

    </section>

</template>

<script lang="js">
export default {
  name: 'src-components-formulario',
  props:[],
  mounted(){
    
  },
  data(){
    return {
        texto:'',
        cantCaracteres: 0,        
    }
  },
  methods:{
   codificado(){    
    let textoMin = this.texto.toLowerCase()
    let resultado = ''
    for(let i = 0; i< textoMin.length; i++){
        switch(this.texto[i]){
            case 'a':
                resultado += 'u';
                break;
            case 'e':
                resultado += 'o';
                break;
            case 'o':
                resultado += 'e';    
                break;
            case 'u':
                resultado += 'a';            
                break;
            default:
                resultado += this.texto[i];
        }          
    }
    return resultado;    
   },
   mayuscula(){
    return this.texto.toUpperCase()
   },
   minuscula(){
    return this.texto.toLowerCase()
   },
   mayMin(){    
    let resultado = ''
    for(let i = 0; i< this.texto.length; i++){
        if(i%2 == 0)
            resultado += this.texto[i].toUpperCase()        
        else
            resultado += this.texto[i].toLowerCase()             
    }
    return resultado
   },
   minMay(){
    let resultado = ''
    for(let i = 0; i< this.texto.length; i++){
        if(i%2 == 0)
            resultado += this.texto[i].toLowerCase()        
        else
            resultado += this.texto[i].toUpperCase()             
    }
    return resultado
   },

  },
  computed:{
    caracteres(){
        return {
            cantidad: this.texto.length,
        }
    }
  }
}
</script>

<style scoped lang="css">
    .src-components-caracteres {        
    }
</style>