<template>
  <div>
    <!-- 속성을 바인딩 하고싶은 경우 콜론(:) 사용 -->
    <img :src="`${roomData.image}`" class="room-img" />
    <!-- $emit()으로 부모컴포넌트에게 custom event 발신 -->
    <h4 @click="$emit('openModal', roomData.id)">{{ roomData.title }}</h4>
    <p>{{ roomData.price }}원</p>
    <!-- v-on:click, @click : vue방식 클릭 이벤트 -->
  </div>
</template>

<script>
  export default {
    name: 'Card',
    props: {
      roomData: Object,
    },
  };
</script>

<style></style>
