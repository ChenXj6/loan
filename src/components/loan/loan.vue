<template>
  <div>
    <!--
    <div>
      <div class="van-nav-bar van-hairline--bottom"
           style="z-index: 1;">
        <div class="van-nav-bar__left"></div>
        <div class="van-nav-bar__title van-ellipsis">{{$t('m.footer.publictab5')}}</div>
        <div class="van-nav-bar__right"></div>
      </div>
    </div>
    -->
    <div class="perback">
      <loanOne v-if="active == 'loan_one'"
               :dis="displayorder"
               @changeActive="change"></loanOne>
      <loanTwo v-if="active == 'loan_two'"
               :dis="displayorder"
               @changeActive="change"></loanTwo>
      <loanThree v-if="active == 'loan_three'"
                 :dis="displayorder"
                 @changeActive="change"></loanThree>
      <loanFour v-if="active == 'loan_four'"
                :dis="displayorder"
                @changeActive="change"></loanFour>
      <loanFive v-if="active == 'loan_five'"
                :dis="displayorder"
                @changeActive="change"></loanFive>
      <loanSix v-if="active == 'loan_six'"
               :dis="displayorder"
               @changeActive="change"></loanSix>
      <loanSeven v-if="active == 'loan_seven'"
                 :dis="displayorder"
                 @changeActive="change"></loanSeven>
      <loanEnd v-if="active == 'end'"
               :dis="displayorder"
               @changeActive="change"></loanEnd>
    </div>
    <div style="width:100%;height:98px"></div>
    <Foot></Foot>
  </div>
</template>
<script>
import Foot from '@/components/index/footer'
import loanOne from '@/components/loan/loan_one'
import loanTwo from '@/components/loan/loan_two'
import loanThree from '@/components/loan/loan_three'
import loanFour from '@/components/loan/loan_four'
import loanFive from '@/components/loan/loan_five'
import loanSix from '@/components/loan/loan_six'
import loanSeven from '@/components/loan/loan_seven'
import loanEnd from '@/components/loan/loan_end'

export default {
  components: { Foot, loanOne, loanTwo, loanThree, loanFour, loanFive, loanSix, loanSeven, loanEnd },
  data () {
    return {
      active: 'loan_one',
      displayorder: '1',
    }
  },
  methods: {
    meloanstatus(){
      this.$api.Post('meloanstatus').then(res => {
        if (res.status == 1) {
          if(res.result.loan == 0){
            this.active = 'loan_one'
            this.displayorder = '1'
          }else{
            this.active = 'loan_four'
            this.displayorder = '3'
          }
        }
      })
    },
    loanIndex () {
      this.$api.Post('loanIndex').then(res => {
        if (res.status == 1) {
          this.active = res.result.loan.loanname;
          this.displayorder = res.result.loan.displayorder;
        }
      })
    },
    change (val) {
      if (val.displayorder == 'end') {
        this.$api.Post('subLoanEnd').then(res => {
          if (res.status == 1) {
            console.log(res.result)
          }
        })
        return
      }
      this.active = val.active;
      this.displayorder = val.displayorder;
    },
  },
  created () {
    // this.loanIndex();
    this.meloanstatus()

  },
  mounted () {

  },
  watch: {

  }
}


</script>

<style>
  .stepbox{
    background-image: linear-gradient(to right, #1a73e7 , #6baafc) !important;
    border-radius: 0 0 0 20px;
    text-align:center;
    margin-bottom: 20px;
  }
  .stepbox .van-nav-bar{ background: none !important;}
  .stepbox i, .stepbox .van-nav-bar__title{ color: #fff !important; }
  .fr{ float: right;}
  .stepbox .steps{
    height: 46px;
    line-height: 46px;
    vertical-align: middle;
    padding: 0 20px;
    color: #fff;
  }
  .steps ul{
    float: left;
    border-bottom:1px #ccc dashed;
    position: relative;
    height: 16px;
    margin-top: 2px;
  }
  .steps li{
    display: inline-block;
    width: 16px;
    height: 16px;
    background: #6bb0fb;
    border: 4px #6bb0fb solid;
    border-radius: 2px;
    margin-right: 26px;
  }
  .steps li:last-child{ margin: 0;}
  .steps li.act{
    background: #ffc050;
    border: 4px #749fb0 solid;
  }
  .stepImg{
    padding: 20px;
  }
  .stepImg img{
    width: 100%;
    border-radius: 10px;
  }
  .el-button--primary{
    color: #FFF !important;
    background-color: #409EFF !important;
    border-color: #409EFF !important;
  }
</style>