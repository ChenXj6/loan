<template>
  <div class="bje">
    <div class="stepbox">
      <div class="van-nav-bar">
        <div class="van-nav-bar__left"><i class="van-icon van-icon-arrow-left van-nav-bar__arrow"></i></div>
        <div class="van-nav-bar__title van-ellipsis">Bank Card Info</div>
        <div class="van-nav-bar__right"></div>
      </div>
      <div class="steps">
        <span class="fr">2/3 Steps</span>
        <ul>
          <li class="act"></li>
          <li class="act"></li>
          <li class=""></li>
        </ul>
        <div style="clear:both;"></div>
      </div>
    </div>
    <div class="with-type">
      <!-- <p>
        <van-field v-model="bank_name"
                   :placeholder="$t('m.Balance.withdrawal11')"
                   :label="$t('m.Balance.withdrawal12')" />
      </p> -->
      <p>
        <label class="lab"
               for="bank_name"
               style="">{{$t('m.Balance.withdrawal12')}}</label>
        <input class="inp"
               type="text"
               style=""
               :placeholder="$t('m.Balance.withdrawal11')"
               name="bank_name"
               v-model="bank_name"
               id="">
      </p>
      <p>
        <label class="lab"
               for="bank_card"
               style="">{{$t('m.Balance.withdrawal14')}}</label>
        <input class="inp"
               type="text"
               style=""
               :placeholder="$t('m.Balance.withdrawal13')"
               name="bank_card"
               v-model="bank_card"
               id="">
      </p>
      <p>
        <label class="lab"
               for="ifsc"
               style="">{{$t('m.Balance.withdrawal27')}}</label>
        <input class="inp"
               type="text"
               style=""
               :placeholder="$t('m.Balance.withdrawal28')"
               name="ifsc"
               v-model="ifsc"
               id="">
      </p>
      <!-- <p>
        <van-field v-model="bank_card"
                   :placeholder="$t('m.Balance.withdrawal13')"
                   :label="$t('m.Balance.withdrawal14')" />
      </p> -->
      <!-- <p>
        <van-field maxlength="11"
                   v-model="ifsc"
                   :placeholder="$t('m.Balance.withdrawal28')"
                   :label="$t('m.Balance.withdrawal27')" />
      </p> -->
    </div>
    <div class="with-btn">
      <el-button type="primary"
                 @click="next()">{{$t('m.changepwd.changepwd8')}}</el-button>
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
      bank_name: '',
      bank_card: '',
      ifsc: '',
      displayorder: this.dis
    }
  },
  methods: {
    next () {
      if (this.bank_name == '') {
        this.$toast(this.$t('m.loanOne.loanOne11'));
        return;
      }
      if (this.bank_card == '') {
        this.$toast(this.$t('m.loanOne.loanOne13'));
        return;
      }
      if (this.ifsc == '') {
        this.$toast(this.$t('m.loanOne.loanOne28'));
        return;
      }
      setTimeout(() => { this.$emit('changeActive', { displayorder: '3', active: 'loan_four' }) }, 500)


      // this.$api.Post('subLoanTwo', {bank_name:this.bank_name,bank_card:this.bank_card,ifsc:this.ifsc,displayorder:this.displayorder}).then(res => {
      //   if (res.status == 1) {
      //     this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
      //   }else{
      //     this.$toast(res.msg)
      //   }
      // })
    },
  },
  mounted () {

  }
}
</script>
<style lang="less" scoped>
</style>