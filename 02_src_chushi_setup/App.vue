<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>性别：{{sex}}</h2>
  <button @click="sayHello">说话(Vue3中setup配置的sayHello)</button>
  <br>
  <br>
  <button @click="sayWelcome">说话(Vue2中配置的sayWelcome)</button>
  <br>
  <br>
  <button @click="test1">说话(Vue2中访问Vue3中setup的数据)</button>
  <br>
  <br>
  <button @click="test2">说话(Vue3中访问Vue2中的数据)</button>
</template>

<script>
  import { h } from 'vue'

  export default {
    name: 'App',
    data() {
      return {
        sex: '男'
      }
    },
    methods: {
      sayWelcome() {
        alert('欢迎来到来学习Vue3！')
      },
      test1() {
        console.log(this.name);
        console.log(this.age);
        console.log(this.sex);
        this.sayHello()
      }
    },
    setup() {
      let name = '张三'
      let age = 18

      function sayHello() {
        alert(`我叫${name}，我${age}岁了，你好啊！`)
      }

      function test2() {
        console.log(name);
        console.log(age);
        console.log(this.sex);
        console.log(this.sayWelcome)
      }

      // 返回一个对象（常用）
      return {
        name,
        age,
        sayHello,
        test2
      }

      // 返回一个函数（渲染函数） 
      // return () => h('h1', 'App组件')

    }
  }
</script>
