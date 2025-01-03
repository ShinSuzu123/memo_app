<template>
  <div id="app">
    <h1>メモアプリ</h1>
    <div>
      <!-- 入力フォーム -->
      <input
        v-model="newMemo"
        placeholder="メモを入力してください"
        @keyup.enter="addMemo"
      />
      <button @click="addMemo">追加</button>
    </div>
    <!-- メモのリスト -->
    <ul>
      <li v-for="(memo, index) in memos" :key="index">
        {{ memo }}
        <button @click="deleteMemo(index)">削除</button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      newMemo: "", //新しいメモの入力値
      memos: [],
    };
  },
  methods: {
    //メモの追加
    addMemo() {
      if(this.newMemo.trim() === "") return; // 空白の場合は無効
      this.memos.push(this.newMemo); // 配列に追加
      this.newMemo = "";
    },
    // メモを削除する
    deleteMemo(index) {
      this.memos.splice(index, 1); //指定のメモを削除
    }
  }
}
</script>
