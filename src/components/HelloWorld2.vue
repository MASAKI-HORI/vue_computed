<template>
  <div>
    <section>
      <h2>console.logあり</h2>
      <label
        >入力
        <input v-model="blockCount"
      /></label>
      <div ref="row">
        {{ blockContent2 }}
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blockCount: ''
    }
  },
  computed: {
    blockContent2() {
      // ↓このconsole.logを出力すると「なぜか」動くようになります
      console.log(this.blockCount)
      const rowElement = this.$refs['row']
      // 一番最初はまだDOMにアクセスできないのでhogeを返す
      if (!rowElement) {
        return 'hoge'
      } else {
        return this.blockCount
      }
    }
  },
  mounted() {
    // computedを再計算
    this.blockCount = ''
  }
}
</script>

<style>
.block {
  display: inline-flex;
  border: 1px solid white;
  background-color: rgb(221, 244, 247);
  color: rgb(85, 99, 102);
  font-size: 11px;
  height: 80px;
  min-width: 50px;
  font-weight: bold;
  align-items: center;
  justify-content: center;
}
</style>