<template>
  <div class="post" v-for="(item, index) in data" :key="index">
    <div class="post-header">
      <div class="profile">
        <img class="profile" :src="data[index].userImage" />
      </div>
      <span class="profile-name">{{ data[index].name }}</span>
    </div>
    <div
      class="post-body"
      :style="{ backgroundImage: `url(${data[index].postImage})` }"
      @click="$store.commit('좋아요', 1)"
    ></div>
    <div class="post-content">
      <p>{{ $store.state.likes }}</p>
      <p>
        <strong>{{ data[index].name }}</strong> {{ data[index].content }}
      </p>
      <p class="date">{{ data[index].date }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Post_",
  props: {
    data: [],
  },
};
</script>

<style>
.post {
  width: 100%;
}
.profile {
  background-image: url("https://placeimg.com/100/100/arch");
  width: 30px;
  height: 30px;
  background-size: 100%;
  border-radius: 50%;
  float: left;
}
.profile-name {
  display: block;
  float: left;
  padding-left: 10px;
  padding-top: 7px;
  font-size: 14px;
}
.post-header {
  height: 30px;
  padding: 10px;
}
.post-body {
  background-image: url("https://placeimg.com/640/480/animals");
  height: 450px;
  background-position: center;
  background-size: cover;
}
.post-content {
  padding-left: 15px;
  padding-right: 15px;
  font-size: 14px;
}
.date {
  font-size: 11px;
  color: grey;
  margin-top: -8px;
}
</style>
