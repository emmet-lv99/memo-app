<template>
  <div class="memo">
    <div class="act">
      <button class="btn btn-primary btn-primary" @click="add">+추가</button>
    </div>
    <ul>
      <li
        v-for="(item, idx) in state.data"
        :key="item.id"
        @click="edit(item.id)"
      >
        {{ item.content }}
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
      const content = prompt('내용을 입력해주세요.')
      if (!content) {
        alert('내용을 입력해주세요.')
        return add()
      }
      axios.post('/api/memos', { content }).then(res => {
        state.data = res.data
      })
    }

    const edit = id => {
      const content = prompt(
        '내용을 입력해주세요',
        state.data.find(item => item.id === id).content,
      )
      axios
        .put('/api/memos/' + id, { content })
        .then(res => {
          state.data = res.data
        })
        .catch(err => console.log(err))
    }

    axios.get('/api/memos').then(res => {
      state.data = res.data
    })
    return { state, add, edit }
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
