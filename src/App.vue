<template>
  <!-- 리지 : 가입전 시작 view, 소개view, 가입완료view, 가입후 시작 view -->
  <div v-if="start_page==true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div><img id="logo_1" src="./assets/christmas-wreath.png"></div>
      <div><button @click="introBtnOn" type="button" class="btn">소개</button></div>
      <div><button @click="togo_login_page" type="button" class="btn" id="startBtn">시작하기</button></div>
      <!-- <div><button @click="pwBtnOn" type="button" onclick="" class="btn">비밀번호 찾기</button></div> -->
      <div id="teamname">teamname</div>
    </div>
  </div>

  <div v-if="introduction_page==true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div class="introductionBox">
        <p>Christmas Q25는<br>12월 1일부터 12월 25일 크리스마스까지<br>
        1년을 돌아볼 수 있는 질문들을<br>매일 하나씩 제공합니다.</p><br>
        <p>여러분들은 각 질문에 대한 답변을 작성하며<br>1년을 되돌아보고,<br>정리할 수 있을 것입니다.</p><br>
        <p>Christmas Q25가<br>1년동안의 소중했던 추억,<br>행복했던 기억,<br>고마웠던 사람을 떠올리게 하는<br>
            따뜻한 매개체가 되길 바라며</p><br>
        <p>모든 사용자분들의 행복한 연말을 기원합니다.</p><br>
        <div id="fromteam">team name<span><img src="./assets/02_stamp_empty.png" id="stampimg">&nbsp;올림&nbsp;&nbsp;</span></div>
      </div>
      <div><button @click="introBtnOff" type="button" class="btn" id="closeBtn">닫기</button></div>
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

  <div v-if="login_page==true">
    <div class="container">
      <div id="title">Christmas Q25</div>
      <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
      <div><img id="logo_2" src="./assets/christmas-wreath.png"></div>
      <div style="color: white; text-align: center;">
        <div id="welcomeWord">어서오세요<br>
        메리크리스마스 :)</div>
      </div>
      <form action="" method="post">
        <div>
          <input type="email" placeholder="이메일을 입력해주세요" v-model="email" id="inputBox" name="userEmail" required>
        </div>
        <div>
          <input type="password" placeholder="비밀번호를 입력해주세요" v-model="password" id="inputBox" name="userPw" required>
        </div>
        <div><input type="submit" value="로그인" @click="togo_Qlist_page" id="loginBtn"></div>
      </form>
      <!-- 로그인 버튼에 @click="checkInfo" 나중에 넣기 -->

      <div class="inlineBtn">
        <button type="button" @click="signUpBtnOn" id="signupBtn">회원가입</button>
        <span style="color: white;">|</span>
        <button type="button" @click="pwBtnOn" id="pwfindBtn">비밀번호 찾기</button>
      </div>
      <div id="teamname">teamname</div>

    <div class="black-bg" v-if="unknownPw == true">
      <div class="white-bg">
        <p>잘못된 비밀번호입니다</p>
        <p @click="checkInfo = false" class="ok">확인</p>
      </div>
    </div> -->

    </div>
  </div>

  <!-- 자몽 : 비번찾기 view -->
  <div v-if="pw_find_page == true">

    <!--모달창-->
    <!--<div class="modal_bg" v-if="pk_find_modal == true">
      <div class="pw_find_modalbox">
        <div class="password_represent">
          <span class="jm_modal_title">임시 비밀번호를</span>
          <span class="jm_modal_title">발송하였습니다</span>
          <span class="mail">메일함을 확인해주세요</span>
          <hr />
          <span @click="pk_find_modal = false" class="ok">확인</span>
        </div>
      </div>
    </div>-->

    <!--이메일 없는 경우 모달창 ) API작업후 추가-->
    <div class="modal_bg" v-if="no_email_modal == true">
      <div class="no_email_modalbox">
        <div class= "password_represent">
          <span class="jm_modal_title">등록되지 않은</span>
          <span class="jm_modal_title">이메일입니다</span>
          <hr>
        <span @click="no_email_modal= false" class="ok">확인</span>
        </div>
      </div>
      </div>

    <!--임시 비밀번호 발송 메인창-->

    <header class="home_icon">
      <i @click="home_button" class="material-icons">keyboard_arrow_left</i>
      <!-- <img @click="home_button" alt="Vue logo" src="./assets/left-arrow.png" /> -->
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

      <button class="jm_finish-btn" @click="no_email_modal = true">완료</button>
