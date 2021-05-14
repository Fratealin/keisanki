<template>
  <div class="hello">
    <h1>{{numberone}} {{operator}} {{numbertwo}} equals
        
        <span v-if="operator == '+'" > {{add}}</span>
        <span v-else-if="operator == '-'"> {{minus}}</span>
        <span v-else-if="operator == '*'"> {{multiply}}</span>
        <span v-else-if="operator == '/'"> {{divide}}</span>
        <span v-else-if="operator == '%'"> {{modulus}}</span>


    </h1>
    <span>
  
    </span>



    First number: <input v-model.number="numberone" type="number">
    Operator: <input v-model="operator"/>
    Second number: <input v-model.number="numbertwo" type="number">

    <div>
    <button v-on:click="makenumberone(0)">0</button>
    <button v-on:click="makenumberone(1)">1</button>
    <button v-on:click="makenumberone(2)">2</button>
    <button v-on:click="makenumberone(3)">3</button>
    <button v-on:click="makenumberone(4)">4</button>
    <button v-on:click="makenumberone(5)">5</button>
    <br>
    <button v-on:click="makenumberone(6)">6</button>
    <button v-on:click="makenumberone(7)">7</button>
    <button v-on:click="makenumberone(8)">8</button>
    <button v-on:click="makenumberone(9)">9</button>
    <button v-on:click="makenumberone(0)">0</button>
    <br>
    <button v-on:click="makeoperator('+')">+</button>
    <button v-on:click="makeoperator('-')">-</button>
    <button v-on:click="makeoperator('/')">/</button>
    <button v-on:click="makeoperator('*')">*</button>
    <button v-on:click="makeoperator('%')">modulus</button>



    <br>
    <button v-on:click="makenumbertwo(0)">0</button>
    <button v-on:click="makenumbertwo(1)">1</button>
    <button v-on:click="makenumbertwo(2)">2</button>
    <button v-on:click="makenumbertwo(3)">3</button>
    <button v-on:click="makenumbertwo(4)">4</button>
    <button v-on:click="makenumbertwo(5)">5</button>
    <br>
    <button v-on:click="makenumbertwo(6)">6</button>
    <button v-on:click="makenumbertwo(7)">7</button>
    <button v-on:click="makenumbertwo(8)">8</button>
    <button v-on:click="makenumbertwo(9)">9</button>
    <button v-on:click="makenumbertwo(0)">0</button>
    <button >C</button>



    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      numberone: null,
      numbertwo: null,
      operator: "",
      answer: 0,
      test: 100
      

    }
  },
  methods:{
    Add: function () {
      console.log("add");
      
    },
    makenumberone: function(thisnum) {
     this.numberone = thisnum;
    },
    makeoperator: function(thisoperator) {
      this.operator = thisoperator;
    },
    makenumbertwo: function(thisnum) {
     this.numbertwo = thisnum;
    }
    
    },
computed: {
      add: function () {
        return this.numberone + this.numbertwo;
      },

      minus: function () {
        return this.numberone - this.numbertwo;
      },

      multiply: function () {
        return this.numberone * this.numbertwo;
      },

      divide: function () {
        return this.numberone / this.numbertwo;
      },

      modulus: function () {
        return this.numberone % this.numbertwo;
      }



  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {font-size: 20px;}

</style>
