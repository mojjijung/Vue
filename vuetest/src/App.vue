<template>
 
    <!-- 데이터를 전송해주고, 등록하고 사용한다. props : 자식에게 데이터 보내는 방법 -->
    <!-- <Modal :rooms="rooms" :roomid="roomid" :modalstatus="modalstatus" @close="handlePointStorageClose"/> -->


    <!-- 조건부로 class명을 넣으려면 { 클래스명: 조건 } -->
    <!-- <div class="start" :class="{end : modalstatus}">
        <Modal :rooms="rooms" :roomid="roomid" :modalstatus="modalstatus" @closeModal="modalstatus=false"/>    
    </div> -->

    <!-- 더 쉽게 애니메이션 넣는 방법 transisition -->
    <transition name="fade">
        <Modal :rooms="rooms" :roomid="roomid" :modalstatus="modalstatus" @closeModal="modalstatus=false"/> 
    </transition>
    
    <div class="menu">
        <a v-for="(menu,i) in menulist" :key="i">{{ menu }}</a>
    </div>

    <!-- 컴포넌트 : 코드가 아름다워 -->
    <Discount/>

    <div style="text-align: center; margin: auto;">
        <img alt="Vue logo" style="width: 50%;" src="./assets/mojjilogo.jpg" />
    </div>


    <!-- 내가 한 방법 -->
    <!-- <Card v-for="(roomslist,i) in rooms" :key="i" :roomid="i" :room="rooms[i]" @open="openModal" /> -->
    <!-- 강사가 한 방법 -->
    <Card @open="modalstatus = true; roomid = i" v-for="(roomslist,i) in rooms" :key="i" :room="rooms[i]" />

    <!-- <div v-for="(roomslist,i) in rooms" :key="i" >
        <img :src="rooms[i].image" class="room-img" />
        <h4 @click="modalstatus = true; roomid = i ">{{ rooms[i].title }}</h4>
        <p>{{ rooms[i].price }} 원</p>    
    </div>  -->


</template>

<script>
    
    import { data } from './assets/oneroom.js';
    import Discount from './components/Discount.vue';
    import Modal from './components/Modal.vue';
    import Card from './components/Card.vue';
    
    export default {
        name: 'App',
        data() {
            return {
                //데이터 보관함 데이터 바인딩 실시간 자동 렌더링을 하기위해서임
                //동적인 UI만드는법 : 
                // 1. UI의 현재 상태를 데이터로 저장해둠
                // 2. 현재 데이터에 따라 UI가 어떻게 보일지 작성
                roomid : 0,
                rooms : data,
                modalstatus : false,
                price1: 60,
                price2: 80,
                price3: 100,
                cnt: [0, 0, 0],
                products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
                menulist: ['Home', 'Shop', 'About'],
            };
        },
        methods: {
            //함수는 여기서 다 만들어준다.
            increase() {
                this.cnt += 1;
            },
            handlePointStorageClose(close){
                this.modalstatus = close;
            },
            openModal(modalstatus, roomid){
                this.modalstatus = modalstatus;
                this.roomid = roomid;
            }
        },
        components: {
            // 컴포넌트 등록하기
            Discount : Discount,
            Modal : Modal,
            Card : Card,
        },
    };
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .menu {
        background: darkslateblue;
        padding: 15px;
        border-radius: 5px;
    }

    .menu a {
        color: white;
        padding: 10px;
    }

    .room-img {
        width: 100%;
        margin-top: 40px;
    }
    
    body{
        margin : 0
    }
    div {
        box-sizing: border-box;
    }
    .black-bg{
        position: fixed;
        top: 0;
        left: 0;
        display: block;
        height: 100%;
        width: 100%;
       
        padding : 20px;
        z-index: 100;
       background-color: rgba(0, 0, 0, 0.5);
          border-radius: 2px;
          box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
          transition: all 0.3s ease;
    }
    .white-bg{
        width: 100%; background: white;
        border-radius: 8px;
        padding: 20px;
    }
    .start{
        opacity: 0; 
        transition: all 1s;
    }
    .end{
        opacity: 1;
    }
    
    .fade-enter-from{
         opacity: 0;        
        transform : translateY(-1000px);
        /* 시작할때 동작구문 */
    }
    .fade-enter-active{
         transition: all 1s;
    }
    .fade-enter-to{
         opacity: 1;
        transform : translateY(0px);
         /* 끝날때 동작구문 */
    }
        
    .fade-leave-from{
         opacity: 1;        
        /* 시작할때 동작구문 */
    }
    .fade-leave-active{
         transition: all 1s;
    }
    .fade-leave-to{
         opacity: 0;
         /* 끝날때 동작구문 */
    }
    

</style>