</div>

<!-- 자몽: 질문 답변하기 디자인 view -->
<!--글 발행기능 아직 구현 X => 공부필요-->
  <div v-if="qna_request_page==true">

<div class ="qna_requset_header">
  <i  class="material-icons">keyboard_arrow_left</i>
  <span class="request_day_number">{{question_25_content[gift_select].question_day}}</span>
</div>

<div class="qna_request_header_hr">
<hr>
</div>

<div class="request_img_icon">
<img src="./assets/08_question_pic01.png" alt="">
</div>

<div class="request_question">
  <span class = "question_number">{{question_25_content[gift_select].question_num}}</span>
  <span class = "question_contents">{{question_25_content[gift_select].question}}</span>
</div>

<!--답변창 180글자까지만 작성 가능  -->
<form id= "request_textarea" action="" method="POST">
<textarea v-model="qna_request" cols="40" rows="10"  placeholder="행복했던 순간을 떠올려보세요:)" maxlength="180"></textarea>
<br/>
<span id="counter">({{qna_request.length}}자 / 최대 180자)</span>
</form>

<div class="requset_share">
  <span class ="text">이미지 공유하기</span>
  <img src="./assets/07_download.png" alt="">
</div>

<div id="jm_button">
<button class="jm_finish-btn2" @click="submit">완료</button>
</div>
  </div>


  <!-- 미니 : 회원가입 view-->
  <div v-if="signUp_page==true" id="signUp_page">
    <div class="modal">
      <div class="modal_background check-password_form" v-if="pwformOpen == true">
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
          <h4>이메일 중복확인을<br>완료해주세요</h4>
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
              <input type="text" class="inputText" v-model="nickName" placeholder="닉네임을 입력해주세요!">
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>이메일을 입력해주세요!</span>
            </div>
            <div class="input-box email-input">
              <input type="email" class="inputText" v-model="email" placeholder="이메일을 입력해주세요!">
              <br>
              <button class="overlap-btn" @click="chkOverlap">중복확인</button>
              <img src="../src/assets/05_check.png" alt="중복확인" v-if="chkEmail == true">
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>아무나 작성할 수 없도록!<br>비밀번호를 입력해주세요</span>
            </div>
            <div class="input-box pw-input">
              <input type="password" class="inputText" id="inputPW" v-model="password" placeholder="비밀번호를 입력해주세요!" @change="chkInput">
              <p :class="[chkPw === false ? 'unchk' : 'chk']">*영문/숫자 포함 6자 이상</p>
            </div>
          </li>
        </ul>
        <p>confirm</p>
        <img id="stamp_img" src="../src/assets/02_stamp.png" alt="스탬프" v-if="pwformOpen == false && pwOpen == false && emailOpen == false && nickOpen == false">
      </div>
      <div id="wrap3">
        <button class="finish-btn" @click="submit">완료</button>
      </div>
    </div>

  </div>

  <!-- 미니 : 비번변경 view -->
  <div v-if="changePw_page==true" id="changePw_page">
    <div class="modal">
      <div class="modal_background" v-if="newpwOpen == true">
        <div class="modal_box">
          <h4>비밀번호 형식을 확인해주세요</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background check-oldpw" v-if="oldpwOpen == true">
        <div class="modal_box">
          <h4>기존 비밀번호가<br>일치하지 않습니다</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background" v-if="changepwOpen == true">
        <div class="modal_box">
          <h4>비밀번호가 변경되었습니다</h4>
          <button @click="togo_Qlist_page">확인</button>
        </div>
      </div>
    </div>
    <div class="content">
      <div id="wrap1">
        <i class="material-icons">keyboard_arrow_left</i>
      </div>
      <div id="wrap2">
        <h3>Change</h3>
        <img id="changePw_img" src="../src/assets/04_key.png" alt="비번변경">
        <ul>
          <li>
            <div class="label-box">
              <span>기존의 비밀번호를 입력해주세요!</span>
            </div>
            <div class="input-box">
              <input type="password" class="inputText" v-model="old_pw" placeholder="기존 비밀번호를 입력해주세요!">
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>새 비밀번호를 입력해주세요!</span>
            </div>
            <div class="input-box newPw-input">
              <input type="password" class="inputText" v-model="new_pw" placeholder="새 비밀번호를 입력해주세요!" @change="chkInput_new">
              <p :class="[chknewPw === false ? 'unchk' : 'chk']">*영문/숫자 포함 6자 이상</p>
            </div>
          </li>
        </ul>
        <p>confirm</p>
        <img id="stamp_img" src="../src/assets/02_stamp.png" alt="스탬프">
      </div>
      <div id="wrap3">
        <button class="finish-btn" @click="changepw_submit">완료</button>
      </div>
    </div>
  </div>

  <!-- 미니 : 회원탈퇴 view -->
  <div v-if="goodbye_page==true" id="goodbye_page">
    <div class="modal">
      <div class="modal_background" v-if="byeemailOpen == true">
        <div class="modal_box">
          <h4>이메일이 일치하지 않습니다</h4>
          <button @click="check">확인</button>
        </div>
      </div>
      <div class="modal_background" v-if="byepwOpen == true">
        <div class="modal_box">
          <h4>잘못된 비밀번호입니다</h4>
          <button @click="check">확인</button>
        </div>
      </div>
    </div>
    <div class="content">
      <div id="wrap1">
        <i @click="back_button" class="material-icons" >keyboard_arrow_left</i>
      </div>
      <div id="wrap2">
        <h3>Bye, Bye</h3>
        <img id="goodbye_img" src="../src/assets/10_goodbye.png" alt="회원탈퇴">
        <ul>
          <li>
            <div class="label-box">
              <span>이메일을 입력해주세요!</span>
            </div>
            <div class="input-box">
              <input type="email" class="inputText" v-model="bye_email" placeholder="이메일을 입력해주세요!">
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>비밀번호를 입력해주세요!</span>
            </div>
            <div class="input-box">
              <input type="password" class="inputText" v-model="bye_pw" placeholder="비밀번호를 입력해주세요!">
            </div>
          </li>
          <li>
            <div class="label-box">
              <span>비밀번호를 다시 한 번 입력해주세요!</span>
            </div>
            <div class="input-box repw-input">
              <input type="password" class="inputText" v-model="bye_repw" placeholder="비밀번호를 입력해주세요!" @change="chkRePw">
              <img src="../src/assets/05_check.png" alt="중복확인" v-if="RePw == true">
            </div>
          </li>
        </ul>
        <p>confirm</p>
        <img id="stamp_img" src="../src/assets/02_stamp.png" alt="스탬프">
      </div>
      <div id="wrap3">
        <button class="finish-btn" @click="bye_submit">완료</button>
      </div>
    </div>
  </div>
  <div v-if="goodbye_finish_page==true" id="goodbye_finish_page">
    <div class="title">Christmas Q25</div>
    <div class="subtitle">- 당신의 1년을 정리하는 25개의 질문 -</div>
    <img src="../src/assets/01_wreath.png">
    <span>탈퇴가 완료되었습니다<br>이용해주셔서 감사했어요 :)<br>행복한 연말 보내세요!</span>
    <button class="togo_home" @click="togo_home">홈으로</button>
    <div class="teamname">teamname</div>
  </div>

  <!-- 미니 : 설정 view -->
  <div v-if="setting_page==true" id="setting_page">
    <div class="modal">
      <div class="modal_background">
        <div class="modal_box">
          <h4 class="changepw-btn" @click="togo_changePw_page">비밀번호 변경</h4>
          <h4 class="goodbye-btn" @click="togo_goodbye_page">회원 탈퇴</h4>
          <button @click="check">닫기</button>
        </div>
      </div>
    </div>
  </div>


  <!-- 엘 : 질문리스트 view-->
  <div v-if="Q_list_page==true" id="Q_list_page">
    <img id="setting" src="../src/assets/09_setting.png" alt="설정" @click="togo_setting_page">

    <div class="title">
      <div><span class="userName">{{nickName}}</span>'s</div>
      <div>Christmas Q25</div>
      <div id="title_line"></div>
      <p>당신의 1년을 정리하는 25개의 질문</p>
      <p> 선물상자는 1번부터 열어주세요 :) </p>
    </div>

    <div class="newcontents">
      <div v-for="i in 8" :key="i">
        <div @click="questionList" v-for="j in 3" :key="j">
          <img :src="require(`@/assets/box/${3*(i-1)+j}.png`)" @click="request_up_btn" gift_select=(3*(i-1)+j) alt="" id='giftbox'>
          {{3*(i-1)+j}}
        </div>
        <div @click="questionList"  v-if='i==8'>
          <img src="./assets/box/25.png" alt="" id="giftbox_25">
          25
        </div>
      </div>
      <button id="answer_group" @click="togo_answerGrouping_page">답변 모아보기</button>
    </div>

  </div>



