<script setup>
import { ref,reactive, onMounted } from "vue";
import axios from 'axios'

const api = axios.create({
    headers:{
        'Content-Type':'application/json',
    },
    timeout:10000
})

const typeWriterRef = ref()

const data = reactive({
    bannerContent:'',
    oneSentence:''
})

let index = 0;
let content = 'Hi, I\'m CairBin ~'.split('')
const typeWriterFunc = ()=>{
    if(index<content.length){
        data.bannerContent += content[index++]
        setTimeout(typeWriterFunc,200)
    }
}

/*
{
  "code": 200,
  "data": {
    "id": 76,
    "tag": "生活",
    "name": "佚名",
    "origin": "木芽",
    "content": "有些东西可以留下，例如服务器操作日志，数据库操作日志。有些东西转身就删了，例如聊天记录，每天清除一切软件的聊天记录，是我每天乐于干的一件事，留着过夜的记录是我一天的失败",
    "created_at": "2018-12-18T05:40:51.000Z",
    "updated_at": "2022-03-09T08:42:10.000Z"
  },
  "updateTime": 1683818603408
}

*/
const getSentence = ()=>{
    api.get('https://api.xygeng.cn/openapi/one#').then((response)=>{
        data.oneSentence = `「 ${response.data.data.content} 」— ${response.data.data.name} ${response.data.data.origin}`
    }).catch((err)=>{
        console.error(err)
        data.oneSentence = '「 API Request Error 」'
    })
        
}

const main = ()=>{
    typeWriterFunc();
    getSentence()
    setInterval(getSentence, 10000);
}

main()


</script>

<template>
    <el-header></el-header>
    <div class="common-main main">
        <div ref="typewriter" class="common-box common-box0 box box0" id="content">
            <img id="my-avatar" src="./../assets/avatar.jpeg" class="my-avatar"/>&nbsp;{{ data.bannerContent }}
        </div>
        <div class="common-box box box1">
            <a href="https://cairbin.top">
                <i class="fa-solid fa-blog"></i>
            </a>
        </div>
        <div class="common-box box box2">
            <a href="https://github.com/CairBin">
                <i class="fa-brands fa-github"></i>
            </a>
        </div>
        <div class="common-box box box3">
            <a href="https://blog.csdn.net/qq_42759112?spm=1000.2115.3001.5343">
                <i class="fa-solid fa-c"></i>
            </a>
        </div>
        <div class="common-box box box4">
            <a href="https://t.me/CairBin">
                <i class="fa-brands fa-telegram"></i>
            </a>
            
        </div>
        <div class="common-box box box5">
            <a href="https://cairbin.top/index.php/time.html">
                <i class="fa-solid fa-envelope"></i>
            </a>
        </div>
        <div class="common-box box box6">
            <a href="https://cairbin.github.io/LearnSSM/">
                <i class="fa-brands fa-java"></i>
            </a>
        </div>
        <div class="common-box box box7">
            <a href="https://travellings.link/">
                <i class="fa-solid fa-train"></i>
            </a>
        </div>

        <div class="page-info">
            <div class="info-item">{{data.oneSentence}}</div>
            <div>&nbsp;</div>
            <div class="info-item">&copy;&nbsp;Copyright 2024-Now CairBin</div>
            <div class="info-item">Powered By Github Page</div>
        </div>
    </div>
</template>

<style scoped>

.page-info{
    background: #2f3542;
    grid-column: 1/4;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    color:white;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    flex-direction: column;
}


.common-box{
    text-align: center;
    color:#dfe4ea;
    border: 5px solid rgba(164,176,190,0);
}


.common-box0{
    grid-column: 1/4;
    grid-row: 1/2;
    background: #2f3542;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.box0 img{
    width:80px;
}


.common-main{
    position: absolute;
    left:50%;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(5,1fr);
    grid-gap: 10px;
    transform: translate(-50%,-50%);
    display: grid;
}

@media screen and (min-width:960px){
    .box{
        font-size:100px;
        line-height: 200px;
    }

    .box0{
        font-size:70px;
    }

    #my-avatar{
        width:80px;
    }

    .main{
        width:600px;
        height: 200px;
        margin-top:60px;
    }
}

@media screen and (max-width:960px){
    .box{
        font-size:100px;
        line-height: 190px;
    }

    #my-avatar{
        width:90px;
    }

    .box0{
        font-size: 60px;
    }

    .main{
        height:3rem;
        width:555px;
    }
}

@media screen and (max-width:560px){
    .box{
        font-size:90px;
        line-height: 120px;
    }

    .box0{
        font-size: 35px;
    }

    .main{
        height:50px;
        width:345px;
    }
}

@media screen and (max-width:350px){
    .box{
        font-size:80px;
        line-height: 90px;
    }

    .box0{
        font-size: 30px;
    }

    #my-avatar{
        width:50px;
    }

    .main{
        height:100px;
        width:290px;
    }
}



.box:hover{
    border:5px solid rgba(241,242,246,0.5);
    transition: 0.3 linear;
    cursor: pointer;
}

.box hover::after{
    content:'关于'
}

.box a{
    text-decoration: none;
    color:inherit;
    font:inherit;
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


.my-avatar{
    border-radius: 50%;
    animation: light 4s ease-in-out infinite;
    transition: 0.5s;
}

/*头像呼吸灯动画*/
@keyframes light {
    0%{box-shadow: 0 0 8px #f00;}
    25%{box-shadow: 0 0 24px #0f0;} 
    50%{box-shadow: 0 0 8px #00f;}
    75%{box-shadow: 0 0 24px #0f0;} 
    100%{box-shadow: 0 0 8px #f00;}
}

/*头像旋转*/
.my-avatar:hover {
    transform: rotate(720deg);
}
</style>