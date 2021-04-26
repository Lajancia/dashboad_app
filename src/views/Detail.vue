<template>
  <div>
    <p class="text-2xl">Detail page</p>
    <div>this is children of Dashboard page</div>
     <!-- <label class="w-20 flex-none font-semibold bg-gray-200">ID</label> -->
        <!-- <input type="text" class="flex-1" v-model="board.detail.id" /> -->
    
    
    <router-view />
  </div>
</template>

<script>

export default {
 name: "Board",
  components: {
    
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
};
</script>

<style lang="scss" scoped></style>