<template>
  <div id="app">
    <div>123456</div>
    <input type="button" @click = "click" value="点击">
    <input type="button" @click = "click2" value="点击出现遮罩层">
    <ul ref="ul">
      <li ref = "a" v-for = "(val,key) in arr" :key="key">{{val}}</li>
    </ul>
    <input 
      type="text"
      ref = "txt"
      v-show = "val"
     >
    <Child /> 
    <Hello  
           :onOff="o"
            @changeO = "click"
    >
      <p> slot="welcome"请点击下面图标进入下一步</p>    
  </Hello>  
  </div>
</template>
<script>
/*
slot: 插槽 目的，有配置，走配置，没配置走默认；

引入子组件，如果不定义某个默认样式的结构或者样式，

如果要定义：1、子组件必须为双标签；
           2、子组件内写上自定义的结构或者样式并加上slot属性，而这个属性名要顶用默认slot的名字；
           3、在子组件中，包一个slot对象，可以任意修改，在slot元素上定义一个叫做name的属性，为了好对应操作
*/


import Child from "./components/child"
import Hello from "./components/slot"
export default {
  components: {
    Child,
    Hello
  },
  data(){
    return {
      arr:[1,2,3,4,5,6],
      val:'',
      o:false
    }
  },
  mounted(){
    let lis = document.getElementsByTagName('li');
    for(let el of lis){
      el.onclick = function(){
        alert(1)
      }
    }
    // this.$hrefs.txt.focus;
  },
  methods:{
    click(){
      console.log(this.$refs.txt);
      this.val = '1234';
      this.$nextTick(()=>{
        this.$refs.txt.focus();
      });
    },
    click2(){
       this.o = !this.o
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
