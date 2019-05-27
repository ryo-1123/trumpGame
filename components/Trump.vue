<template>
  <div class="trump-wrapper">
    <div v-for="n in 52" :key="n">
      <img :src="trumpUrl[n-1]" width="100">
    </div>
  </div>
</template>

<script>
// トランプ用配列の準備
const trumpUrl = Array(52)

// 最大
const max = trumpUrl.length

// 配列に要素を入れる
for (let i = 0; i < max; i++) {
  trumpUrl[i] = require(`~/assets/images/trump/${i + 1}.gif`)
}

// for文でurlの作成
for (let i = max - 1; i > 0; i--) {
  const r = Math.floor(Math.random() * (i + 1))
  // 配列の入れ替え処理
  const tmp = trumpUrl[i]
  trumpUrl[i] = trumpUrl[r]
  trumpUrl[r] = tmp
}

// データの輸出(上のtemplateで使えるようにする)
export default {
  data() {
    return {
      trumpUrl
    }
  }
}
</script>
