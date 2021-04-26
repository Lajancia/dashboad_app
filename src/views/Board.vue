<template>
  <div class="w-1/2 mx-auto">
    <p class="text-xl">Board Page {{ $route.params.id }}!</p>
    <div class="flex justify-center">
      <table>
        <thead class="text-lg font-semibold bg-green-200">
          <tr>
            <th class="w-24 border-r">ID</th>
            <th class="w-96">
              제목
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="b in board.list" v-bind:key="b.id">
            <td class="border-r">{{ b.id }}</td>
            <td
              class="hover:text-green-500 cursor-pointer"
              @click="showDetailPage(b)"
            >
              {{ b.subject }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="text-right my-2">
      <button class="px-2 py-1 mr-2 border" @click="save">수정</button>
      <button class="px-2 py-1 border">취소</button>
    </div>
    <div>
      <div class="flex">
        <label class="w-20 flex-none font-semibold bg-gray-200">ID</label>
        <input type="text" class="flex-1" v-model="board.detail.id" />
      </div>
      <div class="flex">
        <label class="w-20 flex-none font-semibold bg-gray-200">제목</label>
        <input type="text" class="flex-1" v-model="board.detail.subject" />
      </div>
      <div class="flex">
        <label class="w-20 flex-none font-semibold bg-gray-200">내용</label>
        <editor ref="editor" class="text-left" />
      </div>
    </div>

    <router-view />
  </div>
</template>

<script>
import "codemirror/lib/codemirror.css";
import "@toast-ui/editor/dist/toastui-editor.css";

import { Editor } from "@toast-ui/vue-editor";

export default {
  name: "Board",
  components: {
    Editor,
  },
  data() {
    return {
      board: {
        list: [
          { id: 1, subject: "배고파요", contents: "text1" },
          { id: 2, subject: "노랑통닭", contents: "치킨" },
        ],
        detail: {},
      },
    };
  },
  methods: {
    showDetailPage(selectBoard) {
      this.board.detail = selectBoard;
      this.$refs.editor.invoke("setMarkdown", this.board.detail.contents);
    },
    save() {
      const contents = this.$refs.editor.invoke("getMarkdown");
      this.board.detail.contents = contents;
    },
  },
};



</script>

<style lang="scss" scoped></style>