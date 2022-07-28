<template>

<div class ="day">
  <span class="day_number">{{day}}</span>
  <hr>
</div>

<div class="img_icon">
<img src="./assets/gift.png" alt="">
</div>

<div class="question">
  <span class = "question_number">{{question_num}}</span>
  <span class = "question_contents">{{question_contents_1}}</span>
  <span class = "question_contents">{{question_contents_2}}</span>

</div>

<form action="" method="POST">
  <input type="text" id="qusetion_answer" placeholder="행복했던 순간을 떠올려보세요:)">
</form>

<div class="text_share">
  <span class ="text">내 답변 공유하기</span>
  <img src="./assets/share.png" alt="">
</div>

<div class="text_input_button">
<button class="finish-btn" @click="submit">완료</button>
</div>

</template>
<script>

export default {
  name: 'App',
   data() {
    return{
      day:'Day 4',
      question_num:'Q4.',
      question_contents_1:'이번년도에 가장 행복했던 순간은 언제인가요?',
      question_contents_2:'누구와 함께였나요?'
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
  padding-top: 40px;
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




.img_icon img{
  width: 170px;
  height: 170px;
  padding: 20px;
}

.day {
  font-size: 30px;
  color: #FFFFFF;
}

.day hr{
  margin-top: 15px;
  width:150px;
}

.question_number{
  padding: 6px;
}

.question{
  display: flex;
  flex-direction: column;
  color: #FFFFFF;
  font-weight: bold;
  font-size: 16px;

}

.question_answer{
  outline: none;

}

input:focus {outline: none;}

form{
  padding-top: 30px;
}

#qusetion_answer {
  width: 250px;
  height: 150px;
  border-radius: 5%;
  border: none;
}

.text_share{
  display: flex;
  justify-content: center;
  color: #fff;
  padding:10px 0px 0px 80px ;

}
.text_share img{
  width: 20px;
  height:20px;
  padding-left: 15px;
}

.text_input_button{
padding: 30px;
}

.text_input_button .finish-btn{
  background-color: #fff;
  border: none;
  width: 100px;
  height: 40px;
  border-radius:5%;
  font-size: 13px;
  font-weight:bold;
}

/*- yellow : FFF500
- white : FFFFFF
- black : 000000
- gray : D9D9D9*/

</style>
