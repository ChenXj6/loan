<template>
  <div class="perback">
    <!-- 轮播 -->
    <div>
      <div class="van-nav-bar van-hairline--bottom"
           style="z-index: 1;">
        <div class="van-nav-bar__left"></div>
        <div class="van-nav-bar__title van-ellipsis">{{$t('m.Homepage.home1')}}</div>
        <div class="van-nav-bar__right"></div>
      </div>
    </div>
    <!-- 宣传栏 -->
    <div>
      <van-swipe class="my-swipe"
                 :autoplay="3000"
                 indicator-color="white">
        <van-swipe-item v-for="(item,index) in indexdata.advs"
                        :key="index">
          <img :src="item.thumb"
               alt
               srcset />
        </van-swipe-item>
      </van-swipe>
    </div>
    <!-- 公告  -->
    <div class="noticesBox">
      <van-notice-bar left-icon="volume-o"
                      :scrollable="false"
                      style="height: 1rem;">
        <van-swipe vertical
                   class="notice-swipe"
                   :autoplay="3000"
                   :show-indicators="false">
          <van-swipe-item v-for="(item,index) in indexdata.notices"
                          :key="index">
            {{item.title}}
          </van-swipe-item>
        </van-swipe>
      </van-notice-bar>
    </div>
    <!-- 四个板块 -->
    <div class="p10 mt_do">
      <ul class="f-jc-sb plate4">
        <li @click="module(1)">
          <img src="../../assets/Money.png" />
          <p>{{$t('m.Homepage.home2')}}</p>
        </li>
        <li @click="module(3)">
          <img src="../../assets/course.png" />
          <p>{{$t('m.Homepage.home16')}}</p>
        </li>
        <li @click="module(2)">
          <img src="../../assets/friends.png" />
          <p>{{$t('m.Homepage.home3')}}</p>
        </li>
        <li @click="module(4)">
          <img src="../../assets/service.png" />
          <p>{{$t('m.Homepage.home5')}}</p>
        </li>
      </ul>
    </div>
    <!-- 任务 -->
    <!-- <div class="taskp">
      <div class="van-notice-bar title">VIP Level</div>
      <div class="f-flex task">
        <p @click="task(item.id)"
           v-for="(item,index) in tasklist_grade"
           :key="index">
          <img src="../../assets/vip1.png"
               alt />{{item.title}}
        </p>
      </div>

    </div> -->
    <!-- 列表 -->
    <div class="zylist">
      <van-list v-model="loading"
                :finished="finished"
                :finished-text="$t('m.Homepage.home6')"
                :loading-text="$t('m.mission.mission21')"
                @load="onLoad">
        <div class="f-flex zyitem"
             v-for="(item,index) in tasklist" @click="newdetail(item.id)"
             :key="index">
          <div>
            <!-- <img  src="../../assets/Tiktok.png" alt=""/> -->
            <img :src="item.thumb" :alt="item.newtitle"/>
            
        </div>
        <div>
          <p><span>{{item.newtitle}}</span></p>
          <p><span>{{item.thistime}}</span></p>
        </div>
        </div>
      </van-list>
    </div>
    <!-- 领取任务弹窗 -->
    <!-- <van-dialog v-model="xinx"
                show-cancel-button
                @confirm="confirms"
                :confirmButtonText="$t('m.Personal.Center23')"
                :cancelButtonText="$t('m.Personal.Center24')">
      <div class="xinx">
        <p class="renwu_color">
          <van-icon name="question" /> {{$t('m.Homepage.home12')}}
        </p>
      </div>
    </van-dialog> -->
    <div style="width:100%;height:50px"></div>
    <Foot></Foot>
    <!-- 首次进入展示框 -->
    <div class="firstMesBox" v-if="$store.state.firstMes">
      <h1>{{$t('m.firstMes.firstMesTitle')}}</h1>
      <div class="firstMesCon" v-html="firstMessage.content">{{firstMessage.content}}</div>
      <img class="firstMesBtn" src="../../assets/close.png" alt="" @click="$store.state.firstMes = false">
      <img class="firstMesClose" src="../../assets/close.png" alt="" @click="$store.state.firstMes = false">
    </div>
  </div>
</template>

<script>
  import Foot from '@/components/index/footer'
