<template>
  <div id="shop_address_edit">
    <!--身份证上传-->
    <h3>{{$t('m.loanThree.loanThree1')}}</h3>
    <div id="uploaderID">
      <div class="uploaderBox">
        <van-uploader v-model="fileList"
                      multiple
                      :max-count="1"
                      :after-read="afterRead"
                      :upload-text="$t('m.loanThree.loanThree2')" />
      </div>
      <!-- @delete="deleteAxiosimg" -->
      <!-- <div class="uploaderBox">
        <van-uploader v-model="sfzfileListfm"
                      multiple
                      :max-count="1"
                      :after-read="afterRead"
                      upload-text="身份证反面" />
      </div> -->
    </div>
    <div class="with-btn">
      <el-button type="primary"
                :disabled="btnDis"
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
      fileList: [],
      sfzfileListzm: [],//身份证正面
      sfzfileListfm: [],//身份证反面
      img:'',
      displayorder: this.dis,
      btnDis:true,
    }
  },
  methods: {
    afterRead (file1) {
      // 此时可以自行将文件上传至服务器
      this.$api.Post('uploader', { file: file1.file }).then(res => {
        this.img = res.result;
        this.btnDis = false;
      })
    },
    next () {
      if (this.img == '') {
        this.$toast(this.$t('m.Submit.task13'))
        return
      }
      this.$api.Post('subLoanThree', { img: this.img, displayorder: this.displayorder }).then(res => {
        if (res.status == 1) {
          this.$emit('changeActive', { displayorder: res.result.loan.displayorder, active: res.result.loan.loanname })
        }else{
          this.$toast(res.msg)
        }
      })
    },
  },
  mounted () {

  }
}
</script>
<style scoped>
#uploaderID {
  display: flex;
  margin-top: 10px;
  margin-left: 10px;
}
</style>
<style>
#uploaderID .uploaderBox {
  width: 50%;
}
#uploaderID .van-uploader__preview-image {
  width: 100% !important;
  height: 150px !important;
}
#uploaderID .van-uploader__upload {
  width: 100% !important;
  height: 150px !important;
}
#uploaderID .van-uploader {
  width: 100%;
}
#uploaderID .van-uploader__input {
  height: 100%;
  width: 100%;
}
#shop_address_edit .van-address-edit__buttons {
  position: absolute;
  bottom: 100px;
  width: 100%;
}
h3{
  width: 100%;
  margin: 10px 0 20px;
  padding: 0 10px 10px;
  border-bottom: 1px #333 dashed;
}
</style>
