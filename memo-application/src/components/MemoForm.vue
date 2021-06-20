<!-- 사용자의 메모를 입력받는 폼 컴포넌트 -->
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
    <div class="memo-form">
        <!-- form 엘리먼트를 통하여 입력 form 작성 -->

        <!-- form에 submit 이벤트를 직접 조작한다. -->
        <!-- <form @submit.prevent="addMemo"> => form에 submit 이벤트가 발생하면 직접 작성한 addMemo 함수가 콜백함수로 실행된다. -->
        <form @submit.prevent="addMemo">
            <fieldset>
                <div class="memo-form-box">
                    <input type="text" class="title_input" v-model="title" placeholder="메모의 제목을 입력해주세요." />
                    <textarea class="body_textarea" v-model="content" placeholder="메모의 내용을 입력해주세요." />
                    <button type="reset">초기화</button>
                </div>
                <button type="submit">등록하기</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
    // 컴포넌트의 이름을 MemoForm으로 변경
    name: "MemoForm",
    data () {
        return {
            title: '',
            content: '',
        }
    },
    methods: {
        addMemo () {
            // 변수 선언 (title, content )
            const { title, content } = this;
            // 저장될 데이터의 고유한 식별용 id 생성
            const id = new Date().getTime();
            // 공백체크 (제목 혹은 내용을 입력하지 않았을 때 경고창)
            const isEmpty = title.length <= 0 || content.length <= 0;

            if (isEmpty) {
                return false;
            }

            // addMemo 이벤트가 발생할 시 사용자가 입력한 데이터를 넣어준다.
            this.$emit('addMemo', { id, title, content });
        },
    }
}
</script>

<style scoped>
    .memo-form {margin-bottom: 24px; padding-bottom: 40px; border-bottom: 1px solid #dedede;}
    .memo-form .memo-form-box {position: relative; padding: 24px; margin-bottom: 20px; box-shadow: 0 4px 10px -4px rgba(0,0,0,0.2); background-color: #ffffff;}
    .memo-form button[type="submit"] {float: right; width: 96px; padding: 12px 0; border-radius: 4px; background-color: #ff5a00; color: #ffffff; font-size:1rem;}
    .memo-form .memo-form-box .title_input {width:100%; margin-bottom:12px; font-size:18px; line-height: 26px;}
    .memo-form .memo-form-box .body_textarea {width:100%; height: 66px; font-size:14px; line-height: 22px; vertical-align: top;}
    .memo-form input:focus {outline: none;}
</style>