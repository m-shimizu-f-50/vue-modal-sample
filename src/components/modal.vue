<template>
  <div>
    <v-btn small color="primary" @click="openModal"> 編集 </v-btn>
    <transition name="fade">
      <div id="overlay" v-show="showContent">
        <div id="content">
          <p>編集画面</p>
          <v-card class="pa-5">
            <div style="display: flex; align-items: center" class="mb-5">
              <span>タイトル：</span>
              <v-text-field
                v-model="title"
                solo
                flat
                hide-details
                class="ml-2 text-style"
              />
            </div>
            <div style="display: flex; align-items: center">
              <span>内容：</span>
              <v-text-field
                v-model="content"
                solo
                flat
                hide-details
                class="ml-2 text-style"
              />
            </div>
          </v-card>
          <div style="display: flex" class="mt-5">
            <v-btn small color="error" 　class="mr-3" @click="closeModal">
              閉じる
            </v-btn>
            <v-btn small color="success" @click="update"> 更新 </v-btn>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    data: Object,
  },
  data() {
    return {
      showContent: false,
      title: this.data.title,
      content: this.data.content,
    };
  },
  methods: {
    openModal: function () {
      this.showContent = true;
    },
    closeModal: function () {
      this.showContent = false;
    },
    test: function () {
      console.log(this.data);
    },
    update() {
      this.$emit("my-click", this.title, this.content);
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

.fade {
  &-enter {
    opacity: 0;
    &-to {
      opacity: 1;
    }
    &-active {
      transition: opacity 0.6s;
    }
  }
  &-leave {
    opacity: 1;
    &-to {
      opacity: 0;
    }
    &-active {
      transition: opacity 0.6s;
    }
  }
}

.text-style {
  border: solid 1px #bdbdbd;
  border-radius: 10px;
}
</style>