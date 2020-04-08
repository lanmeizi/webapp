<template>
  <div id="Home" class="pageContainer">
    <div class="loginBox">
      <div class="logo">
        <van-image
          round
          width="30"
          height="30"
          src="https://img.yzcdn.cn/vant/cat.jpeg"
        />
        <p>logo图片众智云擎</p>
      </div>
      <p class="login">
        <span class="word">登录</span>
        <span class="word">申请试用</span>
      </p>
    </div>
    <div class="navBox">
      <van-tabs v-model="activeName" @click="changeTabs">
        <van-tab name="a">
          <template #title>
            <van-dropdown-menu>
              <van-dropdown-item v-model="value1" :options="option1" @change="changeOneItem" />
            </van-dropdown-menu>
          </template>
          <div v-if="showItem === 0">
            <div class="cell" v-for="list in lists" :key="list.id">
              <p class="word">{{ list.title }}</p>
              <p class="time">[{{ list.time }}]</p>
            </div>
          </div>
          <div v-if="showItem === 1">
            <div class="cell">111111</div>
          </div>
          <div v-if="showItem === 2">
            <div class="cell">22222</div>
          </div>
        </van-tab>
        <van-tab title="法规层级" name="b">内容 法规层级 5</van-tab>
        <van-tab title="法规分类" name="c">
          <van-popup v-model="showfaguifenlei" position="top" :style="{minHeight: '20%'}" closeable close-icon="close" :close-on-click-overlay="false">
            <van-dropdown-menu>
              <van-dropdown-item v-model="value2" :disabled="disabled2" :options="option2" @change="change2" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled2">
              <van-dropdown-item v-model="value3" :disabled="disabled3" :options="option3" @change="change3" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled3">
              <van-dropdown-item v-model="value4" :disabled="disabled4" :options="option4" @change="change4" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled4">
              <van-dropdown-item v-model="value5" :disabled="disabled5" :options="option5" @change="change5" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled5">
              <van-dropdown-item v-model="value6" :disabled="disabled6" :options="option6" @change="change6" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled6">
              <van-dropdown-item v-model="value7" :disabled="disabled7" :options="option7" @change="change7" />
            </van-dropdown-menu>
            <div class="btn"><van-button :disabled="showBackBtn"  type="info" @click="backToFrontMenu">返回</van-button></div>
          </van-popup>
          <!-- <van-popup v-model="showfaguifenlei" position="top" :style="{minHeight: '20%'}" closeable close-icon="close" :close-on-click-overlay="false">
            <van-dropdown-menu>
              <van-dropdown-item v-model="value2" :disabled="disabled2" :options="option2" @closed="change2" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled2">
              <van-dropdown-item v-model="value3" :disabled="disabled3" :options="option3" @closed="change3" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled3">
              <van-dropdown-item v-model="value4" :disabled="disabled4" :options="option4" @closed="change4" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled4">
              <van-dropdown-item v-model="value5" :disabled="disabled5" :options="option5" @closed="change5" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled5">
              <van-dropdown-item v-model="value6" :disabled="disabled6" :options="option6" @closed="change6" />
            </van-dropdown-menu>
            <van-dropdown-menu v-if="disabled6">
              <van-dropdown-item v-model="value7" :disabled="disabled7" :options="option7" @closed="change7" />
            </van-dropdown-menu>
            <div class="btn"><van-button :disabled="showBackBtn"  type="info" @click="backToFrontMenu">返回</van-button></div>
          </van-popup> -->
          <div>
            <div class="cell" v-for="list in lists" :key="list.id">
              <p class="word">{{ list.title }}</p>
              <p class="time">[{{ list.time }}]</p>
            </div>
          </div>
        </van-tab>
        <van-tab title="操作手册" name="d">内容 操作手册 3</van-tab>
        <van-tab title="演示视频" name="e">内容 演示视频 4</van-tab>
      </van-tabs>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeName: 'a',
      lists: [
        {id: 0, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 1, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 2, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 3, title: '关于《国家税务总局关于发布〈研发机构采购国产设备增值税退税管理办法〉的公告》的解读', time: '2020-3-20'},
        {id: 4, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 5, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 6, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 7, title: '关于《国家税务总局关于发布关于做好新型冠状病毒感染的肺炎疫情防控期间出口退（免）税有关工作的通知〈研发机构采购国产设备增值税退税管理办法〉的公告》的解读', time: '2020-3-20'},
        {id: 8, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 9, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'}
      ],
      lists1: [
        {id: 0, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 1, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 2, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 3, title: '关于《国家税务总局关于发布〈研发机构采购国产设备增值税退税管理办法〉的公告》的解读', time: '2020-3-20'}
      ],
      lists2: [
        {id: 0, title: '测试数据三', time: '2020-3-20'},
        {id: 1, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 2, title: '关于延长2020年4月纳税申报期限有关事项的通知', time: '2020-3-20'},
        {id: 3, title: '关于《国家税务总局关于发布〈研发机构采购国产设备增值税退税管理办法〉的公告》的解读', time: '2020-3-20'}
      ],
      homeItem: '',
      value1: 0,
      option1: [
        { text: '首页1', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value2: 0,
      option2: [
        { text: 'disabled2222', value: 0 },
        { text: '首页111222', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value3: 0,
      option3: [
        { text: 'disabled2首页33', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value4: 0,
      option4: [
        { text: 'disabled2首页44', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value5: 0,
      option5: [
        { text: 'disabled2首页555', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value6: 0,
      option6: [
        { text: 'disabled2首页666', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      value7: 0,
      option7: [
        { text: 'disabled2首页7777', value: 0 },
        { text: '首页2', value: 1 },
        { text: '首页3', value: 2 }
      ],
      showItem: 0, // 显示首页对应的选项
      showfaguifenlei: false, // 显示法规分类弹框
      showItem2: 0,
      disabled2: false,
      disabled3: false,
      disabled4: false,
      disabled5: false,
      disabled6: false,
      disabled7: false,
      showBackBtn: true
    }
  },
  mounted() {
    this.homeItem = localStorage.getItem('homeItem')
    switch(this.homeItem) {
      case '首页1':
        this.value1 = 0
        this.showItem = 0
        break
      case '首页2':
        this.value1 = 1
        this.showItem = 1
        break
      case '首页3':
        this.value1 = 2
        this.showItem = 2
        break
    }
  },
  methods: {
    // 切换首页
    changeOneItem(value) {
      this.showItem = value
    },
    // 点击tabs
    changeTabs(name, title) {
      if (name === 'c' && title === '法规分类') {
        this.showfaguifenlei = true
      }
    },
    change2(value) {
      console.log('value2==>', value)
      this.disabled2 = true
      this.showBackBtn = false
      this.showItem2 = value
      if (this.showItem2 === 1) {
        this.lists = this.lists1
      }
    },
    change3(value) {
      console.log('value3==>', value)
      this.disabled3 = true
    },
    change4(value) {
      console.log('value4==>', value)
      this.disabled4 = true
    },
    change5(value) {
      console.log('value5==>', value)
      this.disabled5 = true
    },
    change6(value) {
      console.log('value6==>', value)
      this.disabled6 = true
    },
    change7(value) {
      console.log('value7==>', value)
      this.disabled7 = true
    },
    backToFrontMenu() {
      if ((this.disabled2 && this.disabled3 && this.disabled4 && this.disabled5 && this.disabled6 && this.disabled7) || (this.disabled2 && this.disabled3 && this.disabled4 && this.disabled5 && this.disabled6 && !this.disabled7)) {
        this.disabled6 = false
        this.disabled7 = false
      } else if ((this.disabled2 && this.disabled3 && this.disabled4 && this.disabled5 && this.disabled6) || (this.disabled2 && this.disabled3 && this.disabled4 && this.disabled5 && !this.disabled6 && !this.disabled7)) {
        this.disabled5 = false
      } else if ((this.disabled2 && this.disabled3 && this.disabled4 && this.disabled5) || (this.disabled2 && this.disabled3 && this.disabled4 && !this.disabled5 && !this.disabled6 && !this.disabled7)) {
        this.disabled4 = false
      } else if ((this.disabled2 && this.disabled3 && this.disabled4) || (this.disabled2 && this.disabled3 && !this.disabled4 && !this.disabled5 && !this.disabled6 && !this.disabled7)) {
        this.disabled3 = false
      } else if ((this.disabled2 && this.disabled3) || (this.disabled2 && !this.disabled3 && !this.disabled4 && !this.disabled5 && !this.disabled6 && !this.disabled7)) {
        this.disabled2 = false
        this.showBackBtn = true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
#Home {
  .loginBox {
    height: 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 10px;
    box-sizing: border-box;
    background: #5E5E5E;
    color: #fff;
    .logo {
      font-size: 16px;
      display: flex;
      align-items: center;
    }
    .login {
      font-size: 12px;
      .word {
        margin: 0 10px;
      }
    }
  }
  .navBox {
    .cell {
      min-height: 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 12px;
      border-bottom: 1px solid #EBEBEB;
      padding: 0 4px;
      .word {
        font-weight: bold;
        flex: 1;
      }
      .time {
        color: #5E5E5E;
        width: 70px;
        margin-left: 6px;
      }
    }
    .btn {
      display: flex;
      justify-content: flex-end;
      margin: 20px 20px 20px 0;
    }
  }
}
</style>

<style>
  /* .van-tab {
    background-color: #494949;
    color: #fff;
  } */
  /* .van-tabs__line {
    background-color: orange;
  } */
  .van-tab__pane {
    padding: 0 10px;
  }
  .van-dropdown-menu {
    height: 44px;
  }
  .van-dropdown-menu__title {
    color: #646566;
    font-size: 14px;
  }
</style>
