<template>
  <div id="app">
    <hello-world msg="hello, world" />
    <hr />
    <input v-model="message" />
    <input :value="message" @input="handleChange" />
    <div>{{ message }} | {{ message + '-' + message }}</div>
    <div :id="message"></div>
    <hr />
    <todo-list>
      <todo-item @delete="handleDelete" v-for="item in list" :key="item.id" :title="item.title" :del="item.del">
        <template v-slot:pre-icon="{ value }">
          <span>前置图标 {{ value }}</span>
        </template>
      </todo-item>
    </todo-list>
  </div>
</template>

<script>
//App.vue是根组件
// import TodoList from '@/components/TodoList.vue';
// import TodoItem from '@/components/TodoItem.vue';
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    // TodoItem,
    // TodoList,
    HelloWorld
  },
  data() {
    return {
      message: 'hello world',
      list: [
        {
          id: '001',
          title: '课程1',
          del: false
        },
        {
          id: '002',
          title: '课程2',
          del: true
        }
      ]
    };
  },
  methods: {
    handleChange(e) {
      this.message = e.target.value;
    },
    handleDelete(val) {
      // eslint-disable-next-line no-console
      console.log('handleDelete', val);
    }
  }
};
</script>
