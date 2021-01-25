<template>
  <div class="bje">
    <div class="stepbox">
      <div class="van-nav-bar">
        <div class="van-nav-bar__left"><i class="van-icon van-icon-arrow-left van-nav-bar__arrow"></i></div>
        <div class="van-nav-bar__title van-ellipsis">Bank Card Info</div>
        <div class="van-nav-bar__right"></div>
      </div>
      <div class="steps">
        <span class="fr">3/3 Steps</span>
        <ul>
          <li class="act"></li>
          <li class="act"></li>
          <li class="act"></li>
        </ul>
        <div style="clear:both;"></div>
      </div>
    </div>
    <div class="with-type">
      <div class="with-type">
        <!--  新增静态内容  -->
        <div class="payment">
          <div class="noticesBox">
            <div role="alert" class="van-notice-bar">
              <i class="van-icon van-icon-volume-o van-notice-bar__left-icon"></i>
              <div role="marquee" class="van-notice-bar__wrap">
                <div class="van-notice-bar__content van-ellipsis" style="padding-left: 0px; animation-delay: 1s; animation-duration: 0s;">
                  <div class="notice-swipe van-swipe">
                    <div class="van-swipe__track">883****534 successfully received $500000</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="boxs">
            <div class="box fr">
              <p>Remain Time</p>
              <h2>01:29:50</h2>
            </div>
            <div class="box">
              <p>Available Credit</p>
              <h2>$30,000</h2>
            </div>
          </div>
          <h4>Payment Notice</h4>
          <p class="tips">*If you cannot prove your solvency within 90 minutes,you will be disqualified from the loan.</p>
        </div>
        <div class="loanlist">
          <h4>Please select the loan amount</h4>
          <div class="loanbox act">
            <i></i>
            <h4>Borrow: $10000</h4>
            <p><span>Interest: $293</span><span>Cycle:92days</span></p>
          </div>
          <div class="loanbox">
            <i></i>
            <h4>Borrow: $10000</h4>
            <p><span>Interest: $293</span><span>Cycle:92days</span></p>
          </div>
          <div class="loanbox">
            <i></i>
            <h4>Borrow: $10000</h4>
            <p><span>Interest: $293</span><span>Cycle:92days</span></p>
          </div>
        </div>
        <div class="loanfoot">
          <div class="lt">
            <p>Interest Deposit</p>
            <h2>Borrow: $10000</h2>
          </div>
          <div class="rt">
            <button class="el-button el-button--primary">Pay</button>
          </div>
        </div>
<!--
      <p>
        <el-button :type="defaultActive == index? 'success' : 'info'"
                   v-for="(item,index) in pay_list"
                   :key="index"
                   @click="chooseLoan(item,index)">{{item.loan_name}}</el-button>
      </p>
      <div class="with-btn">
        <el-button type="primary"
                   v-if="btnDis"
                   @click="pay()">{{ pay_money || 100}}</el-button>
        <el-button type="primary"
                   v-else>{{$t('m.loanFour.loanFour8')}}</el-button>
