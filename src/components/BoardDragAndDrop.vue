<script setup>
import { cloneDeep } from 'lodash'
import { reactive } from 'vue'
const props = defineProps({
  board: Object,
  tasks: Array
})
const tasks = reactive(cloneDeep(props.tasks))
const board = reactive(cloneDeep(props.board))
const colums = reactive(JSON.parse(board.order))

</script>

<template>
  <div class="flex item-start py-10">
    <draggable :list="column" groups="columns" :item-key="id">
      <template #item="{ element: column }">
        <div class="colum bg-gray-100 flex fex-col justify-between rounded-lg px-3 rounded w-[300px]">
          <h2>{{ column.title }}</h2>
          <draggable list="column taskIds" group="tasks" :item-key="uid">
            <template #item="{ element: taskId }">
              <task-card
                v-if="tasks.find((t) => t.id === taskId)"
                :task="tasks.find((t) => t.id === taskId)"
                class="mt-3 cursor-move"
              ></task-card>
            </template>
          </draggable>
        </div>
      </template>
    </draggable>
  </div>
</template>