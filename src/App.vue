<template>

  <div class="black-bg" v-if="모달창열렸니==true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="모달창열렸니=false">닫기</button>
    </div>
  </div>
  <!--  상단메뉴 -->
  <div class="menu">
    <a v-for="i in 메뉴들" :key="i">
      {{ i }}
    </a>
  </div>

  <!--  상품, 가격, 신고수-->
  <div v-for="(원룸,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click="모달창열렸니=true"> {{ 원룸들[i].title }}</h4>
    <p>{{원룸들[i].content}}</p>
    <p> {{ 원룸들[i].price }}원 </p>
    <button v-on:click="신고수[i]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>


</template>
<script>

import data from './oneroom.js'

export default {
  name: 'App',
  data() {
    return {
      원룸들: data,
      모달창열렸니: false,
      price1: 60,
      price2: 80,
      price3: 100,
      스타일: "color:blue",
      product: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      메뉴들: ["Home", "Shop", "About"],
      신고수: [0, 0, 0, 0, 0, 0]
    }
  },
  method: {
    increase() {
      this.신고수 += 1;
    }
  },
  components: {},
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  position: fixed;
  padding: 20px;
}


.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;

}
</style>