-->
      </div>
      <!-- <p>
        <van-field maxlength="30"
                   v-model="loanName"
                   input-align="right"
                   @click="chooseLoan"
                   disabled
                   :placeholder="$t('m.loanFour.loanFour2')"
                   :label="$t('m.loanFour.loanFour1')" />
      </p>
      <p v-if="loanid != 0">
        <van-field maxlength="30"
                   v-model="loan_mount"
                   input-align="right"
                   disabled
                   :placeholder="$t('m.loanFour.loanFour2')"
                   :label="$t('m.loanFour.loanFour3')" />
      </p>
      <p v-if="loanid != 0">
        <van-field maxlength="30"
                   v-model="days"
                   input-align="right"
                   disabled
                   :placeholder="$t('m.loanFour.loanFour2')"
                   :label="$t('m.loanFour.loanFour4')" />
      </p> 
      <p v-if="loanid != 0">
        <van-field maxlength="30"
                   v-model="daily_interest"
                   input-align="right"
                   disabled
                   :placeholder="$t('m.loanFour.loanFour2')"
                   :label="$t('m.loanFour.loanFour5')" />
      </p>
      <p v-if="loanid != 0">
        <van-field maxlength="30"
                   v-model="pay_money"
                   input-align="right"
                   disabled
                   :placeholder="$t('m.loanFour.loanFour2')"
                   :label="$t('m.loanFour.loanFour6')" />
      </p>-->
    </div>
    <!-- <div class="with-btn"
         v-if="orderStatus != 3">
      <el-button type="primary"
                 :disabled="btnDis"
                 @click="next(orderS)">{{btnVal}}</el-button>
    </div>
    <div class="shop_address_edit"
         v-if="orderStatus == 2">
      <div class="tip">
        <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F41%2F16%2F99573d2cce230db.jpg&refer=http%3A%2F%2Fku.90sjimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1611905411&t=2cccd9a668c9aa7d2ffa3f09d5cc7b23"
             alt="">
        <p></p>

        <el-button type="success"
                   @click="Reset">重新申请</el-button>
      </div>
    </div>
    <van-popup v-model="isOpenLoanBox"
               position="bottom">
      <van-picker show-toolbar
                  :columns="loanBox"
                  @cancel="isOpenLoanBox = false"
                  @confirm="onChooseLoan"
                  :confirm-button-text="$t('m.Personal.Center23')"
                  :cancel-button-text="$t('m.Personal.Center24')" />
    </van-popup> -->
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
      // amountList: [],
      // loanid: 0,
      // loanName: '',
      // isOpenLoanBox: false,
      // loanBox: [],
      defaultActive: 0,
      pay_money: 100,
      loan_name: 'oneLoan',
      pay_list: [
        { loan_name: 'oneLoan', money: 100 },
        { loan_name: 'twoLoan', money: 200 },
        { loan_name: 'threeLoan', money: 300 },
      ],
      // loan_mount: 0.00,
      // daily_interest: 0.00,
      // days: 1,
      // orderid: '',
      // orderStatus: '',
      // btnVal: this.$t('m.loanFour.loanFour7'),
      // orderS: 0, // 控制点击下一步/支付按钮不一样的事件
      btnDis: true
    }
  },
  methods: {
    chooseLoan (loan, index) {
      this.pay_money = loan.money;
      this.loan_name = loan.loan_name;
      this.defaultActive = index;
    },
    pay () {
      console.log(this.btnDis)
      this.$api.Post('submitloanpay', { loanname: this.loan_name, money: this.pay_money }).then(res => {
        if (res.status == 1) {
          location.href = res.result.loan.payurl;
        } else {
          this.$toast(res.msg)
        }
      })
    },
    selectloanorderstatus () {
      this.$api.Post('selectloanorderstatus').then(res => {
        if (res.status == 1) {
          if (res.result.loan.status == 0) {
            this.btnDis = false;
            return
          } else if (res.result.loan.status == -1) {
            return
          } else {
            this.$api.Post('nextloan').then((res) => {
              if (res.status == 1) {
                return
              } else {
                return
              }
            })
            if (res.result.loan.status == 2) {
              this.$router.push({ name: 'index' })
            } else {
              this.$emit('changeActive', { displayorder: '4', active: 'loan_six' })
            }
          }
        }
      })
    }
    // getAmountList () {
    //   if (this.orderStatus != 1) {
    //     this.$api.Post('getAmountList').then(res => {
    //       if (res.status == 1) {
    //         for (let i = 0; i < res.result.list.length; i++) {
    //           let obj = {};
    //           obj.text = res.result.list[i].loan_name;
    //           obj.value = res.result.list[i].id;
    //           this.loanBox.push(obj);
    //         }
    //         this.amountList = res.result.list;
    //       } else {
    //         this.$toast(res.msg);
    //       }
    //     })
    //   }
    // },
    // chooseLoan () {
    //   this.isOpenLoanBox = true;
    // },
    // onChooseLoan (e) {
    //   this.loanid = e.value;
    //   this.loanName = e.text;
    //   this.isOpenLoanBox = false;
    // },
    // getOrderStatus () {
    //   this.$api.Post('getOrderStatus').then(res => {
    //     if (res.status == 1) {
    //       this.orderStatus = res.result.loan.orderstatus;
    //       if (this.orderStatus == 0) {
    //         this.loanid = res.result.loan.loanid;
    //         this.pay_money = res.result.loan.pay_money;
    //         this.loan_mount = res.result.loan.loan_mount;
    //         this.daily_interest = res.result.loan.daily_interest;
    //         this.days = res.result.loan.days;
    //         this.loanName = res.result.loan.loan_name;
    //         this.btnDis = true;
    //         this.btnVal = this.$t('m.loanFour.loanFour8');
    //         this.displayorder = res.result.loan.displayorder;
    //       } else if (this.orderStatus == 1) {
    //         this.loanid = res.result.loan.loanid;
    //         this.pay_money = res.result.loan.pay_money;
    //         this.loan_mount = res.result.loan.loan_mount;
    //         this.daily_interest = res.result.loan.daily_interest;
    //         this.days = res.result.loan.days;
    //         this.loanName = res.result.loan.loan_name;
    //         this.btnDis = true;
    //         this.btnVal = this.$t('m.loanFour.loanFour8');
    //         this.displayorder = res.result.loan.displayorder;
    //         this.btnDis = false;
    //         this.btnVal = this.$t('m.loanFour.loanFour9')
    //         this.orderS = 1;
    //       }
    //     } else {
    //       this.$toast(res.msg)
    //     }
    //   })
    // },
    // Reset () {
    //   this.$api.Post('backOne').then(res => {
    //     if (res.status == 1) {
    //       this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
    //     } else {
    //       this.$toast(res.msg)
    //     }
    //   })
    // },
    // next (orderS) {
    //   if (this.loanid === 0) {
    //     this.$toast(this.$t('m.loanFour.loanFour2'))
    //     setTimeout(() => { this.isOpenLoanBox = true }, 500)
    //     return
    //   }
    //   if (orderS == 0) {
    //     this.$api.Post('subLoanFour', { loanid: this.loanid, displayorder: this.displayorder }).then(res => {
    //       if (res.status == 1) {
    //         this.orderid = res.result.loan.orderid;
    //         this.btnDis = true;
    //         this.$router.push({ name: 'index' })
    //       } else {
    //         this.$toast(res.msg)
    //       }
    //     })
    //   } else if (orderS == 1) {
    //     this.$api.Post('submitloanfourconfirm', { displayorder: this.displayorder }).then(res => {
    //       if (res.status == 1) {
    //         this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
    //       } else {
    //         this.$toast(res.msg)
    //       }
    //     })
    //   }


    // }
  },
  created () {
    // this.loanid = 0;
    // this.getOrderStatus();

    // this.getAmountList();
  },
  watch: {
    loanid () {
      for (let i = 0; i < this.amountList.length; i++) {
        let obj = {};
        if (this.amountList[i].id == this.loanid) {
          this.pay_money = this.amountList[i].pay_money;
          this.loan_mount = this.amountList[i].loan_mount;
          this.daily_interest = this.amountList[i].daily_interest + '%';
          this.days = this.amountList[i].days;
        }
      }
    }
  },
  mounted () {
    this.selectloanorderstatus()

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
.payment {
  background: #fff;
  box-shadow: 0 0 10px #cfe6ff;
  border:1px solid #fff;
  margin: 10px;
  padding: 10px;
}
.payment .noticesBox .van-notice-bar{
  border-radius: 10px;
}
.payment .boxs{
  margin: 20px auto;
}
.payment .box {
  display: inline-block;
  background: #f7f7f7;
  border-radius: 10px;
  text-align: center;
  width: 48%;
  padding: 8px 3px;
}
.payment p{
  color: #999;
}
.payment .box h2{
  color: #1a73e7;
}
.payment .tips{
  background: url("../../assets/tips.png") no-repeat 0 center;
  padding-left: 28px;
  font-size: 14px;
  margin: 10px auto;
}
.loanlist{
  margin:10px;
  padding-bottom: 20px;
}
.loanlist h4 {
  line-height: 30px;
}
.loanbox{
  background: #fff;
  border: 2px #fff solid;
  border-radius: 10px;
  padding:10px 15px;
  margin-bottom: 10px;
}
.loanbox h4, .loanfoot h2{
  color:#f2c866;
}
.loanbox span {
  font-size: 14px;
  margin-right: 20px;
}
.loanbox.act{
  background: #eff2f7;
  border: 2px #188af5 solid;
  position: relative;
}
.loanbox.act i{
  position: absolute;
  top: 0;
  right: 0;
  width: 40px;
  height: 30px;
  background: #188af5 url("../../assets/selected.png") no-repeat 15px 5px;
  border-radius: 0px 6px 0px 30px;
}
.loanfoot{
  background: #fff;
  border-radius: 20px 20px 0 0;
  width: 100%;
  padding: 20px;
}
.loanfoot div{
  display: inline-block;
}
.loanfoot .lt{
  width: 80%;
}
.loanfoot .rt button{
  border-radius: 20px !important;
}
</style>