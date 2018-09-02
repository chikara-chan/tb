<template>
  <div class="about">
    <textarea v-model="input" rows="10"/><br><br>
    <button @click="click">biu ～～～</button><br><br>
    <textarea v-model="input2" rows="100" readonly/>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      input: "",
      input2: ""
    };
  },
  methods: {
    click() {
      this.input2 =
        `${"点击人气".padEnd(7)}${"点击热度".padEnd(8)}${"点击率".padEnd(
          8
        )}${"在线商品数".padEnd(7)}${"直通车参考价".padEnd(
          7
        )}${"支付转化率".padEnd(7)}${"搜索人气".padEnd(7)}  ${"搜索热度".padEnd(
          8
        )}${"未知".padEnd(8)}${"商城点击占比".padEnd(7)}${"交易指数".padEnd(
          7
        )}${"搜索词"}\n\n` +
        JSON.parse(this.input)
          .data.map(
            item =>
              `${String(item.clickHits).padEnd(10)}${String(
                item.clickHot
              ).padEnd(10)}${String(
                (item.clickRate * 100).toFixed(2) + "%"
              ).padEnd(10)}${String(item.onlineGoodsCnt).padEnd(10)}${String(
                item.p4pAmt && item.p4pAmt.toFixed(2)
              ).padEnd(12)}${String(
                (item.payConvRate * 100).toFixed(2) + "%"
              ).padEnd(10)}${String(item.seIpvUvHits).padEnd(10)}  ${String(
                item.sePvIndex
              ).padEnd(10)}${String(item.spvRatio).padEnd(10)}${String(
                (item.tmClickRatio * 100).toFixed(2) + "%"
              ).padEnd(10)}${String(item.tradeIndex).padEnd(10)}${String(
                item.keyword
              )}`
          )
          .join("\n");

      console.log(this.input2);
    }
  }
};
</script>
<style>
input {
  width: 80%;
}
textarea {
  width: 80%;
}
</style>
