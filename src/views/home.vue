<script setup>
import { ref,reactive, onMounted } from "vue";

const typeWriterRef = ref()

const data = reactive({
    bannerContent:''
})

let index = 0;
let content = 'Hi, I\'m CairBin ~'.split('')
const typeWriterFunc = ()=>{
    if(index<content.length){
        data.bannerContent += content[index++]
        setTimeout(typeWriterFunc,200)
    }
}

const main = ()=>{
    typeWriterFunc();
}

main()


</script>

<template>
    <div class="main">
        <div ref="typewriter" class="box box0" id="content">
            &nbsp;{{ data.bannerContent }}
        </div>
        <div class="box box1">
            <a href="https://cairbin.top">
                <i class="fa-solid fa-blog"></i>
            </a>
        </div>
        <div class="box box2">
            <a href="https://github.com/CairBin">
                <i class="fa-brands fa-github"></i>
            </a>
        </div>
        <div class="box box3">
            <a href="https://blog.csdn.net/qq_42759112?spm=1000.2115.3001.5343">
                <i class="fa-solid fa-c"></i>
            </a>
        </div>
        <div class="box box4">
            <a href="https://t.me/CairBin">
                <i class="fa-brands fa-telegram"></i>
            </a>
            
        </div>
        <div class="box box5">
            <a href="https://cairbin.top/index.php/time.html">
                <i class="fa-solid fa-envelope"></i>
            </a>
        </div>
        <div class="box box6">
            <a href="https://cairbin.github.io/LearnSSM/">
                <i class="fa-brands fa-java"></i>
            </a>
        </div>
        <div class="box box7">
            <a href="https://travellings.link/">
                <i class="fa-solid fa-train"></i>
            </a>
        </div>
    </div>
</template>

<style scoped>
.box{
    color:#dfe4ea;
    font-size:100px;
    text-align: center;
    line-height: 200px;
    border: 5px solid rgba(164,176,190,0);
}

.box:hover{
    border:5px solid rgba(241,242,246,0.5);
    transition: 0.3 linear;
    cursor: pointer;
}

.main{
    position: absolute;
    left:50%;
    margin-top:150px;
    height:153px;
    width:560px;
    display: grid;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(5,1fr);
    grid-gap: 10px;
    transform: translate(-50%,-50%);
}

.box a{
    text-decoration: none;
    color:inherit;
    font:inherit;
}

.box0{
    background: wheat;
    grid-column: 1/4;
    grid-row: 1/2;
    font-size: 50px;
    background: #2f3542;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.box1{
    grid-column: 1/2;
    grid-row:2/3;
    background-color: #f1c40f;
}


.box2{
    grid-column: 2/4;
    grid-row: 2/3;
    background-color: #2c3e50;
}

.box3{
    grid-column: 1/1;
    grid-row: 3/4;
    background-color: #d35400;
}

.box4{
    grid-column: 2/3;
    grid-row:3/4;
    background: #70a1ff
}

.box5{
    grid-column: 3/4;
    grid-row:3/4;
    background: #3498db;
}

.box6{
    grid-column: 1/3;
    grid-row: 4/5;
    background-color: #2ecc71;
}

.box7{
    grid-column: 3/4;
    grid-row:4/5;
    background-color: #8e44ad;
}

 /* 设置容器样式 */
#content {

}
  /* 产生光标闪烁的效果 */
  #content::after{
      content: '|';
      color:darkgray;
      animation: blink 1s infinite;
  }
  @keyframes blink{
      from{
          opacity: 0;
      }
      to{
          opacity: 1;
      }
  }
</style>