<!-- App.vue -->
<template>
  <div id="app">
    <div class="nav-bar">
      <!-- 导航链接，使用router-link -->
      <router-link to="/" class="nav-item">主页</router-link>
      <router-link to="/registration" class="nav-item">预约挂号</router-link>
      <router-link to="/my-registrations" class="nav-item">我的挂号</router-link>
      <router-link to="/my-bills" class="nav-item">我的账单</router-link>
      <router-link to="/messages" class="nav-item">消息中心</router-link>
      <router-link to="/profile" class="nav-item">个人中心</router-link> 
    </div>
    <div class="main-content">
      <!-- 路由视图 -->
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router';

export default {
  setup() {
    const router = useRouter();

    function navigate(event) {
      event.preventDefault();
      const path = event.target.getAttribute('to');
      router.push(path);
    }

    return {
      navigate
    };
  }
};
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
  height: 100%;
}

#app {
  display: flex;
  height: 100%;
}

.nav-bar {
  width: 200px;
  height: 100%;
  position: fixed;
  background-color: #444;
  color: white;
  padding: 20px;
}

.nav-item {
  color: white;
  display: block;
  margin-bottom: 10px;
  text-decoration: none;
  padding: 10px;
  border-bottom: 1px solid #444;
}

.nav-item:hover, .nav-item.active {
  background-color: #555;
}

.main-content {
  margin-left: 220px; /* Adjust the margin to account for the width of the nav-bar plus padding */
  padding: 20px;
  width: 100%; /* Ensure the main content takes up the remaining space */
}
</style>