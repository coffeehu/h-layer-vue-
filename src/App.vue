<template>
  <div id="app">
    <img src="./assets/logo.png" width="100" height="100">
    <HelloWorld/>
    
    <div class="module-wrapper root-module">
      <h1>Message</h1>
      <div class="module-wrapper">
        <button @click="showMessage">默认</button>
        <button @click="showMessageSuccess">success</button>
        <button @click="showMessageHelp">help</button>
        <button @click="showMessageWarn">warn</button>
        <button @click="showMessageError">error</button>
        <button @click="showMessageNoIcon">无图标</button>
      </div>
      <div class="module-wrapper">
        <button @click="showMessageClose">显示关闭按钮</button>
        <button @click="showMessageNotClose">不会自动关闭</button>
      </div>
      <div class="module-wrapper">
        <button @click="showMessageTextCenter">文本居中</button>
        <button @click="showMessageCenter">位置居中</button>
        <button @click="showMessageBottom">位置靠底</button>
      </div>
      <button @click="closeMessage">close</button>
    </div>

    <div class="module-wrapper root-module">
      <h1>Notification</h1>
      <div class="module-wrapper">
        <button @click="showNotification">默认</button>
        <button @click="showNotificationInfo">info</button>
        <button @click="showNotificationSuccess">success</button>
        <button @click="showNotificationHelp">help</button>
        <button @click="showNotificationWarn">warn</button>
        <button @click="showNotificationError">error</button>
      </div>
      <div class="module-wrapper">
        <button @click="showNotificationBottomRight">右下</button>
        <button @click="showNotificationBottomLeft">左下</button>
        <button @click="showNotificationTopLeft">左上</button>
        <button @click="showNotificationOffset">垂直偏移</button>
      </div>
      <div class="module-wrapper">
        <button @click="showNotificationNoClose">不显示关闭按钮</button>
      </div>
      <button @click="closeNotification">close</button>
    </div>

    <div class="module-wrapper root-module">
      <h1>MessageBox</h1>

      <div class="module-wrapper" style="border-color:#a8def5">
        <h1>alert</h1>
        <div class="module-wrapper">
          <button @click="msgboxAlert">alert-默认</button>
          <button @click="msgboxAlertInfo">alert-info</button>
          <button @click="msgboxAlertSuccess">alert-success</button>
          <button @click="msgboxAlertHelp">alert-help</button>
          <button @click="msgboxAlertWarn">alert-warn</button>
          <button @click="msgboxAlertError">alert-error</button>
        </div>
        <div class="module-wrapper">
          <button @click="msgboxAlertCenter">alert-文本居中</button>
          <button @click="msgboxAlertCenterIcon">alert-文本居中带图标</button>
        </div>
      </div>

      <div class="module-wrapper" style="border-color:pink">
        <h1>confirm</h1>
        <div class="module-wrapper">
          <button @click="msgboxConfirm">confirm-默认</button>
          <button @click="msgboxConfirmNoLock">confirm-不锁滚动条</button>
          <p class="tips">和 alert 的区别只是多了一个 cancel 按钮</p>
        </div>
      </div>
    </div>

    <div class="module-wrapper root-module fixed-btn">
      <h1>tooltip</h1>
      <div class="box">
        <div class="top">
          <h-tooltip content="ni hao ma?" placement="top">
            <button>top</button>
          </h-tooltip>
        </div>
        <div class="left">
          <h-tooltip content="ni hao ma?" placement="left">
            <button>left</button>
          </h-tooltip>
        </div>
        <div class="right">
          <h-tooltip content="ni hao ma?" placement="right">
            <button>right</button>
          </h-tooltip>
        </div>
        <div class="bottom">
          <h-tooltip content="ni hao ma?" placement="bottom">
            <button>bottom</button>
          </h-tooltip>
        </div>
      </div>
    </div>

    <div class="module-wrapper root-module loading-module">
      <h1>loading</h1>
      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px" v-loading="loading1"></div>
        <button @click="toggle1">默认</button>  
      </div>

      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px" v-loading="loading2" h-loading-type="2"></div>
        <button @click="toggle2">载入动画type=2</button>  
      </div>

      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px"
         v-loading="loading3" 
         h-loading-type="3"></div>
        <button @click="toggle3">载入动画type=3</button>  
      </div>

      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px" v-loading.fullscreen="loading4"></div>
        <div  v-loading.fullscreen.lock="loading5"></div>
        <button @click="toggle4" style="font-size:1vw;padding:10px 2px">fullscreen</button>
        <button @click="toggle5" style="font-size:1vw;padding:10px 2px">lockscroll</button>
      </div>

      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px"
         v-loading="loading6"
         h-loading-text="拼命加载中"></div>
        <button @click="toggle6">文字1</button>  
      </div>

      <div>
        <div style="background:pink;width:100%;height:200px;margin-bottom:20px"
         v-loading="loading7"
         h-loading-text="拼命加载中"
         h-loading-text-type="horizontal"
         h-loading-type="3"></div>
        <button @click="toggle7">文字2</button>  
      </div>

    </div>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Message from './packages/message'