</template>

<script>

import question_25 from './assets/question_25.js';

export default {
  name: 'App',
  data() {
    return{
      start_page : true,
      introduction_page : false,
      Q_list_page : false,
      pw_find_page : false,
      signUp_page : false,
      complete_page : false,
      login_page : false,
      goodbye_page : false,
      goodbye_finish_page : false,
      changePw_page : false,
      setting_page : false,
      qna_request_page:false,

      email : '',

      nickName : '',
      질문데이터 : '부여된 랜덤 질문 리스트 데이터',
      ClickButton : false,
      nickOpen: false,
      password: '',
      pwOpen: false,
      chkPw: true,
      chkNum: /[0-9]/,
      chkEng: /[a-zA-Z]/,
      chkEmail: false,
      emailOpen: false,
      pwformOpen: false,
      RePw: false,
      bye_email: '',
      bye_pw:'',
      bye_repw:'',
      byeemailOpen: false,
      byepwOpen: false,
      old_pw: '',
      new_pw: '',
      newpwOpen: false,
      oldpwOpen: false,
      changepwOpen: false,
      chknewPw: true,
      pk_find_modal: false,
      no_email_modal: false,
      day:'Day 4',
      question_num:'Q4.',
      question_contents_1:'이번년도에 가장 행복했던 순간은 언제인가요?',
      question_contents_2:'누구와 함께였나요?',
      qna_request:[],
      question_25_content:question_25,
      gift_select:0,
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
      this.login_page=false;
      this.signUp_page=true;
    },
    // 닫기버튼이 아직 없어서 적용못함
    signUpBtnOff(){
      this.signUp_page=false;
    },
    pwBtnOn(){
      this.login_page=false;
      this.pw_find_page=true;
      this.Q_list_page = false;
    },
    togo_login_page(){
      this.start_page=false;
      this.login_page=true;
    },
    togo_Qlist_page(){
      this.Q_list_page=true;
      this.login_page=false;
      this.changePw_page=false;
      this.changepwOpen = false;
    },
    togo_home(){
      this.goodbye_finish_page = false;
      this.start_page = true;
      this.pw_find_page = false;
    },
    togo_changePw_page(){
      this.Q_list_page = false;
      this.setting_page = false;
      this.changePw_page = true;
    },
    togo_goodbye_page(){
      this.Q_list_page = false;
      this.setting_page = false;
      this.goodbye_page = true;
    },
    togo_setting_page(){
      this.setting_page = true;
    },
    togo_answerGrouping_page(){
      this.Q_list_page=false;
    },
    home_button(){
      this.pw_find_page=false;
      this.login_page=true;
    },
    back_button(){
      this.goodbye_page=true
      this.Q_list_page=false;
    },

    request_up_btn(){
      this.Q_list_page=false;
      this.qna_request_page=true;
    },

     request_down_btn(){
      this.Q_list_page=true;
      this.qna_request_page=false;
    },

    random_Q(){
      console.log(this.nickName)
    },

    submit(e){
      e.preventDefault();
      if (this.nickName == ''){
        this.nickOpen = true;
        this.emailOpen = false;
        this.pwOpen = false;
        this.pwformOpen = false;
      }
      else if (this.chkEmail == false){
        this.emailOpen = true;
        this.pwOpen = false;
        this.pwformOpen = false;
      }
      else if (this.password == ''){
        this.pwOpen = true;
        this.pwformOpen = false;
      }
      else if (this.chkPw == false){
        this.pwformOpen = true;
      }
      else {
        this.login_page=true;
        this.signUp_page=false;
      }
    },
    bye_submit(e){
      e.preventDefault();
      // api 받아와서 수정해야함
      if(this.bye_email == ''){
        this.byeemailOpen = true;
        this.byepwOpen = false;
      }
      else if(this.bye_pw == ''){
        this.byepwOpen = true;
      }
      else if(this.bye_email !== '' && this.bye_pw !== '' && this.bye_repw !== ''){
        this.goodbye_page = false;
        this.goodbye_finish_page = true;
      }
    },
    changepw_submit(e){
      e.preventDefault();
      if(this.chknewPw == false){
        this.newpwOpen = true;
        this.oldpwOpen = false;
        this.changepwOpen = false;
      }
      // api 받아와서 수정해야함
      else if(this.old_pw == ''){
        this.oldpwOpen = true;
        this.changepwOpen = false;
      }
      else if(this.chknewPw == true && this.old_pw !== ''){
        this.changepwOpen = true;
      }
    },
    check(){
      this.nickOpen = false;
      this.pwOpen = false;
      this.emailOpen = false;
      this.pwformOpen = false;
      this.byeemailOpen = false;
      this.byepwOpen = false;
      this.oldpwOpen = false;
      this.newpwOpen = false;
      this.setting_page = false;
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
    chkInput_new(){
      if (this.new_pw.length < 6){
        this.chknewPw = false;
      }
      if(!this.chkNum.test(this.new_pw)){
        this.chknewPw = false;
      }
      if(!this.chkEng.test(this.new_pw)){
        this.chknewPw = false;
      }
      if(this.new_pw.length > 5 && this.chkNum.test(this.new_pw) && this.chkEng.test(this.new_pw))
        this.chknewPw = true;
    },
    chkOverlap(){
      this.chkEmail = true;
    },
    chkRePw(){
      if(this.bye_pw == this.bye_repw){
        this.RePw = true;
      }
      else{
        this.RePw = false;
      }
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
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
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

body {
    font-family: 'NanumSquareRound';
}

#title {
    color: #FFF500;
    font-family: 'Sorts Mill Goudy', serif;
    font-size: 50px;
}

.subtitle {
    color: white;
    font-family: 'NanumSquareRound';
    font-size: 16px;
}

.btn {
    margin: 7px;
    background-color: white;
    border: none;
    border-radius: 6px;
    width: 170px; height: 42px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    font-family: 'NanumSquareRound';
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
    background-color: #F4E7B6;
    width: 305px;

    margin: 30px;
    margin-bottom: 10px;
    font-family: 'NanumSquareRound';
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
    width: 200px; height: 41px;
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
    width: 110px; height: 42px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    font-family: 'NanumSquareRound';

    margin-top: 8px;
    margin-bottom: 20px;
}

.inlineBtn {
  display: inline-block;
  margin-bottom: 20px;
}

#signupBtn, #pwfindBtn {
  border: none;
  color: white;
  background-color: transparent;
  font-size: 16px;
  font-family: 'NanumSquareRound';
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
ul, li {list-style: none;}
span {vertical-align: baseline;}

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
  background: rgba(217,217,217,0.7);
  position: absolute;
  left: -34px;
}
#setting_page .modal_background {
  width: 400px;
  height: 660px;
  background: rgba(217,217,217,0.7);
  position: absolute;
  left: -200px;
}
.modal_background .modal_box {
  width: 223px;
  height: 110px;
  background: #F4E7B6;
  border-radius: 10px;
  padding: 16px;
  margin: 246px 68px;
}
#setting_page .modal_background .modal_box {
  width: 223px;
  height: 110px;
  background: #F4E7B6;
  border-radius: 10px;
  padding: 16px;
  margin: 62px 0 0 112px;
}
.modal_background .modal_box h4 {
  padding: 20px 0 30px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
.modal_background.check-email .modal_box h4 {
  padding: 6px 0 18px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
.modal_background.check-oldpw .modal_box h4 {
  padding: 14px 0 18px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
#setting_page .modal_background .modal_box .changepw-btn {
  padding: 4px 0 12px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
#setting_page .modal_background .modal_box h4 {
  padding: 12px 0;
  border-bottom: 0.3px solid #000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
.modal_background .modal_box button {
  padding: 16px 0 0 0;
  border: none;
  background: #F4E7B6;
  color: #920000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}
#setting_page .modal_background .modal_box button {
  padding: 12px 0 0 0;
  border: none;
  background: #F4E7B6;
  color: #920000;
  font-size: 16px;
  font-weight: 800;
  font-family: 'NanumSquareRound';
}

/* #app {
  padding-top: 0;
} */
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
  font-family: 'NanumSquareRound';
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
  background-color: #F4E7B6;
  font-family: 'NanumSquareRound';
}
#wrap2 h3 {
  font-family: 'Sorts Mill Goudy', serif;
  font-weight: 500;
  font-size: 32px;
  border-bottom: 0.3px solid #000;
  padding: 10px;
}
#wrap2 #changePw_img {
  width: 84px;
  padding: 38px 0 0 0;
}
#wrap2 #goodbye_img {
  width: 105px;
  padding: 12px 0 0 0;
}
#wrap2 ul {
  padding: 28px 0 0 0;
}
#changePw_page #wrap2 ul {
  padding: 38px 0 0 0;
}
#goodbye_page #wrap2 ul {
  padding: 14px 0 0 0;
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
#goodbye_page #wrap2 li .input-box {
  position: relative;
  padding: 18px 0 28px 0;
}
#wrap2 li .input-box.email-input {
  position: relative;
  padding: 18px 0 28px 0;
}
#wrap2 li .input-box.pw-input {
  position: relative;
  padding: 18px 0 26px 0;
}
#changePw_page #wrap2 li .input-box.newPw-input {
  position: relative;
  padding: 18px 0 33px 0;
}
#goodbye_page #wrap2 li .input-box.repw-input {
  position: relative;
  padding: 18px 0 17px 0;
}
#goodbye_page #wrap2 li .input-box.repw-input img {
  position: absolute;
  color: #920000;
  width: 15px;
  height: 15px;
  top: 23px;
  padding: 0 0 0 6px;
}
#wrap2 li .input-box .inputText {
  width: 200px;
  height: 25px;
  border: none;
  border-radius: 5px;
}
#wrap2 li .input-box .inputText::placeholder {
  font-family: 'NanumSquareRound';
  text-align: center;
  font-weight: 800;
  color: #d9d9d9;
}
#wrap2 li .input-box .overlap-btn {
  margin: 10px 0 0 0;
  font-family: 'NanumSquareRound';
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
  font-family: 'Sorts Mill Goudy', serif;
  font-weight: 500;
  font-size: 16px;
  color: #000;
  text-align: right;
  padding: 0 35px 0 0;
}
#wrap2 #stamp_img {
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
  font-family: 'NanumSquareRound';
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

