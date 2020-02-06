<template>
  <div class='todo'>
    <ul>
      <li v-for="item in items" :key="item.index">
        <label :class="{ checked: item.isChecked }">
          <input type="checkbox" v-model="item.isChecked"> {{ item.title }}
        </label>
      </li>
    </ul>
    <div>
      <input type="text"
        placeholder="タスクを入力してみよう"
        v-model="newItemTitle" />
    </div>
    <div>
      <TodoButton @buttonClick="addTodo(newItemTitle)" :text="'タスクを追加する'"></TodoButton>
      <TodoButton @buttonClick="deleteTodo(newItemTitle)" :text="'チェックを付けたタスクを削除する'"></TodoButton>
    </div>
  </div>
</template>

<script>
import TodoButton from './components/Button'
export default {
  name: 'App',
  components: {
    TodoButton: TodoButton
  },
  data: () => {
    return {
      items: [
        {
          title: '夕飯の材料を買いに行く',
          isChecked: false
        },
        {
          title: 'お風呂の掃除をする',
          isChecked: true
        },
        {
          title: 'ゴミ出しをする',
          isChecked: false
        }
      ],
      newItemTitle: '',
    }
  },
  methods: {
    addTodo(newTitle) {
      let item = {
        title: newTitle,
        isChecked: false
      }
      this.items.push(item)
    },
    deleteTodo() {
      this.items = this.items.filter(item => {
        return item.isChecked === false
      })
    }
  }
}
</script>
