<template>
  <div id="container">
    <!-- <video id="video" src="videos/demo.mp4" controls></video> -->
     <img src="https://img95.699pic.com/photo/50059/8720.jpg_wh860.jpg" />
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
      barrageList: []
    }
  },
  mounted() {
    // 加载弹幕
    const barrage = new Barrage({
      container: document.getElementById('container'), // 父级容器
      data: example, // 弹幕数据
      config: {
        // 全局配置项
        duration: 20000, // 弹幕循环周期(单位：毫秒)
        defaultColor: '#ccc', // 弹幕默认颜色
      },
    })

    barrage.play();
  },
  methods:{
    
  }
}
</script>

<style>
  img {
    visibility: hidden;
  }

  #app {
    width: 100%;
    height: 100vh;
    margin: 0 !important;
    padding: 0 !important;
    background-color: black;
  }
</style>
