<template>
  <div>
    <v-btn small color="success" @click="openModal"> 編集 </v-btn>
    <div id="overlay" v-show="showContent">
      <div id="content">
        <p>これがモーダルウィンドウです。</p>
        <button @click="closeModal">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showContent: false,
    };
  },
  methods: {
    openModal: function () {
      this.showContent = true;
    },
    closeModal: function () {
      this.showContent = false;
    },
  },
};
</script>

<style lang="scss" scoped>
#overlay {
  /*　要素を重ねた時の順番　*/
  z-index: 1;

  /*　画面全体を覆う設定　*/
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);

  /*　画面の中央に要素を表示させる設定　*/
  display: flex;
  align-items: center;
  justify-content: center;
}
#content {
  z-index: 2;
  width: 50%;
  padding: 1em;
  background: #fff;
}
</style>