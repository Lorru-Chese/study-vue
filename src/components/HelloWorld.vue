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

// 同時呼叫兩種函式(程式運算上會按照排列先後順序跑程式碼，中間有錯就GG)
const userClick = () => {
  increase();
  change();
}
const userMsg = ref("")
const userMail = ref("")
const submitted = ref(false)

const submit = () => {
  if (!userMail.value.includes("@")) {
    alert('信箱怎麼會缺少@?')
    return
  }
  submitted.value = true
  userMsg.value = ""
  userMail.value = ""
}

</script>

<template>
  <div>
    <p>{{ message }}</p>
    <p>計數器：{{count}}</p>
    <button @click="userClick">+1</button>
  </div>
  <div>
    <h1>一張表單在這裡</h1>
    <input v-model="userMsg" placeholder="輸入姓名">
    <input v-model="userMail" placeholder="輸入信箱">
    <button @click = "submit">提交</button>
    <div v-if = "submitted">
      <p>姓名：{{ userMsg }}</p>
      <p>信箱：{{ userMail }}</p>
    </div>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>