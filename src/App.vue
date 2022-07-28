<template>
  <!-- 리지 : 가입전 시작 view, 소개view, 가입완료view, 가입후 시작 view -->
  <div v-if="start_page==true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div id="logo">로고</div>
      <div><button @click="introBtnOn" type="button" class="btn" id="introductionBtn">소개</button></div>
      <div><button @click="signUpBtnOn" type="button" onclick="" class="btn">시작하기</button></div>
      <div><button @click="pwBtnOn" type="button" onclick="" class="btn">비밀번호 찾기</button></div>
      <div style="color: white;">teamname</div>
    </div>
  </div>

  <div v-if="introduction_page==true">
    <div><button @click="introBtnOff" type="button" id="backBtn">Back</button></div>
    <div class="container">    
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div id="introductionBox">
        <p>Christmas Q25는 12월 1일부터 12월 25일 크리스마스까지
        1년을 돌아볼 수 있는 질문들을 매일 하나씩 제공합니다.</p>
        <p>여러분들은 각 질문에 대한 답변을 작성하며 1년을 되돌아보고, 정리할 수 있을 것입니다.</p>
        <p>Christmas Q25가 1년동안의 소중했던 추억, 행복했던 기억, 고마웠던 사람을 떠올리게 하는
            따뜻한 매개체가 되길 바라며
        </p>
        <p>모든 사용자분들의 행복한 연말을 기원합니다.</p>
      </div>
      <div><button @click="introBtnOff" type="button" class="btn" id="closeBtn">닫기</button></div>
    </div>
  </div>

  <div v-if="complete_page==true">
     <div class="container">
        <div id="title">Christmas Q25</div>
        <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
        <div id="Registration">축하하는 느낌의 일러스트</div>
        <div style="color: white;">
          생성이 완료되었어요 :)<br>
          <div id="usermail"><a :href="email">{{email}}</a></div>
          메일함을 확인해주세요!
        </div>
        <div><button type="button" @click="togo_login_page" class="btn">바로가기</button></div>
    </div>
  </div>

  <div v-if="login_page==true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div id="logo">로고</div>
      <div style="color: white; text-align: center;">
        <div>어서오세요 <span class="userName">{{nickname}}</span>님!</div>
        <div>메리크리스마스<span style="font-size: 20px;">&#x1F384;</span></div>
      </div>
      <form action="" method="post">
        <div>
          <input type="password" placeholder="비밀번호를 입력해주세요." id="password" name="pw" required>
        </div>
      </form>
      <div><button type="button" @click="togo_Qlist_page" class="btn">시작하기</button></div>
      <div><button type="button" class="btn">비밀번호 찾기</button></div>
      <div style="color: white;">teamname</div>
    </div>

  </div>
  
  <!-- 자몽 : 비번찾기 view -->
  <div v-if="pw_find_page==true">
    <!--비밀번호 재설정 링크 발송 모달창 -->
    <div class="black-bg" v-if="ClickButton == true">
      <div class="white-bg">
        <div class="password_represent">
        <span class="title">비밀번호 재설정 링크를</span>
        <span class="title"> 발송하였습니다</span>
        <span class="mail">메일함을 확인해주세요</span>
        <hr width="220px">
        <span @click="ClickButton= false" class="ok">확인</span>
      </div>
    </div>
  </div>


    <!--비밀번호 재설정 링크 발송 모달창 (API 적용할때 추가예정)
      <div class="black-bg" v-if="ClickButton == true">
      <div class="white-bg">
        <div class=  "password_represent">
          <span class="title">등록되지 않은</span>
          <span class="title">이메일입니다</span>
          <hr width="200px">
          <span @click="ClickButton= false" class="ok">확인</span>
        </div>
      </div>
      </div>-->


      <div class="key_icon">
      <img alt="Vue logo" src="./assets/key.png">
      </div>

      <div class="password_guide">
        <div class="info1">이메일을 입력해주세요!</div>
        <div class="info1">비밀번호 재설정 링크가 </div>
        <div class="info1">발송됩니다</div>
      </div>

      <div class="bottom_input">
        <input type="text" name="" placeholder="이메일 입력해주세요 !">
      </div>

      <button @click="ClickButton =true" class="next_button">완료</button>

      </div>

  <!-- 미니 : 회원가입 view-->
  <div v-if="signUp_page==true" id="signUp_page">
    <div class="black-bg check-password" v-if="pwOpen == true">
      <div class="white-bg">
        <h4>비밀번호를 입력해주세요</h4>
        <button @click="check">확인</button>
      </div>
    </div>
    <div class="black-bg check-email" v-if="emailOpen == true">
      <div class="white-bg">
        <h4>이메일 중복확인을 완료해주세요</h4>
        <button @click="check">확인</button>
      </div>
    </div>
    <div class="black-bg check-nickname" v-if="nickOpen == true">
      <div class="white-bg">
        <h4>닉네임을 입력해주세요</h4>
        <button @click="check">확인</button>
      </div>
    </div>
  

  <div id="start">
    <div class="content">
      <ul>
        <li>
          <div class="label-box">
            <span>페이지에 표기될 닉네임을<br>입력해주세요!</span>
          </div>
          <div class="input-box">
            <input type="text" class="inputText" v-model="nickName" placeholder="닉네임을 입력해주세요!">
          </div>
        </li>
        <li>
          <div class="label-box">
            <span>링크를 전달받으실 이메일을<br>입력해주세요!</span>
          </div>
          <div class="input-box">
            <input type="email" class="inputText" v-model="email" placeholder="이메일을 입력해주세요!">
            <br>
            <button class="overlap-btn" @click="chkOverlap">중복확인</button>
            <i class="fa fa-check" v-if="chkEmail == true"></i>

          </div>
        </li>
        <li>
          <div class="label-box">
            <span>아무나 작성할 수 없도록!<br>비밀번호를 입력해주세요</span>
          </div>
          <div class="input-box">
            <input type="password" class="inputText" id="inputPW" v-model="password" placeholder="비밀번호를 입력해주세요!" @change="chkInput">
            <p :class="[chkPw === false ? 'unchk' : 'chk']">*영문/숫자 포함 6자 이상</p>
          </div>
        </li>
      </ul>
    </div>
    <div class="finish">
      <button class="finish-btn" @click="submit">완료</button>
    </div>
  </div>
  </div>

  <!-- 엘 : 질문리스트 view-->
  <div v-if="Q_list_page==true" id="Q_list_page">
    <div class="title">
      <div><span class="userName">{{nickName}}</span>'s</div> 
      <div>Christmas Q25</div>
      <div id="title_line"></div>
      <p>당신의 1년을 정리하는 25개의 질문</p>
      <p> 선물상자는 1번부터 열어주세요 :) </p>
    </div>
    
    <div class="newcontents">
      <!-- <p>하단에 답변을 모아볼 수 있는 버튼이 있어요!</p> -->
      <div v-for="i in 8" :key="i">
        <div @click="questionList" v-for="j in 3" :key="j">
          <img :src="require(`@/assets/box/${3*(i-1)+j}.png`)" alt="" id='giftbox'>
          {{3*(i-1)+j}}
        </div>
        <div @click="questionList" v-if='i==8'>
          <img src="./assets/box/25.png" alt="" id="giftbox_25">
          25
        </div>
      </div>
      <button id="answer_group" @click="togo_answerGrouping_page">답변 모아보기</button>
    </div>

  </div>



