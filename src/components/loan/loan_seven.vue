<template>
  <div class="shop_address_edit">
    <div class="tip">
      <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F41%2F16%2F99573d2cce230db.jpg&refer=http%3A%2F%2Fku.90sjimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1611905411&t=2cccd9a668c9aa7d2ffa3f09d5cc7b23"
           alt="">
      <p></p>
      <!-- <p>请耐心等待放款结果，预计24小时完成</p> -->

      <!-- <el-button type="success">重新申请</el-button> -->
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

    }
  },
  methods: {
    
  },
  mounted () {

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
.tip {
  position: absolute;
  width: 60%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  > img {
    width: 100px;
    height: 100px;
  }
  > p:nth-child(2) {
    color: #333;
    margin-top: 10px;
    font-size: 16px;
    font-weight: bold;
  }
  > p:nth-child(3) {
    color: #1989fa;
    margin-top: 10px;
    font-size: 10px;
  }
  > button {
    margin-top: 50px;
  }
}
</style>