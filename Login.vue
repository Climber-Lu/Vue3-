<template>
  <div class="LoginForm">
    <div class="Info">
      <el-icon :size="40">
        <lock />
      </el-icon>
      <span>登录</span>
    </div>
    <div class="Content">
      <label for="username">用户名</label>
      <el-input type="text" id="username" v-model="LoginForm.username" placeholder="请输入用户名" />
      <label for="password">密码</label>
      <el-input type="password" id="password" v-model="LoginForm.password" placeholder="请输入密码" show-password />

      <div class="loginButton">
        <el-button type="primary" style="width: 100%;" @click="login">登录</el-button>
      </div>
      <div class="ano">
        <div class="register">
          <span>还没有账号?<router-link to="/register" style="text-decoration: none;">注册</router-link></span>
        </div>
        <div div class="forget">
          <span><a href="#" style="text-decoration: none;color: black;">忘记密码</a></span>
        </div>
      </div>
    </div>
    <div class="divider">
      <el-divider content-position="center">其他登录方式</el-divider>
    </div>
  </div>
</template>

<script>
import router from '@/router';
import { ElMessage } from 'element-plus';
export default {
  data() {
    return {
      // 登录表单数据
      LoginForm: {
        username: 'admin',
        password: '123456'
      }
    }
  },
  methods: {
    // 处理登录
    login() {
      if (this.LoginForm.username === 'admin' && this.LoginForm.password === '123456') {
        router.push('/home')
        ElMessage({
          type: 'success',
          message: '登录成功',
          duration: 1000
        }
        )
      }
    }
  }
}

</script>

<style>
body {
  background-image: url('../../assets/login.png');
  background-repeat: no-repeat;
  background-size: cover;
}

.LoginForm {
  width: 420px;
  height: 600px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 20px;
  border: 2px solid black;
  box-shadow: 10px 10px 10px #d1d9e6, -10px -10px 10px #f9f9f9;
  background-color: rgb(255, 255, 255);
}

.Info {
  margin-left: 45%;
  margin-top: 10%;
  display: flex;
  flex-direction: column;
}

.Info span {
  font-size: 30px;
  color: black;
  margin-top: 20px;
  margin-left: -10px;
}

.Content {
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  width: 330px;
  margin-left: 35px;
  row-gap: 10px;
}

.Content label {
  font-size: larger;
  color: black;
}

.Content el-input {
  width: 90%;
}

.loginButton {
  margin-top: 20px;
}

.ano {
  display: flex;
  gap: 140px;
  margin-top: 20px;
}
</style>