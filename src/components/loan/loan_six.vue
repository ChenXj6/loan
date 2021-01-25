<template>
  <div class="shop_address_edit">
    <div class="tip">
      <!-- <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fpic.51yuansu.com%2Fpic3%2Fcover%2F01%2F04%2F90%2F5900f3b6ccf32_610.jpg&refer=http%3A%2F%2Fpic.51yuansu.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1611905331&t=434282b26bece2b3a9975e8102db2453"
           alt="">
      <p>申请成功</p> -->
      <van-list v-model="loading"
                :finished="finished"
                finished-text="没有更多了"
                @load="onLoad">
        <div class="recordllist"
             v-for="(item, index) in list"
             :key="index">
          <p>{{$t('m.loanSix.loanSix1')}}: &nbsp;{{item.name}}</p>
          <p>{{$t('m.loanSix.loanSix2')}} &nbsp;<a :href="item.down">{{item.down}}</a></p>
        </div>
      </van-list>
      <!-- <p>请耐心等待放款结果，预计24小时完成</p> -->

      <!-- <el-button type="primary">查看进度</el-button> -->
    </div>
  </div>
</template>
<script>
export default {
  props: {
    dis: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      list: [
        { 'name': '众安小贷', 'down': "https://www.baidu.com" },
        { 'name': '榕树贷款', 'down': "https://www.baidu.com"},
        { 'name': '维信闪贷', 'down': "https://www.baidu.com"},
        { 'name': '城一带', 'down': "https://www.baidu.com" },
        { 'name': '现金借款', 'down': "https://www.baidu.com" },
        { 'name': '缺钱吗', 'down': "https://www.baidu.com"},
        { 'name': '阔啦', 'down': "https://www.baidu.com" },
        { 'name': '应急无忧', 'down': "https://www.baidu.com" },
        { 'name': '无忧贷款', 'down': "https://www.baidu.com" },
      ],
      loading: false,
      finished: false
    };
  },
  methods: {
    onLoad () {
      // 异步更新数据
      // setTimeout 仅做示例，真实场景中一般为 ajax 请求

      // 加载状态结束
      this.loading = false;
      this.finished = true;
    }
  }
}
</script>
<style lang="less" scoped>
.shop_address_edit {
  width: 100%;
  height: 500px;
  margin: 0 auto;
  padding: 10px;
  position: relative;
}
// .tip {
//   position: absolute;
//   width: 60%;
//   top: 50%;
//   left: 50%;
//   transform: translate(-50%, -50%);
//   text-align: center;
//   > img {
//     width: 100px;
//     height: 100px;
//   }
//   > p:nth-child(2) {
//     color: #333;
//     margin-top: 10px;
//     font-size: 16px;
//     font-weight: bold;
//   }
//   > p:nth-child(3) {
//     color: #1989fa;
//     margin-top: 10px;
//     font-size: 10px;
//   }
//   > button {
//     margin-top: 50px;
//   }
// }
</style>