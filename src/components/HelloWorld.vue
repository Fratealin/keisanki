<template>
  <div class="hello">


    <h1>{{numberone}} {{operator}} {{numbertwo}} equals
        
        <span v-if="operator == '+' && numbertwo != ''" >{{add}}</span>
        <span v-else-if="operator == '-'"> {{minus}}</span>
        <span v-else-if="operator == '*'"> {{multiply}}</span>
        <span v-else-if="operator == '/'"> {{divide}}</span>
        <span v-else-if="operator == '%'"> {{modulus}}</span>


    </h1>
    <span>
  
    </span>
    

<input v-model="userinput" @keyup.enter="splitinput">
    <button v-on:click="splitinput()">calculate</button>
    <br>

    First number: <input v-model.number="numberone" type="number">
    Operator: <input v-model="operator"/>
    Second number: <input v-model.number="numbertwo" type="number">

    <div>
    <button v-on:click="makenumber(0)">{{nums[0]}}</button>
    <button v-on:click="makenumber(1)">{{nums[1]}}</button>
    <button v-on:click="makenumber(2)">{{nums[2]}}</button>
    <button v-on:click="makenumber(3)">{{nums[3]}}</button>
    <button v-on:click="makenumber(4)">{{nums[4]}}</button>
    <button v-on:click="makenumber(5)">{{nums[5]}}</button>
    <br>
    <button v-on:click="makenumber(6)">{{nums[6]}}</button>
    <button v-on:click="makenumber(7)">{{nums[7]}}</button>
    <button v-on:click="makenumber(8)">{{nums[8]}}</button>
    <button v-on:click="makenumber(9)">{{nums[9]}}</button>
    <button v-on:click="makenumber(0)">{{nums[0]}}</button>
    <br>
    <button v-on:click="makeoperator('+')">+</button>
    <button v-on:click="makeoperator('-')">-</button>
    <button v-on:click="makeoperator('/')">/</button>
    <button v-on:click="makeoperator('*')">*</button>
    <button v-on:click="makeoperator('%')">modulus</button>
    <br>
        <button v-on:click="clearscreen()">C</button>
    <br>
    <h2>backward calculator</h2>
    enter max: <input v-model="max" @keyup.enter="getquestion"/>
        <button v-on:click="getquestion()">go!</button>
        
<br>
Now try and make the answer below using the calculator above<br>(only works with + and *)
        <h2>{{question}}</h2>

    Input here: 
    <br>
        <button v-on:click="checkmultiply()">check multiplication</button>
        <button v-on:click="checkadd()">check add</button>{{iscorrect}}

        <br>

    
    <h1>words</h1>
    <br>
        Type list of words to practice: <input v-model="wordsinput" @keyup.enter="makewordlist"/>
        <button v-on:click="makewordlist()">go!</button>

    <h1>{{ selection }}</h1>
    <br>
    Type answer here:
    <input v-model="attempt" @keyup.enter="getword"/>
        <button v-on:click="getword()">next word</button>
<br>
<h2>{{checkinput}}</h2>





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
      userinput: "",




      numberone: "",
      numbertwo: "",
      operator: "",
      answer: 0,
            nums: ['零', '一', '二', '三', '四', '五', '六', '七', '八', '九', '十'],
      wordsinput: "",
      wordlist: ['ㄅ', 'ㄆ', 'ㄇ', 'ㄈ', 'ㄉ', 'ㄊ', 'ㄋ', 'ㄌ', 'ㄍ', 'ㄎ', 'ㄏ', 'ㄐ', 'ㄑ', 'ㄒ', 'ㄓ', 'ㄔ', 'ㄕ', 'ㄖ', 'ㄗ', 'ㄘ', 'ㄙ', 'ㄚ', 'ㄛ', 'ㄜ', 'ㄝ', 'ㄞ', 'ㄟ', 'ㄠ', 'ㄡ', 'ㄢ', 'ㄣ', 'ㄤ', 'ㄥ', 'ㄦ', 'ㄧ', 'ㄨ', 'ㄩ'],
      selection: "",
      attempt: "",
      max: "",
      question: null,
      iscorrect: "",
      test:"",
      op:"",
      teststring:""
    }
  },
  methods:{
    
    
    
    makenumber: function(thisnum) {
      if (thisnum != 0  || this.numberone != "" )
      {
        if (this.operator == "") {
     this.numberone = this.numberone + thisnum;
      }
      else{
        this.numbertwo = this.numbertwo + thisnum;
      }
      }
    },
    makeoperator: function(thisoperator) {
      this.operator = thisoperator;
    },
        splitinput: function() {
      
      if (this.userinput.includes("+")){
                    this.operator = "+";
      }
      else if (this.userinput.includes("-")){
                    this.operator = "-";
      }
      else if (this.userinput.includes("/")){
                    this.operator = "/";
      }
      else if (this.userinput.includes("*")){
                    this.operator = "*";
      }
      else if (this.userinput.includes("%")){
                    this.operator = "%";
      }
      else {
        this.userinput = "";
      }


            this.test = "checked";
            var splitstring = this.userinput.split(this.operator);
            this.numberone = splitstring[0];
            this.numbertwo = splitstring[1];
      
      

    },




    clearscreen: function() {
     this.numbertwo = "";
     this.numberone = "";
     this.operator = "";
     this.userinput = "";
    },
    getquestion: function() {
      
      this.question = Math.floor(Math.random() * (this.max-1)+2) * Math.floor(Math.random() * (this.max-1)+2)
    },
    checkmultiply: function() {
      if (this.multiply == this.question) {
      this.iscorrect = "yes";
      }
      else {
        this.iscorrect = "no";
      }
    },
    checkadd: function() {
      if (this.add == this.question) {
      this.iscorrect = "Bravo";
      }
      else {
        this.iscorrect = "Try again!";
      }

    },
    makewordlist: function() {
      this.wordlist = this.wordsinput.split(" ");
      this.wordsinput = ""
      this.selection = this.wordlist[Math.floor(Math.random() * this.wordlist.length)]

      
    },
    getword: function() {
      this.selection = this.wordlist[Math.floor(Math.random() * this.wordlist.length)];
      this.attempt = "";
    }
    },
computed: {
      add: function () {
        return parseInt(this.numberone) + parseInt(this.numbertwo);      },

      minus: function () {
        return parseInt(this.numberone) - parseInt(this.numbertwo);
      },

      multiply: function () {
        return parseInt(this.numberone) * parseInt(this.numbertwo);
      },

      divide: function () {
        return parseInt(this.numberone) / parseInt(this.numbertwo);
      },

      modulus: function () {
        return parseInt(this.numberone) % parseInt(this.numbertwo);
      },
      
      checkinput: function () {
        if (this.attempt == this.selection) {

        return "Bravo!";
        }
        else{
          return "Keep trying!";
        }
        
      }




  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {font-size: 20px;}

</style>
