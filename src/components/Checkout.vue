<template>
  <div class="container">
    <template v-if="seen1" class="box">
      <ul>
        <li>
          <p
            style="font-size:13px;padding-top:10px;padding-left:5px;padding-bottom:5px"
          >1.你觉得以下哪一对情侣最恩爱？</p>
          <img src="../assets/1.png" width="100%">
          <br>
          <div class="choose-box">
            <el-radio v-model="radio" label="1" size="medium">情侣1</el-radio>
            <el-radio v-model="radio" label="2" size="medium">情侣2</el-radio>
            <el-radio v-model="radio" label="3" size="medium">情侣3</el-radio>
            <el-radio v-model="radio" label="4" size="medium">情侣4</el-radio>
          </div>
          <div class="button-box">
            <button v-on:click="handle1" class="button-box">下一题</button>
          </div>
        </li>
      </ul>
    </template>

    <template v-if="seen2" class="box">
      <ul>
        <li>
          <p style="font-size:13px;padding-top:10px;padding-left:5px;">2.你认为以下这段音乐描述的是这四个场景中的哪一个？</p>
          <audio
            src="../assets/献给爱丽丝.mp3"
            style="margin-bottom:7px;margin-top:7px;"
            controls="controls"
          ></audio>
          <img src="../assets/2.png" width="100%">
          <br>
          <div class="choose-box">
            <el-radio v-model="radio" label="5" size="medium">1</el-radio>
            <el-radio v-model="radio" label="6" size="medium">2</el-radio>
            <el-radio v-model="radio" label="7" size="medium">3</el-radio>
            <el-radio v-model="radio" label="8" size="medium">4</el-radio>
          </div>
          <div class="button-box">
            <button v-on:click="handle2" class="button-box">下一题</button>
          </div>
        </li>
      </ul>
    </template>

    <template v-if="seen3" class="box">
      <ul>
        <li>
          <p
            style="font-size:13px;padding-top:10px;padding-left:5px;padding-bottom:5px;"
          >3.凭第一眼缘和感觉，你最想和以下哪位女生做朋友？</p>
          <img src="../assets/3.png" width="100%">
          <br>
          <div class="choose-box">
            <el-radio v-model="radio" label="9" size="medium">女生1</el-radio>
            <el-radio v-model="radio" label="10" size="medium">女生2</el-radio>
            <el-radio v-model="radio" label="11" size="medium">女生3</el-radio>
            <el-radio v-model="radio" label="12" size="medium">女生4</el-radio>
          </div>
          <div class="button-box">
            <button v-on:click="handle3" class="button-box">下一题</button>
          </div>
        </li>
      </ul>
    </template>

    <template v-if="seen4" class="box">
      <ul>
        <li>
          <p
            style="font-size:13px;padding-top:10px;padding-left:5px;padding-bottom:5px;"
          >4.以下这张图片中你最先看到的是？</p>
          <img src="../assets/4.png" width="100%">
          <div class="choose-box">
            <el-radio v-model="radio" label="13" size="medium">森林中男人的背影</el-radio>
            <el-radio v-model="radio" label="14" size="medium">男人头部映像</el-radio>
          </div>
          <div class="button-box">
            <button v-on:click="handle4" class="button-box">下一题</button>
          </div>
        </li>
      </ul>
    </template>

    <template v-if="seen5" class="box">
      <ul>
        <li>
          <p
            style="font-size:13px;padding-top:10px;padding-left:5px;padding-bottom:5px;"
          >5.你认为下图中两个人的关系是？</p>
          <img src="../assets/5.png" width="100%">
          <div class="choose-box">
            <el-radio v-model="radio" label="15">普通的邻居关系</el-radio>
            <br>
            <el-radio v-model="radio" label="16">暧昧关系</el-radio>
            <br>
            <el-radio v-model="radio" label="17">男女闺蜜关系</el-radio>
          </div>
          <div class="button-box">
            <button v-on:click="handle5" class="button-box">下一题</button>
          </div>
        </li>
      </ul>
    </template>

    <template v-if="seen6" class="box">
      <ul>
        <li>
          <p
            style="font-size:13px;padding-top:10px;padding-left:5px;padding-bottom:5px;"
          >6.以下几个世界奇观景色，你最想去哪里看看？</p>
          <img src="../assets/6.png" width="100%">
          <div class="choose-box">
            <el-radio v-model="radio" label="18" size="small">a.冰河</el-radio>
            <br>
            <el-radio v-model="radio" label="19" size="small">b.地狱之门</el-radio>
            <br>
            <el-radio v-model="radio" label="20" size="small">c.汉密尔顿池</el-radio>
            <br>
            <el-radio v-model="radio" label="21" size="small">d.盐沼</el-radio>
            <br>
          </div>
          <div class="button-box">
            <button class="button-box" v-on:click="handle6">查看答案</button>
          </div>
        </li>
      </ul>
    </template>

    <template>
      <div class="answer-box" v-if="seen7">{{result}}</div>
    </template>
  </div>
</template>


<script>
import axios from "axios";
export default {
  name: "Checkout",
  data() {
    return {
      radio: "",
      seen1: true,
      seen2: false,
      seen3: false,
      seen4: false,
      seen5: false,
      seen6: false,
      seen7: false,
      answerArr: [],
      result: ""
    };
  },
  methods: {
    handle1: function() {
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      this.seen1 = false;
      this.seen2 = true;
      this.radio = "";
    },

    handle2: function() {
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      this.seen2 = false;
      this.seen3 = true;
      this.radio = "";
    },

    handle3: function() {
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      this.seen3 = false;
      this.seen4 = true;
      this.radio = "";
    },

    handle4: function() {
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      this.seen4 = false;
      this.seen5 = true;
      this.radio = "";
    },

    handle5: function() {
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      this.seen5 = false;
      this.seen6 = true;
      this.radio = "";
    },

    handle6: function() {
      let that = this;
      if (!this.radio) {
        alert("请选择答案再走呀！");
        return;
      }
      axios
        .post("http://localhost:3000/checkout", {
          answerArr: this.answerArr
        })
        .then(function(res) {
          console.log(res);
          that.result = res.data;
        });
      this.seen6 = false;
      this.seen7 = true;
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

.choose-box {
  padding-top: 20px;
  display: flex;
  justify-content: space-around;
}

.answer-box {
  padding-left: 30px;
  padding-right: 30px;
  padding-top: 30px;
  box-sizing: border-box;
  width: 100vw;
  height: 100vh;
  color: dimgrey;
  font-size: 18px;
  border: 1px solid #66669a;
  background-image: url(../assets/7.png);
}

.button-box {
  margin-top: 5px;
  line-height: 20px;
  padding: 4px;
  border-radius: 8px;
  display: flex;
  justify-content: flex-end;
  outline: none;
  background: #ffedb2;
  cursor: pointer; /*鼠标移入按钮时出现手势*/
}

.container {
  background-color: #ffedb2;
}

.box {
  box-sizing: border-box;
}
/* .class ul li{
  list-style:none
} */
</style>