export default {
  data () {
    return {
      indexdata: "",
      images: [],
      tasklist: [],
      tasklist_grade: [],
      page: 1,
      grade: "",
      loading: false,
      finished: false,
      money: "",
      xinx: false,
      id: '',
      dy: require('../../assets/Tiktok.png'),
      ks: require('../../assets/Zantine.png'),
      // host:process.env.NODE_ENV=='development'?'http://7230.iiio.top':`${location.protocol}//${location.host}`
      host: 'https://app.indianbicycles.in',
      firstMessage:''
    };
  },
  components:{
    Foot
  },
  mounted () {
  },
  created () {
    this.main();
    this.newset();
    this.getFirstMes();
  },
  methods: {
    // 获取首次进入
    getFirstMes(){
      this.$api.Post("firstMes").then(res => {
        if (res.status == 1) {
          this.firstMessage = res.result.result;
        }
      });
    },
    //四个板块
    module (e) {
      if (e == 1) {
        this.$router.push({ name: "release" });
      }
      if (e == 2) {
        var language = window.localStorage.getItem('language');
        var lang;
        if (language == "" || language == "en-US" || language == 'en') {
          lang = "en"
        } else {
          lang = "cn"
        }
        let isLogin = this.getCookie3('openid') || false;
        if(isLogin == false){
          setTimeout(()=>this.$router.push({path:'/login'}),1000)
         }else{
           location.href = `${this.host}/app/index.php?i=4&c=entry&method=shares&app=goods&p=commission&m=sz_yi&do=plugin&lang=` + lang
         }
      }
      if (e == 3) {
        this.$router.push({ name: "course" });
      }
      if (e == 4) {
        this.$api.Post("service").then(res => {
          if (res.status == 1) {
            location.href = res.result;
          }
        });
      }
    },
    // 新闻点击详情
    newdetail(id){
      this.$router.push({name:'detail',query:{id:id}})
    },
    // 公告
    main () {
      this.$api.Post("main").then(res => {
        if (res.status == 1) {
          this.indexdata = res.result;
        }
      });
    },
    // 获取列表
    newset () {
      this.$api
        .Post("newset", {
          page: this.page,
          psize: 10
        })
        .then(res => {
          if (res.status == 1) {
            this.tasklist = res.result.newset;
          }
        });
    },
    onLoad () {
      // 异步更新数据
        this.page++;
        this.$api.Post("newset", {
            page: this.page,
            psize: 10
          })
          .then(res => {
            if (res.status == 1) {
              this.tasklist = this.tasklist.concat(res.result.newset);
              // 数据全部加载完成
              if (res.result.newset.length < 10) {
                this.finished = true;
              }
            }
          });
        // 加载状态结束
        this.loading = false;
    }
  }
};
</script>

<style lang="less">
.task {
  flex-wrap: wrap;
}
.task p {
  width: 49%;
  padding: 10px 0;
  margin: 0.1rem 0.5% 0;
  background-color: #1e243d;
  border-radius: 0.16667rem;
}
.mt_do {
  padding: 0.1rem !important;
}
.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  line-height: 160px;
  text-align: center;
  //   background-color: #39a9ed;
}
.my-swipe img {
  width: 100%;
}
.plate4 {
  > li {
    display: inline-block;
    width: 48%;
    text-align: center;
    background-color: #ffffff;
    color: #666666;
    padding: 0.3rem 0;
    margin:1%;
    font-weight: bold;
   border-radius: 0.16667rem;
    img {
      float: right;
      width: 48px;
    }
    p{
      padding: 6px 10px;
      line-height: 18px;
      text-align: left;
    }
  }
}
.task {
  > p {
    text-align: center;
    &:first-child {
    }
    img {
      width: 32px;
      margin-right: 20px;
    }
  }
}
.zyitem {
  padding: 10px;
  position: relative;
  background: #ffffff;
  border-bottom: 1px #eeeeee solid;
  > div:nth-child(1) {
    width: 20%;
    margin-right: 10px;
    span {
      position: absolute;
      left: 0;
      top: 0;
      color: #1989fa;
      border-radius: 12px 0 0 0 !important;
      padding: 5px 0 3px 10px;
      font-size: 12px;
      border-radius: 4px 0 0 0;
    }
  }
  >div:nth-child(2){
    width: 80%;
    padding: 10px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    font-size: 14px;
    >p:nth-child(1){
      max-height: 80%;
      line-height: 16px;
      display: -webkit-box;
      overflow: hidden;
      text-overflow: ellipsis;
      -webkit-box-orient:vertical;
      -webkit-line-clamp:3;
      font-weight: 600;
    }
    >p:nth-child(2){
      max-height: 20%;
      >span{
        color: #999999;
      }
    }
  }
  img {
    width: 50px;
    position: absolute;
    top: 50%;
    transform:translateY(-50%)
  }
}
.el-button--primary {
  background: #e7f0fe !important;
  border: 0 !important;
  color: #1a73e7 !important;
}
.renwu_color {
  color: #000;
}
.van-ellipsis > .notice-swipe {
  width: 352px;
  height: 0.64rem;
}
.firstMesBox{
  width: 80%;
  height: 450px;
  // overflow: auto;
  min-height: 60%;
  position: fixed;
  left: 10%;
  top:10%;
  background: #fff;
  box-shadow: 1px 1px 10px #3b3838;
  // background-repeat: no-repeat;
  // background-size: cover;
  box-sizing: border-box;
  border-radius: 5px;
  padding: 0 20px;
}
.firstMesBox>h1{
  text-align: center;
  margin: 10px 0;
  height: 30px;
  // color: #fff;
}
.firstMesBox>.firstMesCon{
  height: 380px;
  overflow: auto;
  scrollbar-width: none; /* Firefox */
  -ms-overflow-style: none; /* IE 10+ */
}
  ::-webkit-scrollbar {
  display: none; /* Chrome Safari */
  }
.firstMesBox>.firstMesBtn{
  display: block;
  width: 50px;
  height: 50px;
  position: absolute;
  left: 50%;
  bottom: -100px;
  transform: translate(-50%,-50%);
}
.firstMesBox>.firstMesClose{
  position: absolute;
  top:17px;
  right: 10px;
  display: block;
  width: 20px;
  height: 20px;
}
</style>
