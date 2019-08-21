<template>
  <section class="container">
    <div>
      <h1 class="title">
        trumpGame
      </h1>
      <trump />
    </div>
  </section>
</template>

<script>
// importでデータを輸入する
import Trump from '~/components/Trump.vue'

// exportでデータを輸出する
export default {
  components: {
    Trump
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: rgb(122, 223, 112);
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
</style>
