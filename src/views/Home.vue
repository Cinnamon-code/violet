<template>
  <div class="home">
    <el-row>
      <el-col :span="24">
        <div class="intro" :style="publicStyle">
          <h1>姐妹齐心，其利断金</h1>
          <span><i>dedicate</i></span>
          <!--          <el-divider>dedicate</el-divider>-->
          <div class="names">
            <el-row>
              <el-col :xl="12" :lg="12" :sm="12" :xs="24">
                <span>沈聪</span><span>贾正一</span>
              </el-col>
              <el-col :xl="12" :lg="12" :sm="12" :xs="24">
                <span>宋海沛</span><span>杨铮</span>
              </el-col>
            </el-row>
          </div>
        </div>
      </el-col>
    </el-row>
    <el-row>
      <div class="flag">我们的故事从未停止……</div>
    </el-row>
    <el-container class="main">
      <el-main>
        <el-row :gutter="20">
          <el-col :xl="6" :lg="6" :sm="10" :xs="24">
            <el-card :style="publicStyle">
              <template v-slot:header>登录</template>
              <el-form :model="model" :rules="rules" class="form" ref="form">
                <el-form-item label="用户名" prop="username">
                  <el-input v-model="model.username" placeholder="请输入用户名">
                    <template v-slot:prefix>
                      <i class="el-icon-user"></i>
                    </template>
                  </el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                  <el-input v-model="model.password" type="password" placeholder="请输入密码">
                    <template v-slot:prefix>
                      <i class="el-icon-key"></i>
                    </template>
                  </el-input>
                </el-form-item>
                <s-button class="login-btn" @click="login">登录</s-button>
              </el-form>
            </el-card>
          </el-col>
          <el-col :xl="18" :lg="18" :sm="14" :xs="24">
            <el-card :body-style="{padding: 0}">
              <el-carousel autoplay
                           loop
                           indicator-position="none"
                           :interval="2000"
                           :height="publicStyle.height"
                           class="carousel">
                <el-carousel-item>
                  <img src="../assets/1.png">
                </el-carousel-item>
                <el-carousel-item>
                  <img src="../assets/2.jpg">
                </el-carousel-item>
                <el-carousel-item>
                  <img src="../assets/3.jpg">
                </el-carousel-item>
              </el-carousel>
            </el-card>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script>
import SButton from '@/components/SButton'

export default {
  name: 'Home',
  data() {
    return {
      publicStyle: {
        height: '400px'
      },
      model: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          {required: true, message: '用户名不可为空', trigger: 'blur'}
        ],
        password: [
          {required: true, message: '密码不可为空', trigger: 'blur'},
          {min: 4, max: 18, message: '密码长度应在4-18之间', trigger: 'change'}
        ]
      }
    }
  },
  methods: {
    login() {
      this.$refs.form.validate(valid => {
        if (valid) this.$message({
          type: 'success',
          message: '登录成功'
        })
        else this.$message({
          type: 'error',
          message: '登录失败'
        })
      })
    }
  },
  components: {SButton}
}
</script>

<style>
.el-col {
  margin-bottom: 20px;
}

img {
  height: 100%;
  /*width: 100%;*/
}

.carousel {
  text-align: center;
}

.intro {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column wrap;
  padding: 0 30px;
  background-color: #fff;
  font-size: 20px;
}

.intro h1 {
  font-size: 60px;
}

.names {
  margin-top: 30px;
}

.names  span {
  margin: 0 20px;
}

.names .el-col {
  text-align: center;
}


.flag {
  padding: 15px 0;
  background-color: #42b983;
  box-shadow: 0 2px 4px 0 #bcbcbc;
  text-align: center;
  color: #fff;
}

.form {
  display: flex;
  flex-flow: column wrap;
  justify-content: center;
  /*padding: 0 20px;*/
}

.el-input__inner:focus {
  border-color: #42b983;
}

.login-btn {
  margin-top: 20px;
}
</style>
