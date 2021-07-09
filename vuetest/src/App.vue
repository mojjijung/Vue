<template>
 
    <!-- 데이터를 전송해주고, 등록하고 사용한다. props : 자식에게 데이터 보내는 방법 -->
    <Modal :rooms="rooms" :roomid="roomid" :modalstatus="modalstatus" @close="handlePointStorageClose"/>

    <div class="menu">
        <a v-for="(menu,i) in menulist" :key="i">{{ menu }}</a>
    </div>

    <!-- 컴포넌트 : 코드가 아름다워 -->
    <Discount/>

    <div style="text-align: center; margin: auto;">
        <img alt="Vue logo" style="width: 50%;" src="./assets/mojjilogo.jpg" />
    </div>


    
     <Card v-for="(roomslist,i) in rooms" :key="i" :roomid="i" :room="rooms[i]" @open="modalOpen" />
 
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
            modalOpen(modalstatus, roomid){
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
        width: 100%; height: 100%;
        background: rgba(0,0,0,0,5);
        position: fixed; padding: 20px
    }
    .white-bg{
        width: 100%; background: white;
        border-radius: 8px;
        padding: 20px;
    }
    

</style>