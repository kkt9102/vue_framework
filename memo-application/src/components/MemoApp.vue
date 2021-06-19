<!-- 메모들의 상태를 관리하는 컴포넌트 -->
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
    <div class="memo-app">
        <memo-form />
        <memo />
    </div>
</template>

<script>
import MemoForm from './MemoForm';
import Memo from './Memo';

export default {
    name: 'MemoApp',
    components: {
        MemoForm,
        Memo
    },
    data () {
        return {
            memos: [],
        };
    },
    created() {
        // 1. 만약 기존에 추가된 localStorage에 데어터가 있다면 created 훅에서 localStorage의 데이터를 컴포넌트 내의 memos 데어터에 넣어주고, 
        // 그렇지 않다면 그대로 빈 배열로 초기화함.
        this.memos = localStorage.memos ? JSON.parse(localStorage.memos) : [];
    }
}
</script>