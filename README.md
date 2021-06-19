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
---
    5. App.vue 에 AppHeader.vue import하기
        -App.vue의 22번째 줄부터 <script> 가 시작됨
        -변경 전 코드
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
        -변경 후 코드
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
---
    6. App.vue에 AppHeader를  커스텀 엘리먼트로 사용하기
        -App.vue의 시작 코드부분부터 <template> 가 시작됨
        -변경 전 코드
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
        -변경 후 코드
        <template>
            <div id="app">
                <app-header>
                <Appheader></Appheader>
                </app-header>
            </div>
        </template>

## 특이사항
1. 프로젝트 생성 후 오류가 뜸. 작동은 정상적으로 됨
    - 오류코드
        found 15 vulnerabilities (3 low, 6 moderate, 6 high)
        run `npm audit fix` to fix them, or `npm audit` for details
