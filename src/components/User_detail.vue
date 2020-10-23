<template>

    <div>
        用户信息：<br>
        ID：{{ id }}<br>
        姓名：{{ name }}<br>
        年龄：{{ age }}<br>
        信息：{{ msg }}
        <button @click="go_back">返回</button>
    </div>

</template>

<script>
export default {
    name: "User_detail",
    data(){
        return{
            id: '',
            name: '',
            age: '',
            msg:'',
        }
    },
    methods: {
        go_back(){
            this.$router.go(-1);
        }
    },
    created() {
        let num = parseInt(this.$route.params.id);
        let users = JSON.parse(localStorage.users);
        let user = users[num]
        this.id = user['id'];
        this.name = user['name'];
        this.age = user['age'];
        this.msg = user['msg'];
    }
}
</script>

<style scoped>

</style>