</template>

<script>


export default {
  name: 'App',
  data() {
    return{
      start_page : false,
      introduction_page : false,
      Q_list_page : true,
      pw_find_page : false,
      signUp_page : false,
      complete_page : false,
      login_page : false,

      email : 'user@gmail.com',

      nickName : 'nickName 데이터',
      질문데이터 : '부여된 랜덤 질문 리스트 데이터',
      ClickButton : false,
      nickOpen: false,
      password: '',
      pwOpen: false,
      chkPw: true,
      chkNum: /[0-9]/,
      chkEng: /[a-zA-Z]/,
      chkEmail: false,
      emailOpen: false
    }
  },
  methods: {
    introBtnOn() {
      this.start_page=false;
      this.introduction_page=true;
    },
    introBtnOff(){
      this.start_page=true;
      this.introduction_page=false;
    },
    signUpBtnOn(){
      this.start_page=false;
      this.signUp_page=true;
    },
    // 닫기버튼이 아직 없어서 적용못함
    signUpBtnOff(){
      this.signUp_page=false;
    },
    pwBtnOn(){
      this.start_page=false;
      this.pw_find_page=true;
    },
    togo_login_page(){
      this.complete_page=false;
      this.login_page=true;
    },
    togo_Qlist_page(){
      this.Q_list_page=true;
      this.login_page=false;
    },
    togo_answerGrouping_page(){
      this.Q_list_page=false;
    },

    random_Q(){
      console.log(this.nickName)
    },
    submit(e){
      e.preventDefault();
      if (this.nickName == ''){
        this.nickOpen = true;
      }
      if (this.password == ''){
        this.pwOpen = true;
      }
      if (this.chkEmail == false){
        this.emailOpen = true;
      }
      else {
        this.complete_page=true;
        this.signUp_page=false;
      }
    },
    check(){
      this.nickOpen = false;
      this.pwOpen = false;
      this.emailOpen = false;
    },
    chkInput(){
      if (this.password.length < 6){
        this.chkPw = false;
      }
      if(!this.chkNum.test(this.password)){
        this.chkPw = false;
      }
      if(!this.chkEng.test(this.password)){
        this.chkPw = false;
      }
      if(this.password.length > 5 && this.chkNum.test(this.password) && this.chkEng.test(this.password))
        this.chkPw = true;
    },
    chkOverlap(){
      this.chkEmail = true;
    }
  },
  components: {
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Sorts+Mill+Goudy&display=swap');
@font-face {
    font-family: 'NanumSquareRound';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/NanumSquareRound.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}
#app {
  margin-top: 20px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  display: flex;
  flex-direction: column;
  align-items:  center;
  /* justify-content: center; */
  background-color: #920000;
  border-radius: 5px;
  padding: 20px;
  padding-top: 70px;
  width: 360px;
  height: 640px;
}
* {
  margin: 0;
  padding: 0;
  /* box-sizing: border-box; */
}
body {
  margin: 0;
  display: flex;
  background-color: #920000;
  align-items:  center;
  justify-content: center;
} 

/* 리지 */
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #920000;
    width: 360px; height: 640px;
    margin: 0 auto;
}

