<template>
  <!-- 리지 : 가입전 시작 view, 소개view, 가입완료view, 가입후 시작 view -->
  <div v-if="start_page == true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div><img id="logo_1" src="./assets/christmas-wreath.png" /></div>
      <div>
        <button @click="introBtnOn" type="button" class="btn">소개</button>
      </div>
      <div>
        <button
          @click="togo_login_page"
          type="button"
          class="btn"
          id="startBtn"
        >
          시작하기
        </button>
      </div>
      <!-- <div><button @click="pwBtnOn" type="button" onclick="" class="btn">비밀번호 찾기</button></div> -->
      <div id="teamname">teamname</div>
    </div>
  </div>

  <div v-if="introduction_page == true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div class="introductionBox">
        <p>
          Christmas Q25는<br />12월 1일부터 12월 25일 크리스마스까지<br />
          1년을 돌아볼 수 있는 질문들을<br />매일 하나씩 제공합니다.
        </p>
        <br />
        <p>
          여러분들은 각 질문에 대한 답변을 작성하며<br />1년을 되돌아보고,<br />정리할
          수 있을 것입니다.
        </p>
        <br />
        <p>
          Christmas Q25가<br />1년동안의 소중했던 추억,<br />행복했던 기억,<br />고마웠던
          사람을 떠올리게 하는<br />
          따뜻한 매개체가 되길 바라며
        </p>
        <br />
        <p>모든 사용자분들의 행복한 연말을 기원합니다.</p>
        <br />
        <div id="fromteam">
          team name<span
            ><img
              src="./assets/02_stamp_empty.png"
              id="stampimg"
            />&nbsp;올림&nbsp;&nbsp;</span
          >
        </div>
      </div>
      <div>
        <button @click="introBtnOff" type="button" class="btn" id="closeBtn">
          닫기
        </button>
      </div>
    </div>
  </div>

  <!-- <div v-if="complete_page==true">
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
  </div> -->

  <div v-if="login_page == true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div><img id="logo_2" src="./assets/christmas-wreath.png" /></div>
      <div style="color: white; text-align: center">
        <div id="welcomeWord">
          어서오세요<br />
          메리크리스마스 :)
        </div>
      </div>
      <form action="" method="post">
        <div>
          <input
            type="email"
            placeholder="이메일을 입력해주세요"
            v-model="email"
            id="inputBox"
            name="userEmail"
            required
          />
        </div>
        <div>
          <input
            type="password"
            placeholder="비밀번호를 입력해주세요"
            v-model="password"
            id="inputBox"
            name="userPw"
            required
          />
        </div>
        <div>
          <input
            type="submit"
            value="로그인"
            @click="togo_Qlist_page"
            id="loginBtn"
          />
        </div>
      </form>
      <!-- 로그인 버튼에 @click="checkInfo" 나중에 넣기 -->

      <div class="inlineBtn">
        <button type="button" @click="signUpBtnOn" id="signupBtn">
          회원가입
        </button>
        <span style="color: white">|</span>
        <button type="button" @click="pwBtnOn" id="pwfindBtn">
          비밀번호 찾기
        </button>
      </div>
      <div id="teamname">teamname</div>
    </div>

    <!-- 로그인 실패 모달창 페이지 -->
    <!-- <div class="black-bg" v-if="unknownEmail == true">
      <div class="white-bg">
        <p>등록되지 않은 이메일입니다</p>
        <p @click="checkInfo = false" class="ok">확인</p>
      </div>
    </div>
    <div class="black-bg" v-if="unknownPw == true">
      <div class="white-bg">
        <p>잘못된 비밀번호입니다</p>
        <p @click="checkInfo = false" class="ok">확인</p>
      </div>
    </div> -->
  </div>

  <!-- 자몽 : 비번찾기 view -->

  <div v-if="pw_find_page == true">
    <!--모달창-->

    <div class="modal_bg" v-if="pk_find_modal == true">
      <div class="pw_find_modalbox">
        <div class="password_represent">
          <span class="title">임시 비밀번호를</span>
          <span class="title">발송하였습니다</span>
          <span class="mail">메일함을 확인해주세요</span>
          <hr />
          <span @click="pk_find_modal = false" class="ok">확인</span>
        </div>
      </div>
    </div>

    <!--이메일 없는 경우 모달창 ) API작업후 추가-->
    <!--<div class="modal_bg" v-if="no_email_modal == true">
      <div class="no_email_modalbox">
        <div class=  "password_represent">
          <span class="title">등록되지 않은</span>
          <span class="title">이메일입니다</span>
          <hr>
        <span @click="no_email_modal= false" class="ok">확인</span>
        </div>
      </div>
      </div>-->

    <!--임시 비밀번호 발송 메인창-->

    <header class="home_icon">
      <img @click="home_button" alt="Vue logo" src="./assets/left-arrow.png" />
      <span class="back">홈으로</span>
    </header>

    <div class="key_icon">
      <img alt="Vue logo" src="./assets/04_key.png" />
    </div>

    <div class="password_guide">
      <div class="info1">이메일을 입력해주세요!</div>
      <div class="info1">임시 비밀번호가 발송됩니다.</div>
    </div>

    <div>
      <input
        type="email"
        placeholder="이메일을 입력해주세요"
        v-model="email"
        id="email_inputBox2"
        name="userEmail"
        required
      />
    </div>

    <div id="wrap3">
      <button class="finish-btn2" @click="no_email_modal = true">완료</button>
    </div>
  </div>

  <!-- 미니 : 회원가입 view-->
  <div v-if="signUp_page == true" id="signUp_page">
    <div class="modal">
      <div
        class="modal_background check-password_form"
        v-if="pwformOpen == true"
      >
        <div class="modal_box">
          <h4>비밀번호 형식을 확인해주세요</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background check-password" v-if="pwOpen == true">
        <div class="modal_box">
          <h4>비밀번호를 입력해주세요</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background check-email" v-if="emailOpen == true">
        <div class="modal_box">
          <h4>이메일 중복확인을<br />완료해주세요</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background check-nickname" v-if="nickOpen == true">
        <div class="modal_box">
          <h4>닉네임을 입력해주세요</h4>
          <button @click="check">확인</button>
        </div>
      </div>
    </div>

    <div class="content">
      <div id="wrap1">
        <i class="material-icons">keyboard_arrow_left</i>
        <span>홈으로</span>
      </div>
      <div id="wrap2">
        <h3>Order</h3>
        <ul>
          <li>
            <div class="label-box">
              <span>페이지에 표기될 닉네임을 입력해주세요!</span>
            </div>
            <div class="input-box">
              <input
                type="text"
                class="inputText"
                v-model="nickName"
                placeholder="닉네임을 입력해주세요!"
              />
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>이메일을 입력해주세요!</span>
            </div>
            <div class="input-box email-input">
              <input
                type="email"
                class="inputText"
                v-model="email"
                placeholder="이메일을 입력해주세요!"
              />
              <br />
              <button class="overlap-btn" @click="chkOverlap">중복확인</button>
              <img
                src="../src/assets/05_check.png"
                alt="중복확인"
                v-if="chkEmail == true"
              />
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>아무나 작성할 수 없도록!<br />비밀번호를 입력해주세요</span>
            </div>
            <div class="input-box pw-input">
              <input
                type="password"
                class="inputText"
                id="inputPW"
                v-model="password"
                placeholder="비밀번호를 입력해주세요!"
                @change="chkInput"
              />
              <p :class="[chkPw === false ? 'unchk' : 'chk']">
                *영문/숫자 포함 6자 이상
              </p>
            </div>
          </li>
        </ul>
        <p>confirm</p>
        <img
          src="../src/assets/02_stamp.png"
          alt="스탬프"
          v-if="
            pwformOpen == false &&
            pwOpen == false &&
            emailOpen == false &&
            nickOpen == false
          "
        />
      </div>
      <div id="wrap3">
        <button class="finish-btn" @click="submit">완료</button>
      </div>
    </div>
  </div>

  <!-- 엘 : 질문리스트 view-->
  <div v-if="Q_list_page == true" id="Q_list_page">
    <div class="title">
      <div>
        <span class="userName">{{ nickName }}</span
        >'s
      </div>
      <div>Christmas Q25</div>
    </div>

    <div class="newcontents">
      <p>당신의 1년을 정리하는 25개의 질문</p>
      <div v-for="i in 8" :key="i">
        <div @click="random_Q" v-for="j in 3" :key="j">
          <!-- <img src="./assets/box/{{3*(i-1)+j}}.png" alt=""> -->
          <!-- <img src="'./assets/box/'+ {{3*(i-1)+j}} + '.png'" alt="" id='giftbox'> -->
          <img
            :src="require(`@/assets/box/${3 * (i - 1) + j}.png`)"
            alt=""
            id="giftbox"
          />
        </div>
        <div v-if="i == 8">25</div>
      </div>
      <button>답변 모아보기</button>
    </div>

    <!-- <img :src="require(`@/assets/images/${img}`)" />  -->
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      start_page: true,
      introduction_page: false,
      Q_list_page: false,
      pw_find_page: false,
      signUp_page: false,
      complete_page: false,
      login_page: false,
      email: "",
      nickName: "nickName 데이터",
      질문데이터: "부여된 랜덤 질문 리스트 데이터",
      ClickButton: false,
      nickOpen: false,
      password: "",
      pwOpen: false,
      chkPw: true,
      chkNum: /[0-9]/,
      chkEng: /[a-zA-Z]/,
      chkEmail: false,
      emailOpen: false,
      pwformOpen: false,
      pk_find_modal: false,
      no_email_modal: false,
    };
  },
  methods: {
    introBtnOn() {
      this.start_page = false;
      this.introduction_page = true;
    },
    introBtnOff() {
      this.start_page = true;
      this.introduction_page = false;
    },
    signUpBtnOn() {
      this.login_page = false;
      this.signUp_page = true;
    },
    // 닫기버튼이 아직 없어서 적용못함
    signUpBtnOff() {
      this.signUp_page = false;
    },
    pwBtnOn() {
      this.login_page = false;
      this.pw_find_page = true;
      this.Q_list_page = false;
    },
    togo_login_page() {
      this.start_page = false;
      this.login_page = true;
    },
    togo_Qlist_page() {
      this.Q_list_page = true;
      this.login_page = false;
    },
    home_button() {
      this.pw_find_page = false;
      this.login_page = true;
    },
    random_Q() {
      console.log(this.nickName);
    },
    submit(e) {
      e.preventDefault();
      if (this.nickName == "") {
        this.nickOpen = true;
        this.emailOpen = false;
        this.pwOpen = false;
        this.pwformOpen = false;
      } else if (this.chkEmail == false) {
        this.emailOpen = true;
        this.pwOpen = false;
        this.pwformOpen = false;
      } else if (this.password == "") {
        this.pwOpen = true;
        this.pwformOpen = false;
      } else if (this.chkPw == false) {
        this.pwformOpen = true;
      } else {
        this.login_page = true;
        this.signUp_page = false;
      }
    },
    check() {
      this.nickOpen = false;
      this.pwOpen = false;
      this.emailOpen = false;
      this.pwformOpen = false;
    },
    chkInput() {
      if (this.password.length < 6) {
        this.chkPw = false;
      }
      if (!this.chkNum.test(this.password)) {
        this.chkPw = false;
      }
      if (!this.chkEng.test(this.password)) {
        this.chkPw = false;
      }
      if (
        this.password.length > 5 &&
        this.chkNum.test(this.password) &&
        this.chkEng.test(this.password)
      )
        this.chkPw = true;
    },
    chkOverlap() {
      this.chkEmail = true;
    },
    // checkInfo(e){
    //   e.preventDefault();
    //   if (this.email != email){
    //     this.unknownEmail = true;
    //   }
    //   if (this.password != password){
    //     this.unknownPw = true;
    //   }
    //   else {
    //   this.Q_list_page = true;
    //   this.login_page = false;
    //   }
    // }
  },
  components: {},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Sorts+Mill+Goudy&display=swap");
