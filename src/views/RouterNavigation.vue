<template>
    <button type="button" @click="getRouter">getRouter</button>

    <button type="button" @click="push">
        Push
    </button>
    <button type="button" @click="replace">
        Replace
    </button>
    <button type="button" @click="go">
        Go
    </button>
    <hr>
    <button type="button" @click="addRoute">
        新增路由
    </button>
</template>

<script>
export default {
  methods: {
    // 包含歷史紀錄：可以上一夜
    push() {
      // 方式一
      // this.$router.push('/newpage/dynamicRouter/:id');
      // 方式二
      this.$router.push({
        name: 'about',
      });
    },
    // 沒有歷史紀錄：不能回上一頁
    replace() {
      this.$router.replace({ name: 'about' });
    },
    go() {
      // 正數：下一頁；負數：上一頁
      this.$router.go(-1);
    },
    getRouter() {
      // $route 可以看到路由底下的所有資訊，如：參數、篩選(query)
      console.log(this.$route);
      // $router 可以看到路由底下的所有方法，如：push、replace
      // 參考：https://router.vuejs.org/zh/api/interfaces/Router.html
      console.log(this.$router);
    },
    addRoute() {
      // 在按下addRoute 前，先輸入網址 http://localhost:8080/#/newabout 會顯示不存在，按下新增後才看得到
      this.$router.addRoute({
        path: '/newAbout',
        name: 'newAbout',
        component: () => import('./AboutView.vue'),
      });
    },
  },
};
</script>
