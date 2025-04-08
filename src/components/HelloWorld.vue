<script setup>
import { ref , computed } from 'vue'

defineProps({
  msg: String,
})

const message = ref("點下面的按鈕看看");
const count = ref(0);
const increase = () => {
  count.value++;
}

const change = () => {
  if (count.value < 10) {
    message.value = "點下面的按鈕看看";
  }
  else {
    message.value = "計數達到10！";
  }  
}

const isActive = ref(true)


// 同時呼叫兩種函式(程式運算上會按照排列先後順序跑程式碼，中間有錯就GG)
const userClick = () => {
  increase();
  change();
}

</script>

<template>
  <div>
    <p>{{ message }}</p>
    <p>計數器：{{count}}</p>
    <button @click="userClick">+1</button>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
