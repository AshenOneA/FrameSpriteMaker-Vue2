<template lang="html">
  <div id="app">
    <header class="header">
      <div class="header-left">
        <h1>逐帧动画雪碧图生成器</h1>
      </div>
      <div class="header-right">
        <a href="https://github.com/pspgbhu/FSM-FrameSpriteMaker-Vue2">GitHub</a>
      </div>
    </header>

    <div class="main">
      <el-content ref="cont" class="main-content"
        :files="files"
        :pixel="pixel"
        :line_num="line_num"
        :single_row="single_row">
      </el-content>
      <el-sidebar ref="bar" class="main-sidebar"></el-sidebar>
    </div>
  </div>
</template>

<script>
import elContent from './components/Content';
import elSidebar from './components/Sidebar';

export default {
  name: 'app',

  components: {
    elContent,
    elSidebar,
  },

  data() {
    return {
      files: [],
      pixel: {
        width: 0,
        height: 0,
      },
      line_num: 10,
      single_row: false,
    };
  },

  mounted() {
    this.$refs.bar.$on('change', val => {
      this.files = val.files;
      this.pixel = val.pixel;
      this.line_num = val.line;
      this.single_row = val.checked;
    });
  },
};
</script>

<style lang="">
  @import "style/reset.css";

  body{
    background: url(img/bg.jpg);
    font-size: 16px;
    color: #333;
  }

  .shadow{
    box-shadow: 2px 2px 10px 0px #aaa;
  }

  .tip{
    color: #999;
  }

  .header{
    display: flex;
    justify-content: space-between;;
    color: #fff;
    padding: 10px 30px;
    line-height: 50px;
    vertical-align: center;
    background-color: #09c;

    h1{
      font-size: 30px;
    }

    a{
      color: #fff;
      font-size: 16px;
    }
  }

  .main{
    padding: 10px 30px;
    display: flex;
    flex-direction: row;

    .main-content{
      padding-right: 10px;
      flex: auto;
    }

    .main-sidebar{
      flex: 0 0 300px;
    }
  }
</style>