@font-face {
  font-family: "NanumSquareRound";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/NanumSquareRound.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}
#app {
  margin-top: 20px;
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  display: flex;
  flex-direction: column;
  align-items: center;
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
  background-color: #fff;
  align-items: center;
  justify-content: center;
}
/* 리지 */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #920000;
  width: 360px;
  height: 640px;
  margin: 0 auto;
}
body {
  font-family: "NanumSquareRound";
}
#title {
  color: #fff500;
  font-family: "Sorts Mill Goudy", serif;
  font-size: 50px;
}
.subtitle {
  color: white;
  font-family: "NanumSquareRound";
  font-size: 16px;
}
.btn {
  margin: 7px;
  background-color: white;
  border: none;
  border-radius: 6px;
  width: 170px;
  height: 42px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  font-family: "NanumSquareRound";
}
#teamname {
  color: white;
  /* teamname을 맨 아래 고정시키는건 위에 있는 요소에 margin bottom 해서 하기. teamname에 마진탑 주면 로그인페이지에서 teamname이 아래로 밀림 */
}
/* 가입전 시작 view css */
#startBtn {
  margin-top: 23px;
  margin-bottom: 33px;
}
#logo_1 {
  width: 202px;
  height: 202px;

  /* padding: 60px; */
  display: block;
  margin: 0 auto;
  margin-top: 57px;
  margin-bottom: 56px;
}
/* 소개view css */
.introductionBox {
  padding: 20px;
  border-radius: 5px;
  background-color: #f4e7b6;
  width: 305px;
  margin: 30px;
  margin-bottom: 10px;
  font-family: "NanumSquareRound";
  font-weight: bold;
}
#fromteam {
  display: flex;
  float: right;
}
#stampimg {
  width: 53px;
  height: 59px;
  position: absolute;
}
/* 가입완료view css */
/* #usermail {
    text-decoration-line: underline;
    color: blue;
    text-align: center;
}
#Registration {
    color: black;
    width: 50px;
    padding: 60px;
    border: 1px solid black;
    margin: 40px;
    text-align: center;
    background-color: white;
} */
/* 가입후 시작 view css */
#inputBox {
  width: 200px;
  height: 41px;
  border-radius: 5px;
  border: none;
  margin: 5px;
  text-align: center;
  margin-bottom: 13px;
}
#loginBtn {
  background-color: white;
  border: none;
  border-radius: 6px;
  width: 110px;
  height: 42px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  font-family: "NanumSquareRound";
  margin-top: 8px;
  margin-bottom: 20px;
}
.inlineBtn {
  display: inline-block;
  margin-bottom: 20px;
}
#signupBtn,
#pwfindBtn {
  border: none;
  color: white;
  background-color: transparent;
  font-size: 16px;
  font-family: "NanumSquareRound";
  cursor: pointer;
}
#signupBtn {
  margin-right: 10px;
}
#pwfindBtn {
  margin-left: 10px;
}
#logo_2 {
  width: 133px;
  height: 133px;

  display: block;
  margin: 0 auto;
  margin-top: 25px;
  margin-bottom: 22px;
}
#welcomeWord {
  margin-bottom: 24px;
}
/* 미니 */
/* @import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"; */
@import "https://fonts.googleapis.com/icon?family=Material+Icons";
/* html, body {margin: 0; padding: 0%; background: green;} */
ul,
li {
  list-style: none;
}
span {
  vertical-align: baseline;
}
.modal {
  position: relative;
  z-index: 2;
}
.content {
  position: relative;
  z-index: 1;
}
.modal_background {
  width: 400px;
  height: 660px;
  background: rgba(217, 217, 217, 0.7);
  position: fixed;
  right: 285px;
}
.modal_background .modal_box {
  width: 223px;
  height: 110px;
  background: #f4e7b6;
  border-radius: 10px;
  padding: 16px;
  margin: 246px 68px;
}
.modal_background .modal_box h4 {
  padding: 20px 0 30px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: "NanumSquareRound";
}
.modal_background.check-email .modal_box h4 {
  padding: 14px 0 18px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: "NanumSquareRound";
}
.modal_background .modal_box button {
  padding: 16px 0 0 0;
  border: none;
  background: #f4e7b6;
  color: #920000;
  font-size: 16px;
  font-weight: 800;
  font-family: "NanumSquareRound";
}
#app {
  padding-top: 0;
  /* padding: 0; */
  /* position: relative; */
}
#wrap1 {
  text-align: left;
  height: 62px;
  position: relative;
}
#wrap1 .material-icons {
  position: absolute;
  top: 10px;
  /* left: 10px; */
  right: 308px;
  display: inline-block;
  color: #fff;
  font-size: 42px;
  font-weight: 800;
}
#wrap1 span {
  position: absolute;
  top: 18px;
  /* left: 50px; */
  right: 250px;
  display: inline-block;
  color: #fff;
  font-size: 21px;
  font-weight: 800;
  font-family: "NanumSquareRound";
  padding: 0 0 26px 0;
}
#wrap2 {
  /* text-align: center;
  padding: 10px 0; */
  position: relative;
  width: 300px;
  height: 490px;
  padding: 16px;
  border-radius: 5px;
  background-color: #f4e7b6;
  font-family: "NanumSquareRound";
}
#wrap2 h3 {
  font-family: "Sorts Mill Goudy", serif;
  font-weight: 500;
  font-size: 32px;
  border-bottom: 0.3px solid #000;
  padding: 10px;
}
#wrap2 ul {
  padding: 28px 0 0 0;
}
#wrap2 li {
}
#wrap2 li .label-box {
}
#wrap2 li .label-box span {
  font-weight: 800;
  font-size: 16px;
}
#wrap2 li .input-box {
  position: relative;
  padding: 18px 0 46px 0;
}
#wrap2 li .input-box.email-input {
  position: relative;
  padding: 18px 0 28px 0;
}
#wrap2 li .input-box.pw-input {
  position: relative;
  padding: 18px 0 26px 0;
}
#wrap2 li .input-box .inputText {
  width: 200px;
  height: 25px;
  border: none;
  border-radius: 5px;
}
#wrap2 li .input-box .inputText::placeholder {
  font-family: "NanumSquareRound";
  text-align: center;
  font-weight: 800;
  color: #d9d9d9;
}
#wrap2 li .input-box .overlap-btn {
  margin: 10px 0 0 0;
  font-family: "NanumSquareRound";
  border: none;
  border-radius: 6px;
  background: #920000;
  width: 49px;
  height: 24px;
  color: #fff;
  font-size: 8px;
  font-weight: 800;
}
#wrap2 li .input-box img {
  position: absolute;
  color: #920000;
  width: 15px;
  height: 15px;
  top: 57px;
  padding: 0 0 0 12px;
}
#wrap2 li .input-box p {
  font-size: 12px;
  font-weight: 800;
  padding: 13px 0 0 0;
}
#wrap2 li .input-box .chk {
}
#wrap2 li .input-box .unchk {
  color: #920000;
}
#wrap2 > p {
  font-family: "Sorts Mill Goudy", serif;
  font-weight: 500;
  font-size: 16px;
  color: #000;
  text-align: right;
  padding: 0 35px 0 0;
}
#wrap2 > img {
  width: 38px;
  position: absolute;
  right: 27px;
  bottom: 7px;
}
#wrap3 {
  text-align: center;
  padding: 16px 0 24px 0;
}
#wrap3 .finish-btn {
  font-family: "NanumSquareRound";
  font-size: 16px;
  font-weight: 800;
  background: #fff;
  border: none;
  border-radius: 6px;
  width: 168px;
  height: 42px;
}
#signUp_page {
  /* padding: 25px;
  border-radius: 5px;
  background-color: #F4E7B6; */
}
/* 엘 */
#Q_list_page {
  overflow: scroll;
}
.title {
  font-family: "Sorts Mill Goudy", serif;
  color: #fff500;
  font-size: 30px;
  font-weight: 600;
}
.newcontents {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
}
.newcontents > p {
  font-family: "NanumSquareRound";
  color: white;
}
.newcontents > div {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
#giftbox {
  width: 80px;
  height: 80px;
  margin: 12px;
  margin-bottom: 25px;
  line-height: 100px;
}
/* 자몽 */
header {
  display: flex;
  justify-content: flex-start;
  padding: 20px 0px 0px 0px;
}