.btn {
    margin: 7px;
    background-color: white;
    border: none;
    border-radius: 3px;
    width: 170px; height: 42px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
}

#title {
    color: #FFF500;
    font-family: 'OFL Sorts Mill Goudy TT';
    font-size: 50px;
    margin-top: 50px;
}

#logo {
    color: black;
    width: 50px;
    padding: 60px;
    border: 1px solid black;
    margin: 40px;
    padding-top: 70px;
    padding-bottom: 70px;
    text-align : center;

    background-color: white;
}

#introductionBox {
    /* border: 1px solid black; */
    /* width: 315px;
    height: 360px; */
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 25px;
    border-radius: 5px;
    background-color: #F4E7B6;

    margin: 30px;
}

#Registration {
    color: black;
    width: 50px;
    padding: 60px;
    border: 1px solid black;
    margin: 40px;
    text-align: center;

    background-color: white;
}

#backBtn {
    background-color:rgba(0,0,0,0);
    color: #0D86FE;
    font-weight: bold;
    border-color: transparent;
    border: none;
    cursor: pointer;
}

.subtitle {
    color: white;
}

#password {
    width: 170px; height: 30px;
    border-radius: 3px;
    border: none;
    margin: 5px;
    text-align: center;
}

body {
    font-family: 'NanumSquareRound';
}

#usermail {
    text-decoration-line: underline;
    color: blue;
    text-align: center;
}

/* 미니 */
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css";
/* html, body {margin: 0; padding: 0%; background: green;} */
ul, li {list-style: none;}
span {vertical-align: baseline;}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  
}
.black-bg .white-bg {
  width: 180px;
  background: #fff;
  border-radius: 10px;
  padding: 20px;
  margin: 150px auto;
}
.black-bg .white-bg h4 {
  padding: 0 0 10px 0;
  border-bottom: 1px solid;
  font-size: 11px;
}
.black-bg .white-bg button {
  padding: 10px 0 0 0;
  border: none;
  background: #fff;
}
#start {
  width: 200px;
  margin: 0 auto;
  /* background: #fff; */
}
#start .content {
  text-align: center;
  padding: 10px 0;
}
#start .content ul {
}
#start .content li {
  padding: 10px 0;
}
#start .content li .label-box {
  padding: 5px 0;
}
#start .content li .label-box span {
}
#start .content li .input-box {
  
}
#start .content li .input-box .inputText {
}
#start .content li .input-box .overlap-btn {
  margin: 5px 0 0 0;
}
#start .content li .input-box i {
  padding: 0 0 0 5px;
}
#start .content li .input-box .chk {
  margin: 5px 0 0 0;
}
#start .content li .input-box .unchk {
  margin: 5px 0 0 0;
  color: #f00;
}
#start .finish {
  border-top: 1px solid ;
  text-align: center;
  padding: 10px 0;
}
#start .finish .finish-btn {
}


