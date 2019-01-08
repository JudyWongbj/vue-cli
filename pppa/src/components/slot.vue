<template>
    <div id="s"  v-show= "onOff">
        <div class="box"  @click = "change">        
        <slot name="welcome">   
        <h1 >欢迎光临！！！~~~</h1>
        </slot>
        </div>
        <div class="shadow"></div>
    </div>
</template>

<script>
export default {
    data(){
        return {

        }
    },
    props:{
        onOff:{
            default:false
        }
    },
    methods:{
        change(){
            this.$emit('changeO')
        }

    }
    
}
</script>
<style>
*{
    padding:0;
    margin:0;
}
#s .shadow{
    position:absolute;
    top:0;
    left:0;
    height:100vh;
    width:100vw;
    background:rgba(225,225, 252, .5);
}
#s .box{
    height:100px;
    width:200px;
    position:absolute;
    top:50%;
    left:50%;
    margin-left:-100px;
    margin-top:-50px;
    background: #fff;
    border: 1px solid #000;
    z-index:2;

}
#s .box h1,#s .box p{
    text-align: center;
    line-height:100px;
}
</style>


