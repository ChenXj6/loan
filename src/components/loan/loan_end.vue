<template>
  <div class="shop_address_edit">
    <div class="tip">
      <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F35%2F06%2F84573bd07306218.jpg&refer=http%3A%2F%2Fbpic.588ku.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1611902009&t=ab7bd7f285a6bf020ff9015fa3512968"
           alt="" style="width:100px;height:100px">
      <p>订单审核中 ~~</p>
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

    }
  },
  methods: {
    getOrderStatus(){
      this.$api.Post('getOrderStatus').then(res=>{
        if (res.status == 1) {
          this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
        }else{
          this.$toast(res.msg)
        }
      })
    }
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
.tip{
  position: absolute;
  top: 50%;
  left:50%;
  transform: translate(-50%,-50%);
  text-align: center;
  >img{
    width: 100px;
    height: 100px;
  }
  >p{
    color: #1989fa;
    margin-top: 10px;
    font-size: 14px;
  }
  >button{
    margin-top:50px ;
  }
}
</style>