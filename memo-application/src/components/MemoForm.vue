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
    <div class="memo_form">
        <!-- form 엘리먼트를 통하여 입력 form 작성 -->
        <form>
            <fieldset>
                <div class="memo_form_box">
                    <input type="text" class="title_input" placeholder="메모의 제목을 입력해주세요." />
                    <textarea class="body_textarea" placeholder="메모의 내용을 입력해주세요." />
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
    name: "MemoForm"
}
</script>

<style scoped>
    .memo_form {margin-bottom: 24px; padding-bottom: 40px; border-bottom: 1px solid #dedede;}
    .memo_form .memo_form_box {position: relative; padding: 24px; margin-bottom: 20px; box-shadow: 0 4px 10px -4px rgba(0,0,0,0.2); background-color: #ffffff;}
    .memo_form button[type="submit"] {float: right; width: 96px; padding: 12px 0; border-radius: 4px; background-color: #ff5a00; color: #ffffff; font-size:1rem;}
    .memo_form .memo_form_box .title_input {width:100%; margin-bottom:12px; font-size:18px; line-height: 26px;}
    .memo_form .memo_form_box .body_textarea {width:100%; height: 66px; font-size:14px; line-height: 22px; vertical-align: top;}
    .memo_form input:focus {outline: none;}
</style>