#signUp_page {
  padding: 25px;
    border-radius: 5px;
    background-color: #F4E7B6;
}

/* 엘 */
#Q_list_page {
  overflow: scroll;
  /* position: relative; */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.title {
  font-family: 'Sorts Mill Goudy', serif;
  color: #FFF500;
  font-size: 30px;
  font-weight: 600;
  /* position: fixed; */
  top: 80px;
  /* position: absolute; */
  display: flex;
  flex-direction: column;
  margin-bottom: 25px;
  /* padding: 0px 60px 20px 60px; */
  
  background-color: #920000;
}
.title > #title_line {
  height: 1px;
  width: 330px;
  background-color: rgba(255, 255, 255, 0.646);
  border-radius: 1px;
  margin: 34px 0 30px 0;

}
.title > p {
  font-family: 'NanumSquareRound';
  color: white;
  font-size: 16px;
  font-weight: normal;
}
.title > p:nth-child(5){
  color: rgba(255, 255, 255, 0.742);
  font-size: 13px;
  margin-top: 5px;
}
.newcontents {
  height: 450px;
  width: 350px;
  display: flex;
  /* position: sticky; */
  overflow: scroll;
  flex-direction: column;
  align-items: center;
  /* margin-top: 30px; */
  /* padding-top: 175px; */
  background-color: #9b1010;
  border-radius: 10px;

}
.newcontents > p {
  font-family: 'NanumSquareRound';
  color: white;
}
.newcontents > div {
  font-family: 'OFL Sorts Mill Goudy TT';
  font-size: 21px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}
.newcontents > div > div {
  display: flex;
  flex-direction: column;
  color: white;
  cursor: pointer;
  margin: 0 16px;
}
#giftbox {
  width: 73px;
  height: 73px;
  margin: 16px 0 5px 0;
  line-height: 100px;
  
}
#giftbox_25{
  width: 100px;
  height: 100px;
  margin-top: 36px;
}
#answer_group {
  width: 120px;
  height: 46px;
  margin: 30px;
  font-weight: bold;
  font-size: 16px;
  padding: 13px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  background-color: white;
  color: rgb(16, 16, 16);
}

/* 자몽 */
.celebrate-illust {
  display: flex;
  width: 300px;
  height: 300px;
  background: rgba(0, 0, 0, 0.3);
  margin: 20px;
}

.user-email {
  color: darkcyan;
}
.key_icon img{
  width:150px;
}
.password_guide{
  display: flex;
  flex-direction: column;
  margin-top:60px;
  font-size:23px;
  font-weight: bold;
}
.bottom_input{
  margin-top:70px;
}
.bottom_input input{
  width:220px;
  height: 30px;
}
.next_button{
  margin-top:50px;
  width:100px;
  height: 25px;
}
/*모달창 css*/
.password_represent{
  display: flex;
  flex-direction: column;
  padding:15px;
}
.password_represent .title{
  font-size: 20px;
  font-weight: bold;
}
.password_represent .mail{
 padding-top:20px;
 font-size:15px;
}
.password_represent .ok{
  padding-top: 27px;
  font-size:13px;
  font-weight: bold;
  color:#920000;
}
  .black-bg{
    position: absolute;
    top: 0;
    left: 0;
    height: 1000px; /*100%*/
    width: 1000px; /*100%*/
}
  hr{
    height: 2px;
    margin-top:40px;
    background-color: rgb(8, 8, 8);
    border: 0;
  }
  .white-bg{
    position: fixed;
    top: 55px;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    background:#F4E7B6;
    border-radius: 8px;
    width: 300px;
    height: 220px;
  }


/* - 메인컬러
    - 배경색(red) : 920000
- 서브컬러
    - yellow : FFF500
    - white : FFFFFF
    - black : 000000
    - beige : F4E7B6
- 폰트 컬러
    - yellow : FFF500
    - white : FFFFFF
    - black : 000000
    - gray : D9D9D9 */
</style>
