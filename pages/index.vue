<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">nuxt-demo</h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
      <!-- user agent is :{{ userAgent }} -->
      <br />
      <br />
      posts:{{ posts }}
    </div>
  </div>
</template>

<script>
// import ErrorHandle from '~/plugins/axios'
export default {
  // asyncData({ $axios, redirect }) {
  //   ErrorHandle($axios, redirect)
  // },

  async asyncData({ $axios }) {
    // $get返回的直接是result.data
    // 使用get返回的带有headers，status等信息
    const result = await $axios.get('http://localhost:8000/posts')
    return {
      posts: result.data,
    }
  },
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