.home_icon img {
  width: 20px;
  padding-right: 15px;
}

.home_icon .back {
  color: white;
  padding-right: 270px;
  font-size: 20px;
}

#email_inputBox2 {
  width: 220px;
  height: 25px;
  border-radius: 5px;
  border: none;
  margin: 5px;
  text-align: center;
  margin-top: 50px;
}

.key_icon img {
  padding-top: 100px;
  width: 120px;
}
.password_guide {
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  font-size: 18px;
  color: white;
}

.finish-btn2 {
  font-family: "NanumSquareRound";
  font-size: 16px;
  font-weight: 800;
  background: #fff;
  border: none;
  border-radius: 6px;
  width: 168px;
  height: 42px;
  margin-top: 100px;
}

/*모달창 css*/

.modal_bg {
  width: 100%;
  height: 100%;
  background: rgba(223, 221, 221, 0.7);
  position: fixed;
  right: 275px;
  bottom: 0;
  left: 0;
  right: 0;
  top: 0;
  margin: auto;
}

/*.no_email_modalbox{
    position: fixed;
    top: -140px;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    background:#F4E7B6;
    border-radius: 8px;
    width: 260px;
    height: 140px;
}*/

.pw_find_modalbox {
  position: fixed;
  top: -140px;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  background: #f4e7b6;
  border-radius: 8px;
  width: 260px;
  height: 170px;
}

.modal_bg .password_represent {
  display: flex;
  flex-direction: column;
  padding: 15px;
}
.modal_bg .password_represent .title {
  font-family: "NanumSquareRound";
  color: black;
  font-size: 18px;
  font-weight: bold;
}
.modal_bg .password_represent .mail {
  font-family: "NanumSquareRound";
  color: black;
  font-size: 15px;
  font-weight: 1000;
  margin-top: 10px;
}
.modal_bg hr {
  background-color: rgb(57, 56, 56);
  border: 0;
  height: 0.8px;
  margin-top: 10px;
}

.modal_bg .password_represent .ok {
  font-size: 13px;
  font-weight: bold;
  color: #920000;
  margin-top: 30px;
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
