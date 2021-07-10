// 1. Vue파일 import
// 2. 등록하고 사용 v-if="isModalViewed" @close-modal="isModalViewed = false"
// props는 read-only임 받아온거 수정하면 큰일남
// 부모컴포넌트에서 쓰는 데이터면 부모컴포넌트에 만들어주는게 좋다

<template>
   <!-- 모달창 -->
    <div class="black-bg" v-if="modalstatus == true" >
        <div class="white-bg">
            <h4>Child-Modal</h4>
            <h4>{{ rooms[roomid].title }}</h4>
            <img :src="rooms[roomid].image" class="room-img" />
            <p> {{ rooms[roomid].content }}</p>
            <!-- input : 입력할때마다 실행시켜주삼 -->
            <!-- <input @input="month = $event.target.value"> -->
            <!-- 축약버전이 있음 input 류에  붙일 수 있음 -->
            <input v-model="month">
            <br>
            <br>
            <input v-model="month" type="range" min="1" max="12">
            <!-- <input v-model.number="month"> -->
            <!-- <textarea v-model="month"></textarea> -->
            <!-- <select v-model="month">
                 <option v-for="i in 12" :key="i" >{{i}}</option>
            </select> -->
            <p> {{ month }} 개월 선택함 :  {{ rooms[roomid].price * month }} 원</p>
            <!-- <Button @click="$emit('close', false)">닫기</button> -->
            <Button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
   <!-- 모달창 -->
</template>

<script>
export default{
    name : 'Modal',    
    data(){
      return{
          month : 1,
          // input은 항상 string으로 인식한다.
      }  
    },
    watch: {
      //데이터 감시를 위한 프로세스
      // 감시하고싶은 데이터형을 함수로 만들어준다. 
      // b : 변경 전 데이터 , a :변경 후 데이터
      // month(a,b){
      month(a){
          // month라는 데이터가 변할때마다 여기 함수가 실행된다.
          if( a > 12 ){   
              alert('개월수가 정확하지 않습니다. 1 ~ 12 개월 수 안에서 선택해주세요.')    
          }
          
          if( isNaN(a) ){
              alert('숫자만 입력해주세요.')
              this.month = 1
          }
      },
    },
    // 데이터를 받아왔다라는 문법이 props
    props : {
        rooms : Array,
        roomid : Number,
        modalstatus : Boolean,
        close: Function
    },
}
</script>

<style>

</style>
        