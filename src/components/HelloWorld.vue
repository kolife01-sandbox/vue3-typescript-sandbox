<template>
  <div class="hello">
    <h1>{{ propsMsg }}</h1>
    <h1>{{ msg }}</h1>
    <h1>{{ book.title }}/{{ book.author }}/{{ book.year }}</h1>
    <h2>{{ getLength }}</h2>
    <h2>{{ changeMessage() }}</h2>
    <h2>{{ fullName }} {{ user.age}}</h2>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

interface Book {
  title: string;
  author: string;
  year: number;
}

export interface User {
  firstName: string;
  lastName: string;
  age: number;
}

export default defineComponent({
  name: 'HelloWorld',
  data(){
    return {
      msg: "Hello TypeScript",
      detail: "Hello TypeScript",
      book: {
        title: 'Vue 3 Guide',
        author: 'Vue Team',
        year: 2020
      } as Book
    }
  },
  computed: {
    getLength(): number{
      return this.msg.length;
    },
    fullName(): string {
      return this.user.firstName + this.user.lastName
    }
  },
  methods: {
    changeMessage(): string{
      return this.detail = "Hi TypeScript"
    }
  },
  props: {
    propsMsg:{
      type: String as PropType<string>,
      required: true,
    },
    user: {
      type: Object as PropType<User>,
      required: true,
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
