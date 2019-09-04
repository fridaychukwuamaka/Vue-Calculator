<template>
  <div id="app">
    <div class="display">
      <input v-show="isEqual" type="number" class="write"  :value="submitVal" >
      <input v-show="!isEqual" autofocus class="write" type="text" @keyup="changeVal()"   v-model="writeVal" />
      <input v-show="!isEqual" :style="myStyle" type="number" class="read"  v-model="readVal" readonly  />
    </div>
    <div class="buttons">
      <div class="num-btn">
        <div class="btn-inner">
          <div class="col">
            <input value="7" type="submit" @click="num('7')"  >
            <input type="submit" value="8"  @click="num('8')" >
            <input type="submit" value="9"  @click="num('9')" >
          </div>
          <div class="col">
            <input value="4" type="submit" @click="num('4')"  >
            <input type="submit" value="5" @click="num('5')" >
            <input type="submit" value="6" @click="num('6')" >
          </div>
          <div class="col">
            <input value="1" type="submit" @click="num('1')"  >
            <input type="submit" value="2" @click="num('2')" >
            <input type="submit" value="3" @click="num('3')" >
          </div>
          <div class="col">
            <input value="0" type="submit" @click="num('0')"  >
            <input type="submit" value="." @click="num('.')" >
            <input type="submit" value="=" @click="equal"  >
          </div>
        </div>
      </div>
      <div class="op-btn">
        <div class="op-inner">
          <input type="submit" value="<" @click="num('<')"  >
          <input type="submit" value="/" @click="num('/')">
          <input type="submit" value="*" @click="num('*')">
          <input type="submit" value="-" @click="num('-')">
          <input type="submit" value="+" @click="num('+')">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data: () => {
    return {
      writeVal: '',
      readVal: 0,
      submitVal: 0,
      isEqual: false,
      myStyle: ''
    };
  },
  methods: {
    changeVal(){
      this.readVal = eval(this.writeVal)
      this.submitVal = eval(this.writeVal)
    },
    num(val){
      console.log(val);
      
      if(val === "+" || val === "-" || val === "/" || val === "*"){
      this.writeVal+=val
      this.readVal = eval(this.writeVal);
      this.isEqual = false;
      this.submitVal = eval(this.writeVal)
      }
      else{
      this.writeVal+=val
      this.readVal = eval(this.writeVal);
      this.submitVal = this.readVal;
       this.myStyle = ''
      this.isEqual = false;

    }

      
       /* this.writeVal = this.readVal */
    },
    equal(){
      this.isEqual = true;
      this.myStyle = `
       margin-top: 57px;
      font-size: 52px;
      color: black; 
      `
    }
  }
};
</script>

<style>

.btn-inner {
  display: flex;
  flex-direction: column;
  flex-basis: 100%;
  justify-content: space-between;
  height: 360px;
}
.num-btn {
  display: flex;
  width: 75%;
  height: 65vh;
  align-items: center;
  justify-content: space-evenly;
}
.op-btn {
  display: flex;
  align-items: center;
  width: 25%;
  justify-content: flex-end;
}

.buttons {
  display: flex;
  flex-direction: row;
  height: 65vh;
  margin: 0 32px;
}
.col {
  display: flex;
  justify-content: space-between;
}

.col input {
  width: 52px;
  height: 52px;
  border-radius: 40px;
  border: none;
  background: white;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
.op-inner {
  display: flex;
  flex-direction: column;
  height: 360px;
  justify-content: space-between;
}
.button{
  font-size: 20px;
}
.op-inner input {
  width: 48.47px;

  height: 48.47px;
  border-radius: 40px;
  border: none;
  color: white;
  background: #2680eb;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}

.display {
  padding: 0 23px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 35vh;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
input.write {
  height: 69px;
  text-align: right;
  width: 100%;
  font-size: 52px;
  font-weight: 500;
  border: none;
  margin: 52px 0 32px 0;
}
input.read {
  width: 100%;
  height: 48px;
  border: none;
  font-size: 36px;
  font-weight: 500;
  color: #4d4b4b;
  text-align: right;
  margin-bottom: 35.8px;
}
* {
  outline: none;
}
</style>
