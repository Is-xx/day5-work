<template>

    <div>
        <table border="1px" >
            <tr>
                <td>ID</td>
                <td>姓名</td>
                <td>年龄</td>
                <td>信息</td>
                <td>操作</td>
            </tr>
            <tr v-for="(user, index) in users" :key="index">
                <td>{{ user.id }}</td>
                <td>{{ user.name }}</td>
                <td>{{ user.age }}</td>
                <td>{{ user.msg }}</td>
                <td><a href="javascript:;" @click="delete_user(index)">删除</a> | <a href="javascript:;" @click="look_detail(index)">查看详情</a></td>
            </tr>
        </table>
        姓名：<input type="text" v-model="name"><br>
        年龄：<input type="text" v-model="age"><br>
        信息：<input type="text" v-model="msg"><br>
        <button @click="add_user">添加</button>
    </div>

</template>

<script>
export default {
    name: "User",
    data() {
        return {
            num: 1,
            name: '',
            age: '',
            msg: '',
            users: localStorage.users ? JSON.parse(localStorage.users) : [],
        }
    },
    methods: {
        add_user() {
            if (this.name && this.age && this.msg) {
                let person = {id: this.num, name: this.name, age: this.age, msg: this.msg};
                this.users.push(person);
                localStorage.users = JSON.stringify(this.users);
                this.num++;
                this.name = '';
                this.age = '';
                this.msg = '';
            }
        },
        delete_user(index){
            this.users.splice(index, 1);
            localStorage.users = JSON.stringify(this.users);
        },
        look_detail(index){
            this.$router.push('/user_detail/'+index)
        }
    }
}
</script>

<style scoped>

a{
    color: cornflowerblue;
}

</style>
