<template>
    <div class="container" ref="container">
      <!-- 默认登陆页 -->
      <div class="panels-container">
        <div class="panel left-panel">
          <div class="panel-content">
            <h3>没有账号 ?</h3>
            <p>在每个人的心里，都有一个人记不住，却不能拥抱和珍惜。</p>
            <button class="panel-btn" @click="toSignUp">前往注册</button>
          </div>
          <img class="panel-img" src="@/assets/imgs/log.png" alt="" />
        </div>
        <div class="panel right-panel">
          <div class="panel-content">
            <h3>已有账号 ?</h3>
            <p>在每个人的心里，都有一个人记不住，却不能拥抱和珍惜。</p>
            <button class="panel-btn" @click="toSignIn">前往登录</button>
          </div>
          <img class="panel-img" src="@/assets/imgs/register.png" alt="" />
        </div>
      </div>
      
      <div class="forms-container">
        <div class="sign-in-up">
            <!-- 登录 -->
            <LoginForm :isLogin="true"/>
            <!-- 注册 -->
            <RegisterForm />
        </div>
      </div>
    </div>
  </template>
  
<script lang="ts" setup>
import { ref } from 'vue'
//坑点: Module LoginForm.vue has no default export 考虑到是Vetur插件的问题, 升级插件
import LoginForm from './LoginForm.vue' 
import RegisterForm from './RegisterForm.vue'

const container = <any>ref(null);

/* 前往注册 */
const toSignUp = () =>{
    container.value.classList.add('sign-up-mode');
}
/* 前往登录 */
const toSignIn = () =>{
    container.value.classList.remove('sign-up-mode')
}
</script>
  
<style lang="less" scoped>
.container {
    position: relative;
    width: 100%;
    min-height: 100vh;
    font-size: 14px;
    font-family: sans-serif;
    background-color: #fff;
    overflow: hidden;
}
  
.container::before {
    content: '';
    position: absolute;
    top: -10%;
    right: 48%;
    transform: translateY(-50%);
    transition: 1.8s ease-in-out;
    width: 2000px;
    height: 2000px;
    background-image: linear-gradient(-45deg, #8a6eff 0%, #ad99fe 100%);
    border-radius: 50%;
    z-index: 3;
}
  
.panels-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
}
  
.panel {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: flex-end;
    text-align: center;
    z-index: 9;
    .panel-content {
        color: #fff;
        transition: transform 0.9s ease-in-out;
        transition-delay: 0.6s;
  
        h3 {
            font-size: 22px;
            font-weight: 600;
            line-height: 1;
        }
    
        p {
            padding: 10px 0;
        }
        .panel-btn {
            width: 130px;
            height: 41px;
            outline: none;
            border: 2px solid #fff;
            border-radius: 49px;
            background: none;
            color: #fff;
            font-weight: 600;
            text-transform: uppercase;
            cursor: pointer;
            transition: 0.5s;
        }
    }
    .panel-img {
        width: 100%;
        transition: transform 1.1s ease-in-out;
        transition-delay: 0.4s;
    }
}
  
.left-panel {
    pointer-events: all;
    padding: 42px 17% 28px 12%;
}
  
.right-panel {
    pointer-events: none;
    padding: 42px 12% 28px 17%;
  
    .panel-content,
    .panel-img {
      transform: translateX(800px);
    }
}
  
.container.sign-up-mode::before {
    right: 52%;
    transform: translate(100%, -50%);
  }
  
.container.sign-up-mode {
.left-panel {
      pointer-events: none;
    .panel-content,
    .panel-img {
        transform: translateX(-800px);
      }
    }
  
.right-panel {
      pointer-events: all;
    .panel-content,
    .panel-img {
        transform: translateX(0);
      }
    }
  
.sign-in-up {
      left: 25%;
    }
  
.sign-up-form {
      z-index: 2;
      opacity: 1;
    }
  
.sign-in-form {
      z-index: 1;
      opacity: 0;
    }
}
  
.forms-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
  
.sign-in-up {
    position: absolute;
    top: 50%;
    left: 75%;
    transform: translate(-50%, -50%);
    transition: 1s 0.7s ease-in-out;
    width: 50%;
    display: grid;
    grid-template-columns: 1fr;
}
  
.sign-in-form,
.sign-up-form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    grid-column: 1 / span 1;
    grid-row: 1 / span 1;
    transition: all 0.2s 0.7s;
}
  
