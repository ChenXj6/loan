<template>
  <div id="bje5" class="bje">
    <p class="division"></p>
    <div class="with-type">
      <p>
        <van-field maxlength="30"
                   v-model="name"
                   :placeholder="$t('m.loanOne.loanOne6')"
                   :label="$t('m.loanOne.loanOne1')" />
      </p>
      <p>
        <van-field maxlength="30"
                   v-model="sex"
                   @click="chooseSex"
                   disabled
                   :placeholder="$t('m.loanOne.loanOne7')"
                   :label="$t('m.loanOne.loanOne2')" />
      </p>
      <p>
        <van-field maxlength="30"
                   v-model="birth"
                   @click="selectbirth"
                   disabled
                   :placeholder="$t('m.loanOne.loanOne8')"
                   :label="$t('m.loanOne.loanOne3')" />
      </p>
      <p>
        <van-field maxlength="30"
                   @click="chooseMarriage"
                   v-model="marriage"
                   disabled
                   :placeholder="$t('m.loanOne.loanOne9')"
                   :label="$t('m.loanOne.loanOne4')" />
      </p>
      <p>
        <van-field maxlength="30"
                   v-model="job"
                   :placeholder="$t('m.loanOne.loanOne7')"
                   :label="$t('m.loanOne.loanOne5')" />
      </p>
      <p>
        <van-field maxlength="30"
                   v-model="relationship"
                   disabled
                   @click="chooseRelationS"
                   :placeholder="$t('m.loanFive.loanFive2')"
                   :label="$t('m.loanFive.loanFive1')" />
      </p>
    </div>
    <div class="with-btn">
      <el-button type="primary"
                 @click="next()">{{$t('m.changepwd.changepwd8')}}</el-button>
    </div>
    <!-- sex -->
    <van-popup v-model="isOpenSexBox"
               position="bottom">
      <van-picker show-toolbar
                  :columns="sexBox"
                  @cancel="isOpenSexBox = false"
                  @confirm="onChooseSex"
                  :confirm-button-text="$t('m.Personal.Center23')"
                  :cancel-button-text="$t('m.Personal.Center24')" />
    </van-popup>
    <!-- birth -->
    <van-datetime-picker v-if="isOpenDate"
                         type="date"
                         :min-date="minDate"
                         :max-date="maxDate"
                         @change="returnF"
                         @cancel="isOpenDate = false"
                         @confirm="onSelectbirth"
                         :confirm-button-text="$t('m.Personal.Center23')"
                         :cancel-button-text="$t('m.Personal.Center24')" />
    <!-- marriage -->
    <van-popup v-model="isOpenMaritalS"
               position="bottom">
      <van-picker show-toolbar
                  :columns="marriageBox"
                  @cancel="isOpenMaritalS = false"
                  @confirm="onChooseMarriage"
                  :confirm-button-text="$t('m.Personal.Center23')"
                  :cancel-button-text="$t('m.Personal.Center24')" />
    </van-popup>
    <!-- relationship -->
    <van-popup v-model="isOpenRelationS"
               position="bottom">
      <van-picker show-toolbar
                  :columns="relationshipBox"
                  @cancel="isOpenRelationS = false"
                  @confirm="onChooseRelationS"
                  :confirm-button-text="$t('m.Personal.Center23')"
                  :cancel-button-text="$t('m.Personal.Center24')" />
    </van-popup>
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
      minDate: new Date(1930, 0, 1),
      maxDate: new Date(2035, 11, 31),
      displayorder: this.dis,
      name: '',
      sex: '',
      birth: '',
      marriage: '',
      job: '',
      relationship: '',
      isOpenSexBox: false,
      isOpenDate: false,
      isOpenMaritalS: false,
      isOpenRelationS: false,
      sexBox: [
        { text: this.$t('m.loanOne.loanOne12'), value: this.$t('m.loanOne.loanOne12') },
        { text: this.$t('m.loanOne.loanOne14'), value: this.$t('m.loanOne.loanOne14') },
      ],
      marriageBox: [
        { text: this.$t('m.loanOne.loanOne15'), value: this.$t('m.loanOne.loanOne15') },
        { text: this.$t('m.loanOne.loanOne16'), value: this.$t('m.loanOne.loanOne16') },
        { text: this.$t('m.loanOne.loanOne17'), value: this.$t('m.loanOne.loanOne17') },
      ],
      relationshipBox: [
        { text: this.$t('m.loanFive.loanFive3'), value: this.$t('m.loanFive.loanFive3') },
        { text: this.$t('m.loanFive.loanFive4'), value: this.$t('m.loanFive.loanFive4') },
        { text: this.$t('m.loanFive.loanFive16'), value: this.$t('m.loanFive.loanFive16') },
        { text: this.$t('m.loanFive.loanFive5'), value: this.$t('m.loanFive.loanFive5') },
      ],
    }
  },
  methods: {
    returnF () {
      return false
    },
    chooseSex () {
      this.isOpenSexBox = true
    },
    onChooseSex (e) {
      this.sex = e.value;
      this.isOpenSexBox = false;
    },
    selectbirth () {
      this.isOpenDate = true;
    },
    checkTime (i) {
      if (i < 10) {
        i = '0' + i
      }
      return i;
    },
    onSelectbirth (e) {
      var date;
      date = new Date(e)
      this.birth = date.getFullYear() + '-' + this.checkTime(date.getMonth() + 1) + '-' + this.checkTime(date.getDate());
      this.isOpenDate = false;
    },
    chooseMarriage () {
      this.isOpenMaritalS = true
    },
    onChooseMarriage (e) {
      this.marriage = e.value;
      this.isOpenMaritalS = false;
    },
    chooseRelationS () {
      this.isOpenRelationS = true
    },
    onChooseRelationS (e) {
      this.relationship = e.value;
      this.isOpenRelationS = false;
    },
    next () {
      if (this.name == '') {
        this.$toast(this.$t('m.loanOne.loanOne6'));
        return;
      }
      if (this.sex == '') {
        this.$toast(this.$t('m.loanOne.loanOne7'));
        this.isOpenSexBox = true;
        return;
      }
      if (this.birth == '') {
        this.$toast(this.$t('m.loanOne.loanOne8'));
        this.isOpenDate = true;
        return;
      }
      if (this.marriage == '') {
        this.$toast(this.$t('m.loanOne.loanOne9'));
        this.isOpenMaritalS = true;
        return;
      }
      if (this.job == '') {
        this.$toast(this.$t('m.loanOne.loanOne10'));
        return;
      }
      if (this.relationship == '') {
        this.$toast(this.$t('m.loanFive.loanFive2'));
        return;
      }
      this.$api.Post('subLoanFive', { name: this.name, sex: this.sex, birth: this.birth, marriage: this.marriage, job: this.job, relationship: this.relationship, displayorder: this.displayorder }).then(res => {
        if (res.status == 1) {
          this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
        }else{
          this.$toast(res.msg)
        }
      })
    },
  },
  mounted () {
  },
  watch: {
  }
}
</script>
<style lang="less" scoped>
</style>