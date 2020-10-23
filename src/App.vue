<template>
    <div id="app">

        <h3>这是主页</h3>
        <router-link to="index">显示留言板</router-link>
        <router-link to="/user">显示用户信息</router-link>
        <hr>

        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'App'
}
</script>

<style>

</style>