import Notification from './packages/notification'
import MessageBox from './packages/message-box'
import './assets/h-ui.css'

export default {
  name: 'App',
  data() {
    return {
      loading1: false,
      loading2: false,
      loading3: false,
      loading4: false,
      loading5: false,
      loading6: false,
      loading7: false,
    }
  },
  components: {
    HelloWorld
  },
  methods: {
    /*-----------------Message-----------------*/
    showMessage() {
       Message({
        message: 'hello',
      });
    },
    showMessageSuccess() {
       Message.success('hello');
    },
    showMessageHelp() {
       Message.help('hello');
    },
    showMessageWarn() {
       Message.warn('hello');
    },
    showMessageError() {
       Message.error('hello');
    },
    showMessageClose() {
       Message({
        message: 'hello',
        showClose: true
       })
    },
    showMessageNotClose() {
       Message({
        message: 'hello',
        showClose: true,
        duration: 0
       })
    },
    showMessageNoIcon() {
       Message({
        message: 'hello',
        iconClass: true
       });
    },
    showMessageTextCenter() {
       Message({
        message: 'hello',
        center: true,
        showClose: true
      });
    },
    showMessageCenter() {
       Message({
        message: 'hello',
        position: 'center',
        showClose: true
      });
    },
    showMessageBottom() {
       Message({
        message: 'hello',
        position: 'bottom',
        showClose: true
      });
    },
    closeMessage() {
      Message.closeAll();
    },

    /*-----------------Notification-----------------*/
    showNotification() {
      Notification({
        title:'info',
        message:'hello'
      })
    },
    showNotificationInfo() {
      Notification.info({
        title:'info',
        message:'hello',
      })
    },
    showNotificationSuccess() {
      Notification.success({
        title:'info',
        message:'hello',
      })
    },
    showNotificationHelp() {
      Notification.help({
        title:'info',
        message:'hello',
      })
    },
    showNotificationWarn() {
      Notification.warn({
        title:'info',
        message:'hello',
      })
    },
    showNotificationError() {
      Notification.error({
        title:'info',
        message:'hello',
      })
    },
    showNotificationBottomLeft() {
      Notification({
        title:'info',
        message:'hello',
        type: 'success',
        position: 'bottom-left'
      })
    },
    showNotificationBottomRight() {
      Notification({
        title:'info',
        message:'hello',
        type: 'success',
        position: 'bottom-right'
      })
    },
    showNotificationTopLeft() {
      Notification({
        title:'info',
        message:'hello',
        type: 'success',
        position: 'top-left'
      })
    },
    showNotificationNoClose() {
      Notification({
        title:'info',
        message:'hello',
        showClose: false
      })
    },
    showNotificationOffset() {
      Notification({
        title:'info',
        message:'hello',
        type: 'success',
        offset: 200
      })
    },
    closeNotification() {
      Notification.closeAll();
    },

    /*-----------------MessageBox-----------------*/
    msgboxAlert() {
      MessageBox.alert('hello', 'title', {
        confirmButtonText: '确定',
      })
    },
    msgboxAlertInfo() {
      MessageBox.alert('hello', 'title', {
        type: 'info',
        confirmButtonText: '确定',
        beforeClose: function(instance, close){
          console.log('beforeClose', instance);
          close();
        }
      });
    },
    msgboxAlertHelp() {
      MessageBox.alert('hello', 'title', {
        type: 'help',
        confirmButtonText: '确定'
      });
    },
    msgboxAlertSuccess() {
      MessageBox.alert('hello', 'title', {
        type: 'success',
        confirmButtonText: '确定'
      });
    },
    msgboxAlertWarn() {
      MessageBox.alert('hello', 'title', {
        type: 'warn',
        confirmButtonText: '确定'
      });
    },
    msgboxAlertError() {
      MessageBox.alert('hello', 'title', {
        type: 'error',
        confirmButtonText: '确定'
      });
    },
    msgboxAlertCenter() {
      MessageBox.alert('hello', 'title', {
        center: true,
        confirmButtonText: '确定'
      });
    },
    msgboxAlertCenterIcon() {
      MessageBox.alert('hello', 'title', {
        type: 'success',
        center: true,
        confirmButtonText: '确定'
      });
    },
    msgboxConfirm() {
      MessageBox.confirm('hello', 'title', {
        confirmButtonText: '确定',
        cancelButtonText: '取消'
      }).then(() => {
        Message.success('确定');
      }).catch(() => {
        Message.info('取消');
      })
    },
    msgboxConfirmNoLock(){
      MessageBox.confirm('hello', 'title', {
        confirmButtonText: 'confirm',
        cancelButtonText: 'cancel',
        lockScroll: false
      }).then(() => {
        Message.success({
          message: 'confirm',
          showClose: true
        });
      }).catch(() => {
        Message.info({
          message: 'cancel',
          showClose: true
        });
      })
    },


    toggle1() {
      this.loading1 = !this.loading1;
    },
    toggle2() {
      this.loading2 = !this.loading2;
    },
    toggle3() {
      this.loading3 = !this.loading3;
    },
    toggle4() {
      this.loading4 = !this.loading4;
      setTimeout(() => {
        if(this.loading4) this.loading4 = false;
      }, 1500);
    },
    toggle5() {
      this.loading5 = !this.loading5;
      setTimeout(() => {
        if(this.loading5) this.loading5 = false;
      }, 1500);
    },
    toggle6() {
      this.loading6 = !this.loading6;
    },
    toggle7() {
      this.loading7 = !this.loading7;
    },


  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
#app h1 {
  margin: 0;
  padding: 0;
  margin-bottom: 20px;
}
.module-wrapper {
  border: 1px solid #e2e2e2;
  padding: 20px 5px;
  margin: 10px 30px;
}
.root-module {
  width: 60%;
  margin-left: 50%;
  margin-bottom: 50px;
  transform: translateX(-50%);
  border-color: #c4c4c4;
}
.module-wrapper button {
  line-height: 1.3;
  padding: 10px 15px;
  border: 1px solid #c4c4c4;
  outline: none;
  background: #e2e2e2;
  cursor: pointer;
}
.module-wrapper button:hover {
  color: #666;
}
.fixed-btn button {
  width: 80px;
}
#app .module-wrapper h1 {
  text-align: left;
  padding-left: 30px;
  font-size: 26px;
}
#app .root-module > h1 {
  text-align: center;
  font-size: 30px;
}
.tips {
  font-size: 12px;
  color: #666;
}
.module-wrapper .box {
  box-sizing: border-box;
  width: 200px;
  margin: auto;
}
.module-wrapper .top {
  margin-bottom: 20px;
} 
.module-wrapper .left {
  float: left;
}
.module-wrapper .right {
  float: right;
  margin-bottom: 20px;
}
.module-wrapper .bottom {
 clear: both;
}

.loading-module > div {
  display: inline-block;
  width:40%;
  padding:20px 20px 0;
  box-sizing:border-box;
}
</style>
