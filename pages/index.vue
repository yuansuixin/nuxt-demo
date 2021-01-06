<template>
  <div class="container">
    <div>
      <p>邮箱：<input type="text" v-model="username" /></p>
      <p>密码：<input type="text" v-model="password" /></p>
      <p>图片验证：<input type="text" v-model="code" /></p>
      <p>sid：<input type="text" v-model="sid" /></p>
      <button type="button" @click="login()">登陆</button>
    </div>
  </div>
</template>

<script>
// import ErrorHandle from '~/plugins/axios'
export default {
  data() {
    return {
      username: '',
      password: '',
      code: '',
      sid: '',
    }
  },
  methods: {
    login() {
      this.$auth.loginWith('local', {
        data: {
          username: this.username,
          password: this.password,
          code: this.code,
          sid: this.sid,
        },
      })
    },
  },
  // asyncData({ $axios, redirect }) {
  //   ErrorHandle($axios, redirect)
  // },

  // async asyncData({ $axios }) {
  //   // $get返回的直接是result.data
  //   // 使用get返回的带有headers，status等信息
  //   const result = await $axios.get('http://localhost:8000/posts')
  //   return {
  //     posts: result.data,
  //   }
  // },
  // asyncData: ({ req }) => {
  //   return {
  //     userAgent: req
  //       ? req.headers['user-agent']
  //       : typeof navigator !== 'undefined'
  //       ? navigator.userAgent
  //       : 'No user agent ',
  //   }
  // },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
