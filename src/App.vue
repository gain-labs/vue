<template>
  <div class="header">
    <ul class="header-button-left">
      <li>Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li>Next</li>
    </ul>
    <img src="./assets/logo.png" class="logo" />
  </div>

  <Container_ :data="data" :step="step" />
  <button @click="more">더보기</button>
  <h4>Hi {{ $store.state.name }}</h4>
  <button @click="$store.commit('이름변경')">버튼</button>
  <p>{{ $store.state.age }}</p>
  <button @click="$store.commit('나이변경')">나이 변경</button>
  <div class="footer">
    <ul class="footer-button-plus">
      <input type="file" id="file" class="inputfile" />
      <label for="file" class="input-plus">+</label>
    </ul>
  </div>
</template>

<script>
import Container_ from "./components/Container_.vue";
import { data } from "./data";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      data,
      clickCount: 0,
      step: 0,
    };
  },
  components: {
    Container_,
  },
  methods: {
    more() {
      axios
        .get(`https://codingapple1.github.io/vue/more${this.clickCount}.json`)
        .then((결과) => {
          this.data.push(결과.data);
          this.clickCount++;
        });
    },
  },
};
</script>

<style>
body {
  margin: 0;
}
ul {
  padding: 5px;
  list-style-type: none;
}
.logo {
  width: 22px;
  margin: auto;
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 13px;
}
.header {
  width: 100%;
  height: 40px;
  background-color: white;
  padding-bottom: 8px;
  position: sticky;
  top: 0;
}
.header-button-left {
  color: skyblue;
  float: left;
  width: 50px;
  padding-left: 20px;
  cursor: pointer;
  margin-top: 10px;
}
.header-button-right {
  color: skyblue;
  float: right;
  width: 50px;
  cursor: pointer;
  margin-top: 10px;
}
.footer {
  width: 100%;
  position: sticky;
  bottom: 0;
  padding-bottom: 10px;
  background-color: white;
}
.footer-button-plus {
  width: 80px;
  margin: auto;
  text-align: center;
  cursor: pointer;
  font-size: 24px;
  padding-top: 12px;
}
.sample-box {
  width: 100%;
  height: 600px;
  background-color: bisque;
}
.inputfile {
  display: none;
}
.input-plus {
  cursor: pointer;
}
</style>
