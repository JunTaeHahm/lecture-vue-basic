<template>
  <!-- transition 태그로 애니메이션 적용하기 -->
  <transition name="fade">
    <Modal
      @closeModal="modalOpened = false"
      :roomData="roomData"
      :roomIndex="roomIndex"
      :modalOpened="modalOpened" />
  </transition>

  <Menu :menus="menus" />

  <Discount v-if="showDiscount === true" />

  <button @click="sortPrice">가격 순 정렬</button>
  <button @click="sortRefresh">되돌리기</button>

  <Card
    @openModal="
      // 자식으로 부터 받은 emit의 이름(@openModal)과 데이터($event)
      modalOpened = true;
      roomIndex = $event;
    "
    :roomData="roomData[i]"
    v-for="(v, i) in roomData"
    :key="v" />
</template>

<script>
  import data from './assets/room';
  import Card from './components/Card.vue';
  import Discount from './components/Discount.vue';
  import Menu from './components/Menu.vue';
  import Modal from './components/Modal.vue';

  export default {
    name: 'App',
    // 데이터 바인딩을 위한 데이터 보관 : data()
    data() {
      return {
        showDiscount: true,
        roomOrigin: [...data],
        roomIndex: 0,
        roomData: data,
        modalOpened: false,
        // object형식으로 작성
        menus: ['Home', 'Shop', 'About'],
      };
    },
    // 함수 보관 : methods
    // 변수 사용 시 this 사용
    methods: {
      sortPrice() {
        this.roomData.sort((a, b) => a.price - b.price);
      },
      sortRefresh() {
        this.roomData = [...this.roomOrigin];
      },
    },

    // Lifecycle
    // created: HTML 생성 전, 데이터만 존재할 때
    created() {},
    // mounted: vue가 mount된 후
    mounted() {
      setTimeout(() => {
        this.showDiscount = false;
      }, 2000);
    },
    // beforeUpdated: 컴포넌트가 update되기 전에
    beforeUpdate() {},

    components: {
      Discount: Discount,
      Modal: Modal,
      Card: Card,
      Menu: Menu,
    },
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

  /* transition 태그 사용법 */
  /* enter-leave */
  .fade-enter-from {
    opacity: 0;
  }
  .fade-enter-active {
    transition: 0.3s;
  }
  .fade-enter-to {
    opacity: 1;
  }

  .fade-leave-from {
    opacity: 1;
  }
  .fade-leave-active {
    transition: 0.3s;
  }
  .fade-leave-to {
    opacity: 0;
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
  .discount {
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  }
</style>
