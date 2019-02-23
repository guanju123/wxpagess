<template>
  <div class="container">
<!-- :src="userInfo.avatarUrl" -->
  <div class="userinfo">
    <img class="userinfo-avatar"  background-size="cover" />
    <span class="userinfo-nickname"></span>
    <img src="/static/images/note-actived.png" class="account-bg"/>

  </div>

  <div class="separate"></div>

  <div class="order" catchtap="toOrder">
    <span class="myorder-span">我的订单</span>
    <span class="myorderlook-span">查看全部订单</span>
    <img class="next-img" src="/static/images/note-actived.png"/>
  </div>
  <div class="line"></div>

  <div class="navs">
    <block v-for="item in orderItems" :key="item.name">
      <div class="nav-item" catchtap="toOrder" data-type="item.name" data-typeid="item.typeId">
        <img :src="item.imgurl" class="nav-img" />
        <span>{{item.name}}</span>
      </div>
    </block>
  </div>

  <div class="separate"></div>
  <div class="person-list">
    <div class="list-item">
      <img class="item-img" src="/static/images/note-actived.png"/>
      <span class="item-span">我的收藏</span>
    </div>
    <div class="person-line"></div>
    <div class="list-item">
      <img class="item-img" src="/static/images/note-actived.png"/>
      <span class="item-span">收货地址</span>
    </div>
    <div class="person-line"></div>
    <div class="list-item">
      <img class="item-img" src="/static/images/note-actived.png"/>
      <span class="item-span">售后记录</span>
    </div>
    <div class="person-line"></div>
    <div class="list-item">
      <img class="item-img" src="/static/images/note-actived.png"/>
      <span class="item-span">我的评价</span>
    </div>
    <div class="person-line"></div>
    <div class="list-item">
      <img class="item-img" src="/static/images/note-actived.png"/>
      <span class="item-span">推广邀请</span>
    </div>
  </div>
  <div class="separate"></div>
</div>

</template>

<script>

export default {
  data () {
    return {
      orderItems: [
      {
        typeId: 0,
        name: '待付款',
        url: 'bill',
        imageurl: '/static/images/note-actived.png',
      },
      {
        typeId: 1,
        name: '待发货',
        url: 'bill',
        imageurl: '/static/images/note-actived.png',
      },
      {
        typeId: 2,
        name: '待收货',
        url: 'bill',
        imageurl: '/static/images/note-actived.png'
      },
      {
        typeId: 3,
        name: '待评价',
        url: 'bill',
        imageurl: '/static/images/note-actived.png'
      }
    ]
    }
  },

  components: {
  },

  methods: {

  },

  created () {
    // let app = getApp() 抓
  },
   //事件处理函数
  toOrder: function () {
    mpvue.navigateTo({
      url: '../profile/main'
    })
  },
  onLoad: function () {
    // console.log('onLoad')
    var that = this
    //调用应用实例的方法获取全局数据
      that.getUserInfo(function (userInfo) {
      console.log(getUserInfo)
      //更新数据
      // that.setData({
      //   userInfo: userInfo
      // })
      that.userInfo = userInfo
    })
  }

}
</script>

<style scoped>
   .userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #f0145a;
}
.account-bg {
  width: 100%;
  height: 150rpx;
}
.userinfo-avatar {
  width: 108rpx;
  height: 108rpx;
  margin: 20rpx;
  border-radius: 50%;
}
.userinfo-nickname {
  color: #fff;
}
/* 订单 */
.order {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
  height: 90rpx;
}
.myorder-span {
  font-size: 30rpx;
  color: gray;
  margin: 20rpx;
  width: 40%;
}
.myorderlook-span {
  font-size: 30rpx;
  color: gray;
  position: relative;
  right: 20rpx;
  width: 60%;
  span-align: right;
}
.next-img {
  width: 20rpx;
  height: 25rpx;
  position: relative;
  right: 10rpx;
}
.navs {
  display: flex;
}
.nav-item {
  width: 25%;
  display: flex;
  align-items: center;
  flex-direction: column;
  padding: 20rpx;
}
.nav-item .nav-img {
  width: 40rpx;
  height: 40rpx;
  margin: 5rpx;
}
.nav-item span {
  margin-top: 20rpx;
  font-size: 25rpx;
  color: gray;
}
/* 列表 */
.person-list {
  display: flex;
  flex-direction: column;
  align-items: left;
}
.list-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 80rpx;
}
.item-img {
  width: 40rpx;
  height: 40rpx;
  margin: 20rpx;
}
.item-span {
  color: gray;
  font-size: 25rpx;
  margin-left: 20rpx;
}
.person-line {
  width: 100%;
  height: 2rpx;
  background: lightgray;
  margin-left: 90rpx;
}

</style>