#goodbye_finish_page {

}
#goodbye_finish_page .title {
  font-family: 'Sorts Mill Goudy', serif;
  color: #FFF500;
  font-size: 42px;
  font-weight: 500;
  padding: 54px 0 10px 0;
}
#goodbye_finish_page .subtitle {
  font-family: 'NanumSquareRound';
  color: #fff;
  font-size: 16px;
  font-weight: 800;
}
#goodbye_finish_page img {
  width: 200px;
  padding: 57px 80px 30px 80px;
}
#goodbye_finish_page span {
  font-family: 'NanumSquareRound';
  color: #fff;
  font-size: 21px;
  font-weight: 800;
}
#goodbye_finish_page .togo_home {
  display: block;
  width: 112px;
  height: 42px;
  border: none;
  border-radius: 6px;
  color: #000;
  background: #fff;
  font-family: 'NanumSquareRound';
  font-size: 16px;
  font-weight: 800;
  margin: 33px 124px 14px 124px;
}
#goodbye_finish_page .teamname {
  font-family: 'NanumSquareRound';
  font-size: 16px;
  font-weight: 800;
  color: #fff;
}

/* 엘 */
#Q_list_page {
  overflow: scroll;
  position: relative;

  /* position: relative; */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

}
#Q_list_page #setting {
  position: absolute;
  width: 24px;
  top: 21px;
  right: 35px;
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

