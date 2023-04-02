<template>
  <!-- v-if 내의 조건식이 true일 때 실행 -->
  <!-- v-if, v-else-if, v-else -->
  <div class="black-bg" v-if="modalOpened === true">
    <div class="white-bg">
      <h4>{{ roomData[roomIndex].title }}</h4>
      <p>{{ roomData[roomIndex].content }}</p>
      <button @click="modalOpened = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- v-for 반복문 -->
    <!-- Menus의 length 만큼 반복문이 실행 -->
    <!-- 각 index의 데이터를 ele로 사용 가능 -->
    <a v-for="v in Menus" :key="v">{{ v }}</a>
  </div>

  <div v-for="(v, i) in roomData" :key="v">
    <!-- 속성을 바인딩 하고싶은 경우 콜론(:) 사용 -->
    <img :src="`${v.image}`" class="room-img" />
    <h4
      @click="
        modalOpened = true;
        roomIndex = i;
      ">
      {{ v.title }}
    </h4>
    <p>{{ v.price }}</p>
    <!-- v-on:click, @click : vue방식 클릭 이벤트 -->
  </div>
</template>

<script>
  import data from './assets/room';

  export default {
    name: 'App',
    // 데이터 바인딩을 위한 데이터 보관 : data()
    data() {
      return {
        roomIndex: 0,
        roomData: data,
        modalOpened: false,
        // object형식으로 작성
        Menus: ['Home', 'Shop', 'About'],
      };
    },
    // 함수 보관 : methods
    // 변수 사용 시 this 사용
    methods: {
      // increase() {
      //   this.reports++;
      // },
    },
    components: {},
  };
</script>

<style>
  body {
    margin: 0;
    text-align: center;
  }
  div {
    box-sizing: border-box;
  }
  .menu {
    background: darkslateblue;
    padding: 15px;
    border-radius: 5px;
  }
  .menu a {
    color: white;
    padding: 10px;
    text-decoration: none;
  }
  .room-img {
    width: 100%;
    max-width: 500px;
    margin-top: 40px;
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
    border-radius: 8px;
    padding: 20px;
  }
</style>
