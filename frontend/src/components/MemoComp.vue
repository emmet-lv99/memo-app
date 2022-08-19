<template>
  <div class="memo">
    <div class="act">
      <button class="btn btn-primary btn-primary" @click="add">+추가</button>
    </div>
    <ul>
      <li v-for="(item, idx) in state.data" :key="idx">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive } from 'vue'
import axios from 'axios'

export default {
  name: 'HeaderComp',
  setup() {
    const state = reactive({
      data: [],
    })

    const add = () => {
      state.data.push('추가된 메모에요')
    }

    axios.get('/api/memos').then(res => {
      console.log(res)
    })
    return { state, add }
  },
}
</script>

<style lang="scss" scoped>
.memo {
  .act {
    padding: 10px 10px 5px 5px;
    text-align: right;
  }
  ul {
    border-top: 1px solid #f7f7f7;
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      padding: 15px;
      margin: 5px;
      border: 1px solid #eee;
    }
  }
}
</style>
