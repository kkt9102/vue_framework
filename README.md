# vue_memo_app

## 참고서적 : 커피 한 잔 마시며 끝내는 Vue.JS

### CODE 5-1
    - vue init webpack-simple memo-application

    - 책에서 사용한 옵션
        -Project name: memo-application (자유롭게 작성)
        -Project description: A Vue.js project (자유롭게 작성)
        -License: MIT
        -Use Sass?: NO
        
    - 애플리케이션 실행에 필요한 모듈 설치
        -cd memo-applicaion
        -npm install    혹은    npm i

    - 프로젝트 실행
        -npm run dev
## 작업순서
---
    1. 프로젝트 생성
        -Project name: memo-application (memo_crud)
        -Project description: A Vue.js project (vue.js project)
        -Author: kkt9102@gmail.com
        -License: kkt9102
        -Use Sass?: NO
---
    2. common.css 추가
        -src폴더 안에 style 폴더 추가
        -style폴더 안에 common.css 추가 및 적용 (개인적으로 쓰는 common.css임)
---
    3. common.css import하기
        -App.vue에 작성한 common.css import하기
        -App.vue 의 33번째 줄 부터 <style> 가 시작됨
        -추가 코드
            @import "./style/common.css";
---
    4. 헤더(Header)컴포넌트 생성
        -src 폴더 안에 components 폴더 추가
        -components 폴더 안에 AppHeader.vue 추가 및 코드 작성
        -추가 코드
```html
            <!-- src/components/AppHeader.vue -->
            <template>
                <div class="app-header">
                    <h1>메모 어플리케이션</h1>
                </div>
            </template>

            <script>
            export default {
                name: 'AppHeader',
            };
            </script>

            <style scoped>
                .app-header{overflow: hidden; padding: 52px 0 27px;}
                .app-header h1 {float: left; font-size: 24px; text-align: center;}
            </style>
```
---
    5. App.vue 에 AppHeader.vue import하기
        -App.vue의 22번째 줄부터 <script> 가 시작됨
        -변경 전 코드
```javascript
        <!-- file : App.vue -->
        <script>
            export default {
            name: 'app',
             data () {
               return {
                 msg: 'Welcome to Your Vue.js App'
               }
             }
            }
            </script>
```
        -변경 후 코드
```javascript
        <script>
        // AppHeader.vue import하기
        import Appheader from './components/AppHeader';

        export default {
        name: 'app',
        components: {
            Appheader
        }
        // 프로젝트 생성 시 처음에 등록되어있던 코드
        // data () {
        //   return {
        //     msg: 'Welcome to Your Vue.js App'
        //   }
        // }
        }
        </script>
```
---
    6. App.vue에 AppHeader를  커스텀 엘리먼트로 사용하기
        -App.vue의 시작 코드부분부터 <template> 가 시작됨
        -변경 전 코드
```html
        <!-- file : App.vue -->
        <template>
            <div id="app">
                <img src="./assets/logo.png">
                    <h1>{{ msg }}</h1>
                    <h2>Essential Links</h2>
                    <ul>
                        <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
                        <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
                        <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
                        <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
                    </ul>
                    <h2>Ecosystem</h2>
                    <ul>
                        <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
                        <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
                        <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
                        <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
                </ul>
            </div>
        </template>
```
        -변경 후 코드
```html
        <template>
            <div id="app">
                <app-header>
                    <Appheader />
                </app-header>
            </div>
        </template>
```
---
    7. 메모 데이터 생성 기능을 구현하기위한 파일생성
        -src 폴더안에 Memo.vue, MemoApp.vue, MemoForm.vue 생성
---
    8. MemoApp.vue에 코드 작성
        -작성한 코드
```html
            <!-- file : MemoApp.vue -->
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
```
---
    9. MemoForm.vue에 사용자가 입력할 수 있는 form 구현
        -작성코드
[코드 보러가기](/MemoForm.vue_초기작성코드.md)
---
    10. MemoApp.vue에 components 추가하기 (삽질함)
        -책보고 그대로 따라했다가 components 빼먹어서 삽질함...
        -MemoApp.vue에 components 추가하기
        -추가코드
```javascript
            <!-- file : MemoApp.vue -->
            .
            .
            .
            .
            components: {
                MemoForm,
                Memo
            },
            data () {
                return {
                    memos: [],
            .
            .
            .
            .
```
---
    11. App.vue에 MemoApp.vue 등록하기
        -MemoApp 컴포넌트를 App.vue에 등록하기
        -변경된 코드
```javascript
            <!-- file : App.vue -->
            <script>
            import AppHeader from './components/AppHeader';
            import MemoApp from './components/MemoApp';

            export default {
            name: 'app',
            components: {
                AppHeader,
                MemoApp
                }
            }
            </script>
```
        -'template > div' 안에 <memo-app/> 추가하기
---
    12. MemoForm.vue에 데이터를 등록하는 코드
        -MemoForm.vue에 사용자가 값을 입력한 후 저장을 할 때 저장 될 값의 value를 지정해준다.
        -export default 에 data를 추가해 준 뒤 값을 지정해준다.
        -작성코드
```javascript
        <!-- file : MemoForm.vue -->
        .
        .
        .
        .
        <fieldset>
            <div class="memo-form-box">
                <input type="text" class="title_input" v-model="title" placeholder="메모의 제목을 입력해주세요." />
                <textarea class="body_textarea" v-model="content" placeholder="메모의 내용을 입력해주세요." />
                <button type="reset">초기화</button>
            </div>
            <button type="submit">등록하기</button>
        </fieldset>
        .
        .
        .
        .
        <script>
        export default {
            name: "MemoForm",
            deta () {
                return {
                    title: '',
                    contents: '',
                }
            }
        }
        </script>
```
---
    13. MemoForm.vue 에 메모를 저장하는 코드 작성
        -작성코드
[코드 보러가기](/MemoForm.vue_메모저장기능추가_코드.md)
---
    14. MemoApp.vue에서 MemoForm.vue로부터 받은 데이터를 local에 저장하는 기능 추가 코드 작성
        -추가코드
```javascript
        <!-- file : MemoApp.vue -->
        .
        .
        .
        .
        methods: {
                addMemo (payload) {
                    // MemoForm에서 받은 데이터를 먼저 MemoApp.vue의 내부 데이터에 추가하는 작업
                    this.memos.push(payload);
                    // 받은 데이터를 문자열로 변환한 후, 로컬스토리지에 저장히는 작업
                    this.storeMemo();
                },
                storeMemo () {
                    const memosToString = JSON.stringify(this.memos);
                    localStorage.setItem('memos',memosToString);
                }
            },
        }
        </script>
```
---
    15. MemoApp.vue안에 MemoForm.vue에 사용된 v-no 디렉티브의 약어 표시하기
        -추가된 코드
```html
        <template>
            <div class="memo-app">
                <!-- 약어 표현식 사용 전 -->
                <!-- <memo-form v-on:addMemo="addMemo" /> -->
                <!-- 약어 사용 후 -->
                <memo-form @addMemo="addMemo" />
                <memo />
            </div>
        </template>
```
## 특이사항
1. 프로젝트 생성 후 오류가 뜸. 작동은 정상적으로 됨
    - 오류코드
        found 15 vulnerabilities (3 low, 6 moderate, 6 high)
        run `npm audit fix` to fix them, or `npm audit` for details
