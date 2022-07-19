<template>
  <div id="scenario1_4">
    <div class="title">
      <div>Christmas Q25</div>
      <div>당신의 1년을 정리하는 25개의 질문</div>
    </div>

    <div class="celebrate-illust">
    </div>
    

    <div class="text-content">
      <p>생성이 완료되었어요 :)</p>
      <a class="user-email">user@gmail.com</a>
      <p>메일함을 확인해주세요!</p>
    </div>

    <div>
      <button>바로가기</button>
    </div>
  </div>

  <div id="scenario2_3">
    <div class="title">
      <div><span class="userName">{{nickname}}</span>'s</div> 
      <div>Christmas Q25</div>
    </div>
    
    <div class="newcontents">
      <p>당신의 1년을 정리하는 25개의 질문</p>
      <div v-for="i in 8" :key="i">
        <div @click="random_Q" v-for="j in 3" :key="j">{{3*(i-1)+j}}</div>
        <div v-if='i==8'>25</div>
      </div>
      <button>답변 모아보기</button>
    </div>
    
  </div>
  
</template>

<script>


export default {
  name: 'App',
  data() {
    return{
      nickname : 'nickName 데이터',
      질문데이터 : '부여된 랜덤 질문 리스트 데이터'
    }
  },
  methods: {
    random_Q(){
      console.log(this.nickname)
    }
  },
  components: {
  }
}
</script>

<style>
#scenario1_4 {
  display: none;
}
#scenario2_3 {
  overflow: scroll;

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  display: flex;
  flex-direction: column;
  align-items:  center;
  /* justify-content: center; */
  
  background-color: white;
  border-radius: 5px;
  padding: 20px;
  padding-top: 70px;
  width: 375px;
  height: 667px;
}

body {
  display: flex;
  background-color: rgb(19, 112, 2);
  align-items:  center;
  justify-content: center;
} 
.title {
  font-size: 30px;
  font-weight: 600;
}

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

.newcontents {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
}
.newcontents > div {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
.newcontents > div div {
  width: 100px;
  height: 100px;
  background-color: rgb(219, 64, 17);
  margin: 8px;
  border-radius: 3px;
  line-height: 100px;
  color: white;
  font-size: 20px;
}
</style>