/* 자몽 - 임시 비밀번호 찾기 css */
header {
  display: flex;
  justify-content: flex-start;
  padding: 10px 0px 0px 0px;
}

.home_icon .material-icons {
  color: #fff;
  font-size: 42px;
  font-weight: 800;
}

/* .home_icon img {
  width: 20px;
  padding-right: 15px;
} */

.home_icon .back {
  color: white;
  padding-top: 8px;
  padding-right: 260px;
  font-size: 20px;
  font-family: "NanumSquareRound";
  font-weight: 800;
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

.jm_finish-btn {
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

/*자몽 - 임시 비밀번호 찾기 - 모달창 css*/

.modal_bg {
  width: 400px;
  height: 700px;
  background: rgba(223, 221, 221, 0.7);
  position: fixed;
  right: 275px;
  bottom: 10;
  left: 0;
  right: 0;
  top: 0;
  margin: auto;
}


.no_email_modalbox{
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
}

/*.pw_find_modalbox {
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
}*/
.modal_bg .password_represent {
  display: flex;
  flex-direction: column;
  padding: 15px;
}
.modal_bg .password_represent .jm_modal_title {
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

/* 자몽 - 질문 답변하기 css */

.qna_requset_header{
  display: flex;
  align-content: center;
  justify-content:space-evenly;
  padding-right:145px;
}

.qna_requset_header .material-icons {
  color: #fff;
  font-size: 42px;
  font-weight: 800;
}
.qna_request_header_hr hr {
  background-color: rgb(215, 213, 213);
  border: 0;
  height: 0.8px;
  margin-top: 10px;
  width:120px;
  margin-left : auto;
  margin-right : auto;
}

.qna_requset_header .request_day_number{
  padding-left:90px;

}

.request_img_icon img{
  width: 170px;
  height: 170px;
  padding-top: 20px;
}

.request_day_number {
  font-size: 30px;
  color: #FFFFFF;
  font-family: "NanumSquareRound";
  font-weight: 800
}

.question_number{
  padding: 6px;
}

.question_contents{
  margin-left : auto;
  margin-right : auto;
  }
.request_question{
  display: flex;
  flex-direction: column;
  color: #FFFFFF;
  font-weight: bold;
  font-size: 18px;
}

textarea:focus {outline: none;}
textarea::placeholder {
	color: #ccc;
  padding: 20px 5px;
}

#request_textarea{
  margin-top: 30px;
}

#request_textarea textarea{
  width:270px;
  height: 160px;
  border-radius: 2%;
  border: none;
  resize: none;
}
#request_textarea #counter{
color:rgb(153, 151, 151);
font-size: 11px;
padding-left:180px;
}

.jm_finish-btn2{
  font-family: "NanumSquareRound";
  font-size: 16px;
  font-weight: 800;
  background: #fff;
  border: none;
  border-radius: 6px;
  width: 120px;
  height: 42px;
  margin-top: 40px;
}

.requset_share{
  font-family: "NanumSquareRound";
  display: flex;
  justify-content: center;
  color: #fff;
  padding:3px 0px 0px 130px ;

}
.requset_share img{
  width: 20px;
  height:20px;
  padding-left: 15px;
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