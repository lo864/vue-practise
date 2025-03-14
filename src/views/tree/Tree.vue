<!--
 * @Author: lost_3stars 1364282438@qq.com
 * @Date: 2025-03-15 01:39:17
 * @LastEditors: lost_3stars 1364282438@qq.com
 * @LastEditTime: 2025-03-15 01:40:11
 * @FilePath: \vue-practise\src\views\tree\Tree.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<!--
一个可以递归渲染自己的嵌套树组件。
你可以双击一个项目将其转变为一个文件夹。
-->

<script setup>
import { ref } from 'vue'
import TreeItem from './TreeItem.vue'

const treeData = ref({
  name: 'My Tree',
  children: [
    { name: 'hello' },
    { name: 'world' },
    {
      name: 'child folder',
      children: [
        {
          name: 'child folder',
          children: [{ name: 'hello' }, { name: 'world' }]
        },
        { name: 'hello' },
        { name: 'world' },
        {
          name: 'child folder',
          children: [{ name: 'hello' }, { name: 'world' }]
        }
      ]
    }
  ]
})
</script>

<template>
  <ul>
    <TreeItem class="item" :model="treeData"></TreeItem>
  </ul>
</template>

<style>
.item {
  cursor: pointer;
  line-height: 1.5;
}
.bold {
  font-weight: bold;
}
</style>
