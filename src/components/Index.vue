<template>

  <div>
    <input type="text" v-model="content">
    <button @click="add_note">发表留言</button>
    <ul>
      <li v-for="(note, index) in note_list" :key="index">
        <span>{{ note }}</span>&nbsp;&nbsp;&nbsp;
        <a href="javascript:;" @click="remove_note(index)">删除</a>
      </li>
    </ul>
  </div>

</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      content: '',
      note_list: localStorage.msg ? JSON.parse(localStorage.msg) : [],
    }
  },
  methods: {
    add_note() {
      if (this.content) {
        this.note_list.push(this.content);
        localStorage.msg = JSON.stringify(this.note_list);
        this.content = '';
      }
    },
    remove_note(index){
      this.note_list.splice(index, 1);
      localStorage.msg = JSON.stringify(this.note_list);
    }
  }
}
</script>

<style scoped>

a{
  color: palegreen;
}

</style>
