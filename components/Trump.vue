<template>
  <div class="trump-wrapper">
    <div v-for="n in 52" :key="n">
      <img :src="trumpUrl[n-1].url" width="100">
    </div>
  </div>
</template>

<script>
// トランプの連想配列の作成
const trumpUrl = Array(52)

// 最大
const max = trumpUrl.length

// カードのnumber情報を持たせるための変数
let num = 0
// 配列に要素を入れる
for (let i = 0; i < max; i++) {
  num++
  // numが13の間の処理
  if (num < 14) {
    trumpUrl[i] = { 'url': require(`~/assets/images/trump/${i + 1}.gif`),
      // カードnum情報
      'num': num,
      'on': 0
    }
    // numが13になったら1からスタート
    if (num === 13) {
      num = 0
    }
  }
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
