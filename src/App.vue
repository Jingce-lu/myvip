<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
    <el-container>
      <el-header>VIP视频破解工具</el-header>
      <el-main>
        <div class="search">
          <el-input
            placeholder="请输入视频地址(支持腾讯、爱奇艺、芒果、乐视、优酷、搜狐、乐视云、58、土豆云)"
            type="text"
            max="1200"
            v-model='value'
            >
          </el-input>
    			<div class="btn">
    				<!-- <p class="start">开始解码</p><p class="clean">清除地址</p> -->
            <el-button type="primary" size="medium" @click="start">开始解码</el-button>
            <el-button type="primary" size="medium" @click="clear">清除地址</el-button>
    			</div>
    		</div>
        <div class="windows">
    			<div class="loading">
    				<div class="loading-top" v-bind:class="{toggleshow:isShow}">
    					<img src="./assets/loading.gif" />
    					<p>~~~精彩马上呈现~~~</p>
    				</div>
    				<iframe v-bind:src="url"  allowtransparency="true" frameborder="0" scrolling="no" class="video-play" id="video-play">
            </iframe>
            <!-- <iframe :src="http://api.baiyug.cn/vip/index.php?url=http://www.iqiyi.com/v_19rr7pe5k4.html!"  allowtransparency="true" frameborder="0" scrolling="no" class="video-play" id="video-play">
            </iframe> -->
    			</div>
    		</div>
      </el-main>
      <el-footer>
        <div style="text-align:center;padding: 20px">
          友情链接
        </div>
        <table border="0" align="center" cellpadding="0" cellspacing="0">
        <tr>
          <td valign="top">
            <a target="_blank" href="http://www.youku.com/" rel="nofollow"><img src="./assets/youkulogo.png" width="110" height="35"/></a><dd style="text-align:center">优酷视频</dd>
          </td>
          <td valign="top">
            <div style="margin-left:50px;">
              <a target="_blank" href="http://v.qq.com/" rel="nofollow"><img src="./assets/qqlogo.png" width="110" height="35"/></a><dd style="text-align:center">腾讯视频</dd>
            </div>
          </td>
          <td valign="top">
            <div style="margin-left:50px;">
              <a target="_blank" href="http://www.iqiyi.com/" rel="nofollow"><img src="./assets/iqiyi.png" width="110" height="35"/></a><dd style="text-align:center">爱奇艺视频</dd>
            </div>
          </td>
        </tr>
        </table>
        <br>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      value:'',
      url: '',
      isShow: false
    }
  },
  methods: {
    start(){
      const the_url = this.value;
      if (the_url=="") {
  			alert("说了要输入网址啦，你想上天么。。。。。。")
  			return
  		} else{
        // let compose_url="http://api.baiyug.cn/vip/index.php?url="+the_url+"!";
        // let compose_url="http://yun.mt2t.com/lines?url="+the_url;
        let compose_url="http://yun.mt2t.com/yun?url="+the_url;
  			console.log('compose_url = '+ compose_url);
        this.isShow = true;
        // this.url="http://api.baiyug.cn/vip/index.php?url=http://www.iqiyi.com/v_19rr7pe5k4.html!"
        this.url = compose_url;
  		};
    },
    clear(){
      this.value = ''
    }
  },
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  .el-header {
    background-color:#1e9fff;
    color: #fff;
    text-align: center;
    line-height: 60px;
  }
  .el-footer {
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-main {
    padding: 20px 0;
  }
  .search input{
  	display: block;
  	width: 50%;
  	padding: 12px;
  	border: 1px solid #009688;
  	margin: 20px auto;
  	font-size: 16px;
  }
  .el-button{
    margin: 0 30px 20px;
  }
  body > .el-container {
    margin-bottom: 40px;
  }
  .windows{
  	background-color: #e2e2e2;
  	text-align: center;
  	padding: 20px 0px;
  }
  .loading{
  	display: inline-block;
  	width: 50%;
  	height: 31vw;
  	background-color: #ffffff;
  	overflow: hidden;
  }

  .loading-top{
  	width: 100%;
  	height: 100%;
  	transition-duration: 1S;
  }
  .loading-top img{
  	margin-top: 100px;
  	width: 150px;
  	height: auto;
  }
  .loading-top p{
  	padding: 0px 25px 25px 25px;
  	font-size: 16px;
  	text-align: center;
  	color: #c2c2c2;
  }
  .toggleshow{
    height: 0;
  }
  .video-play{
  	width: 100%;
  	height: 100%;
  	background-color: #01AAED;
  }
  table{
    margin: 0 auto;
  }
</style>
