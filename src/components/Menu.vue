<template>
  <div class="menu">
    <!-- v-for 반복문 -->
    <!-- Menus의 length 만큼 반복문이 실행 -->
    <!-- 각 index의 데이터를 ele로 사용 가능 -->
    <a v-for="v in menus" :key="v">{{ v }}</a>
  </div>
</template>

<script>
  export default {
    name: 'Menu',
    props: {
      menus: Array,
    },
  };
</script>

<style></style>
