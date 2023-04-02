<template>
  <!-- v-if 내의 조건식이 true일 때 실행 -->
  <!-- v-if, v-else-if, v-else -->
  <div class="black-bg" v-if="modalOpened === true">
    <div class="white-bg">
      <h4>{{ roomData[roomIndex].title }}</h4>
      <p>{{ roomData[roomIndex].content }}</p>
      <!-- <input @input="month = $event.target.value" /> :v-model로 대체 가능 -->
      <!-- 숫자로 바꿀 수도 있음 number -->
      <input v-model.number="month" />
      <p>{{ month }}개월 선택됨 : {{ roomData[roomIndex].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Modal',
    data() {
      return {
        month: 1, // 초기값의 타입에 따라 v-model 값의 타입을 결정함
      };
    },
    // watch로 input 데이터 감시하기 (데이터가 변경될 때마다 함수가 실행됨)
    watch: {
      month(v) {
        if (v >= 13) alert('최대 12개월까지 입력 가능합니다.');
      },
    },
    props: {
      // props로 받아온 데이터의 자료형까지 입력
      // props는 read-only, 수정 불가
      roomData: Array,
      roomIndex: Number,
      modalOpened: Boolean,
    },
  };
</script>

<style></style>
