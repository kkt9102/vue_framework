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
        <!-- 약어 표현식 사용 전 -->
        <!-- <memo-form v-on:addMemo="addMemo" /> -->
        <!-- 약어 사용 후 -->
        <memo-form @addMemo="addMemo"/>
        <ul class="memo-list">
            <!-- v-for를 이용하여 memos데이터의 개수만큼 memo 컴포넌트 랜더링하기 -->
            <memo v-for="memo in moses" :key="memo.id" :memo="memo"/>
        </ul>
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
    created () {
        // 1. 만약 기존에 추가된 localStorage에 데어터가 있다면 created 훅에서 localStorage의 데이터를 컴포넌트 내의 memos 데어터에 넣어주고, 
        // 그렇지 않다면 그대로 빈 배열로 초기화함.
        this.memos = localStorage.memos ? JSON.parse(localStorage.memos) : [];
    },
    methods: {
        addMemo(payload) {
            // MemoForm에서 받은 데이터를 먼저 MemoApp.vue의 내부 데이터에 추가하는 작업
            this.memos.push(payload);
            // 받은 데이터를 문자열로 변환한 후, 로컬스토리지에 저장히는 작업
            this.storeMemo();
        },
        storeMemo () {
            // memosToString 변수 설정
            const memosToString = JSON.stringify(this.memos);
            localStorage.setItem('memos', memosToString);
        }
    },
}
</script>

<style scoped>
    .memo-list { padding: 20px 0; margin:0;}
</style>