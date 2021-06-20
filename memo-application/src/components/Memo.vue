<!-- 각각의 메모의 상태를 표현할 수 있는 컴포넌트 -->
<!--
// 싱글 파일 컴포넌트의 기본 형식
<template>
    <div>Single File Compoent의 기본 형식</div> 
</template>

<script>
    export default {
        name: '컴포넌트 이름'
    }
</script>

<style scoped>
</style>
-->

<template>
  <li class="memo-item">
      <!-- Spring이나 Ruby on Rails 를 이용해서 DB값 뿌려는 방식 (기본적인 Form은 다 비슷한가보다..) -->
      <strong>{{ memo.title }}</strong>
      <p>{{ memo.content }}</p>
      <!-- button 클릭시 이벤트를 deleteMemo 함수로 등록 -->
      <button class="deleted_btn" @click="deleteMemo">X</button>
  </li>
</template>

<script>
export default {
    name: 'Memo',
    // 부모한테서 내려받은 props를 등록함 (메모를 입력하여 저장된 데이터)
    props: {
        memo: {
            type: Object
        }
    },
    methods: {
        deleteMemo () {
            // 부모(저장된 데이터)로부터 받은 memo의 id를 
            const id = this.memo.id;
            //부모 컴포넌트의 사용자 정의 이벤트인 deleteMemo 함수의 파라미터로 전달함.
            this.$emit('deleteMemo', id);
        }
    }
}
</script>

<style scoped>
    .memo-item {position:relative; width:100%; height:200px; margin-bottom: 50px; border:1px solid #000000;}
    .memo-item strong {font-size:2.0rem;}
    .memo-item p {font-size:1.2rem; margin-top:15px;}
    .deleted_btn {position: absolute; cursor:pointer; top:10px; right:10px; width:20px; height: 20px; font-size: 1rem;}
</style>
