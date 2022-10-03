<template>
  <div class="main-div">
    <p class="title">Password generator</p>
    <header>
      <div class="wrapper-password">
        <p class="password">{{resPass}}</p>
        <img src="./styles/copy.svg" alt="" v-on:click='copy'>
      </div>
    </header>
      
      <div class="wrapper"> 
        <div class="pass-len">
          <p class="len">Password length:</p>
          <p class="len-value">{{value}}</p>
        </div>
      <input v-model='value' type="range" class="form-range" id="customRange1" min="1" max="20">
          <div class="checkbox">
            <input type="checkbox" id="uppercase" class='check-box' value="uppercase" v-model="checkedUppercase"> 
              <label for="uppercase">Include Uppercase Letters</label>
          </div>
          <div class="checkbox">
            <input type="checkbox" id="lowercase" value="lowercase" v-model="checkedLowercase"> 
              <label for="lowercase">Include Lowercase Letters</label>
          </div>
          <div class="checkbox">
            <input type="checkbox" id="numbers" value="numbers" v-model="checkedNumbers"> 
              <label for="numbers">Include Numbers</label>
          </div>
          <div class="checkbox">
            <input type="checkbox" id="symbols" value="symbols" v-model="checkedSymbols"> 
              <label for="symbols">Include Symbols</label>
          </div>
          <div v-on:click='generatePassword' class="button-generate">
            <p>GENERATE</p>
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-right-short" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M4 8a.5.5 0 0 1 .5-.5h5.793L8.146 5.354a.5.5 0 1 1 .708-.708l3 3a.5.5 0 0 1 0 .708l-3 3a.5.5 0 0 1-.708-.708L10.293 8.5H4.5A.5.5 0 0 1 4 8z"/>
            </svg>
          </div>
      </div>
    </div>
    


</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    generatePassword() {
      let resArr = [];
      if (this.checkedLowercase) {
        resArr = resArr.concat(this.lowercase);
      }
      if (this.checkedUppercase) {
        resArr = resArr.concat(this.uppercase);
      }
      if (this.checkedNumbers) {
        resArr = resArr.concat(this.numbers);
      }
      if (this.checkedSymbols) {
        resArr = resArr.concat(this.symbols);
      }
      this.resPass = '';
      for (let i  = 0; i < this.value; i++) {
        this.resPass += resArr[Math.floor(Math.random()*resArr.length)];
      }
      console.log(this.resPass)
    },
    copy() {
      navigator.clipboard.writeText(this.resPass)
    }
  },
  data() {
    return {
      lowercase: ['q', 'w', 'e', 'r', 't', 'y', 'u', 'i', 'o', 'p', 
        'a','s', 'd', 'f', 'g', 'h', 'j', 'k', 'l', 'z', 'x', 'c', 'v', 'b', 'n', 'm'],
      uppercase: ['Q', 'W', 'E', 'R', 'T', 'Y', 'U', 'I', 'O', 'P', 
        'A','S', 'D', 'F', 'G', 'H', 'J', 'K', 'L', 'Z', 'X', 'C', 'V', 'B', 'N', 'M'],
      numbers: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'],
      symbols: ['!', '@', '#', '$', '%', '&', '*'],
      value: '8',
      checkedUppercase: false,
      checkedLowercase: true,
      checkedNumbers: true,
      checkedSymbols: false,
      resPass: ''

    }
  }
}
</script>

<style scoped>
  .pass-len {
    display: flex;
  }
  
  .len-value {
    color:#bafcb5;
    margin-left: 55%;
    margin-top: 10px;
  }

  .len {
    margin-left: 23px;
    margin-top: 15px;
    font-size: 15px;
  }

  header {
    margin: 20px;
  }
  .form-range {
    width: 84%;
    margin-top: 6px;
    margin-bottom: 20px;
    border-radius: 0;
  }

  .title {
    color: #61606b;
  }

  .wrapper-password {
    background: #24232a;
    color: white;
    height: 45px;
    width: 400px;
    margin: 0 auto;
    display: flex;
  }

  .password {
    font-size: 30px;
    margin-left: 10px;
  }

  .wrapper {
    background: #24232a;
    width: 400px;
    height: 342px;
    margin: 0 auto;
    color: white;
    font-size: 20px;
  }

  .button-generate {
    background: #bafcb5;
    width: 370px;
    margin: 0 auto;
    height: 45px;
    color: black;
    border-radius: 2px;
    margin-top: 30px;
    padding-top: 13px;
    font-size: 13px;
    display: flex;
    padding-left: 136px;

  }
  .checkbox {
    margin-bottom: 8px;
  }

  label {
    padding-left: 10px;
  }

  .checkbox {
    margin-left: -80px;
  }

  #lowercase {
    margin-left: -2px;
  }

  #numbers {
    margin-left: -79px;
  }

  #symbols {
    margin-left: -85px;
  }

  img {
    position: fixed;
    margin-left: 365px;
    margin-top: 7px;
    width: 30px;
  }

  img:hover {
    cursor: pointer;
  }
</style>
