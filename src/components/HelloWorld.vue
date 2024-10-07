<template>
  <div id="container">
    <!-- <video id="video" src="videos/demo.mp4" controls></video> -->
     <img src="https://img95.699pic.com/photo/50059/8720.jpg_wh860.jpg" />
     <a-input-search
      v-model:value="value"
      placeholder="请输入一条弹幕"
      enter-button="发射"
      class="input"
      size="large"
      @search="onSearch"
    />
  </div>
</template>

<script>
import Barrage from 'barrage-ui';
import example from 'barrage-ui/example.json'; // 组件提供的示例数据

export default {
  name: 'HelloWorld',
  data () {
    return {
      barrage: {},
      barrageIsShow: true,
      currentId : 0,
      barrageLoop: false,
      barrageList: [],
      value: ''
    }
  },
  
  mounted() {
    this.barrage = new Barrage({
      container: document.getElementById('container'), // 父级容器
      data: example, // 弹幕数据
      config: {
        // 全局配置项
        duration: 20000, // 弹幕循环周期(单位：毫秒)
        defaultColor: '#ccc', // 弹幕默认颜色
      },
    })
    
    this.barrage.play();
  },
  methods:{
    onSearch: function(value) {
      const uniqueId = `${Math.random().toString(36).substr(2, 9)}${Math.random().toString(36).substr(2, 9)}`;
      console.log(uniqueId, value);

      this.barrage.add({
        key: uniqueId, // 弹幕的唯一标识
        time: 1000, // 弹幕出现的时间(单位：毫秒)
        text: value, // 弹幕文本内容
        fontSize: 24, // 该条弹幕的字号大小(单位：像素)，会覆盖全局设置
        color: '#0ff', // 该条弹幕的颜色，会覆盖全局设置
      });
    }
  }
}
</script>

<style>
  img {
    visibility: hidden;
  }

  #container {
    width: 100%;
    height: 100%;
  }

  #app {
    width: 100%;
    height: 100vh;
    margin: 0 !important;
    padding: 0 !important;
    background-color: black;
  }

  .input {
    max-width: 80%;
    margin: 10px;
    width: 400px;
    position: absolute;
    bottom: 20px;
    left: 0;
    right: 0;
  }
</style>
