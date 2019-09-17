<template>
  <div class="trumpWrapper">
    <div
      v-for="n in 52"
      :key="n"
      class="showTrump"
    >
      <img
        :src="trump[n-1].on
          ? trump[n-1].url
          : trump[n-1].backUrl"
        width="100"
        @click="trump[n-1].on=!trump[n-1].on, checkCard()"
      >
      <p>{{ trump[n-1].num }}</p>
    </div>
  </div>
</template>

<script>
// トランプの連想配列の作成
const trump = Array(52)
// 赤黒の判定用
let count = 1
let blackRed = 1
// 最大
const max = trump.length

// カードのnumber情報を持たせるための変数
let num = 0
// 配列に要素を入れる
for (let i = 0; i < max; i++) {
  num++
  // numが13の間の処理
  trump[i] = {
    'url': require(`~/assets/images/trump/${i + 1}.gif`),
    'backUrl': require(`~/assets/images/trump/z0${blackRed}.gif`),
    // カードnum情報
    'num': num,
    'on': false
  }
  // numが13になったら1からスタート
  if (num === 13) {
    num = 0
    count++
    if (count === 2 || count === 3) {
      blackRed = 2
    } else {
      blackRed = 1
    }
  }
}

// 配列の入れ替え処理
for (let i = max - 1; i > 0; i--) {
  const r = Math.floor(Math.random() * (i + 1))
  const tmp = trump[i]
  trump[i] = trump[r]
  trump[r] = tmp
}

// データの輸出(上のtemplateで使えるようにする)
export default {
  data() {
    return {
      trump
    }
  },
  methods: {
    checkCard() {

    }
  }
}
</script>

<style>
.showTrump {
  display: inline-block;
  margin: 0 7px;
  width: 87px;
}
</style>