.sign-up-form {
    z-index: 1;
    opacity: 0;
}
  
.sign-in-form {
    z-index: 2;
}
  
.form-title {
    font-size: 30px;
    color: #444;
    margin-bottom: 20px;
}
  
.form-input {
    width: 100%;
    max-width: 380px;
    height: 55px;
    line-height: 55px;
    border-radius: 55px;
    display: grid;
    grid-template-columns: 15% 85%;
    padding: 0 6px;
    background-color: #f0f0f0;
    margin: 10px 0;
  
    i {
      display: flex;
      justify-content: center;
      align-items: center;
      transition: 0.5s;
    }
  
    input {
      outline: none;
      border: none;
      background: none;
      font-size: 16px;
      font-weight: 600;
      color: #333;
      line-height: 1;
    }
  
    input::placeholder {
      color: #aaa;
      font-weight: 500;
    }
}
.form_item{
    width: 100%;
    max-width: 380px;
    .form_input{
    width: 100%;
    max-width: 380px;
    height: 55px;
    line-height: 55px;
    margin: 10px 0;
}
}

  
.form-btn {
    width: 150px;
    height: 49px;
    margin: 20px 0;
    outline: none;
    border: none;
    border-radius: 49px;
    color: #fff;
    font-weight: 600;
    text-transform: uppercase;
    background-color: #8a6eff;
    cursor: pointer;
  }
  
.form-btn:hover {
    background-color: #6c48ff;
}
  
.social-text {
    padding: 10px 0;
}
  
.social-media {
    display: flex;
    justify-content: center;
}
  
.social-link {
    margin: 0 4px;
    color: #333;
    text-decoration: none;
    transition: 0.3s;
}
  
.social-link:hover {
    color: #6c48ff;
}
  
.social-icon {
    fill: currentColor;
}
  
@media screen and(max-width:870px) {
.container {
      min-height: 760px;
      height: 100vh;
    }
  
.container::before {
      left: 30%;
      bottom: 68%;
      top: initial;
      right: initial;
      transform: translateX(-50%);
      transition: 2s ease-in-out;
      width: 1500px;
      height: 1500px;
    }
  
.panels-container {
      grid-template-columns: 1fr;
      grid-template-rows: 1fr 2fr 1fr;
    }
  
.panel {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
      grid-column: 1 / span 1;
      padding: 35px 8%;
  
    .panel-content {
        padding-right: 15%;
        transition: transform 0.9s ease-in-out;
        transition-delay: 0.8s;
  
        h3 {
          font-size: 18px;
        }
  
        p {
          font-size: 12px;
          padding: 8px 0;
        }
  
    .panel-btn {
          width: 110px;
          height: 35px;
          font-size: 12px;
        }
      }
  
    .panel-img {
        width: 200px;
        transition: transform 0.9s ease-in-out;
        transition-delay: 0.6s;
      }
    }
  
.left-panel {
      grid-row: 1 / span 1;
    }
  
.right-panel {
      grid-row: 3 / span 1;
  
    .panel-content,
    .panel-img {
        transform: translateY(300px);
      }
    }
  
.container.sign-up-mode::before {
      right: initial;
      bottom: 32%;
      transform: translate(-50%, 100%);
    }
  
.container.sign-up-mode {
    .left-panel {
    .panel-content,
    .panel-img {
          transform: translateY(-300px);
        }
      }
  
    .right-panel {
    .panel-content,
    .panel-img {
          transform: translateY(0);
        }
      }
  
    .sign-in-up {
        top: 5%;
        left: 50%;
        transform: translate(-50%, 0);
      }
    }
  
    .sign-in-up {
        top: 95%;
        left: 50%;
        transform: translate(-50%, -100%);
        transition: 1s 0.8s ease-in-out;
        width: 100%;
    }
}
  
@media screen and(max-width:570px) {
.container {
      padding: 20px;
    }
  
.container::before {
      left: 50%;
      bottom: 72%;
    }
  
.panel {
    .panel-content {
        padding: 8px 14px;
      }
  
    .panel-img {
        display: none;
      }
    }
  
.container.sign-up-mode::before {
      left: 50%;
      bottom: 28%;
    }
  
.sign-in-form,
.sign-up-form {
      padding: 0 22px;
    }
}
</style>
