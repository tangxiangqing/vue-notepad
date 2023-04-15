<template>
  <div class="dialog">
    <header v-if="props.title">
      <span>{{ props.title }}</span>
      <button @click="closeDialog">X</button>
    </header>
    <main>{{ props.container }}</main>
    <footer>
      <span>
        <button class="cancel" @click="iscancel">{{ props.cancel }}</button>
        <button class="confirm" @click="isconfirm">{{ props.confirm }}</button>
      </span>
    </footer>
  </div>
</template>
<script>
export default {
  name: "DialogComponent",
};
</script>

<script setup>
import { ref, toRefs } from "vue";
const props = defineProps({
  // 标题
  title: {
    type: String,
  },

  // 内容
  container: {
    type: String,
    // 必填项
    required: true,
  },

  // 取消
  cancel: {
    type: String,
    default: "Cancel",
  },

  // 确定
  confirm: {
    type: String,
    default: "Confirm",
  },
});

// 向父组件传递数据

const emit = defineEmits(["closeDialog", "iscancel", "isconfirm"]);

//  向父组件传递方法
const closeDialog = () => {
  emit("closeDialog");
};

const iscancel = () => {
  emit("iscancel");
};
const isconfirm = () => {
  emit("isconfirm");
};
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
.dialog {
  width: 210px;
  height: 100px;
  background-color: white;
  border-radius: 5px;

  header {
    position: relative;
    width: 210px;
    height: 27px;

    padding: 10px 10px 5px;
    font-size: 9px;

    button {
      width: 27px;
      height: 27px;
      outline: 0;
      background-color: white;
      border: 0;
      color: #606266;
      cursor: pointer;
      position: absolute;
      right: 0;
      top: 3px;
    }
  }
  main {
    width: 210px;
    height: 40px;
    padding: 15px 10px;
    font-size: 7px;

    color: #606266;
  }
  footer {
    width: 210px;
    height: 33px;
    padding: 6px 10px 11px;
    text-align: right;

    button {
      width: 40px;
      height: 16px;
      outline: 0;
      padding: 4px 8px;
      font-size: 14px;
      background-color: white;
      border: 1px solid #606266;
      border-radius: 3px;
      cursor: pointer;
    }

    .cancel {
      color: #606266;
      margin-right: 10px;
    }
    .confirm {
      color: #fff;
      background-color: #409eff;
      border: 0;
    }
  }
}
</style>
