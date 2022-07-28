<script setup lang="ts">
import { computed, ref } from "vue";
// import { useAlerts } from "@/stores/Alerts";
import { useRouter } from "vue-router";
import type { Board } from "@/types";
const router = useRouter();
const boards = ref<Partial<Board>[]>([
  {
    id: "1",
    title: "My First Board",
    order: "[]",
    image: {
      downloadUrl: "https://picsum.photos/480/270?board=1",
    },
  },
  {
    id: "2",
    title: "My Second Board",
    order: "[]",
    image: {
      downloadUrl: "https://picsum.photos/480/270?board=2",
    },
  },
  {
    id: "3",
    title: "My Third Board",
    order: "[]",
  },
]);
function createBoard(){
  console.log('board created')
}
const newBoardTemplate = computed(() => {
  return {
    title: "My New Board",
    order: JSON.stringify([
      {
        uid: "1",
        title: "Backlog",
        taskIds: [],
      },
    ]),
  };
});
</script>
<template>
  <AppPageHeading>Boards</AppPageHeading>
    <div class="flex">
      <BoardCard v-for="board in boards" :key="board.id" :board="board" />
      <button class="text-gray-500" @click="createBoard()">
        <span>New Board +</span>
      </button>
    </div>
</template>