// 1. Vue파일 import
// 2. 등록하고 사용
v-if="isModalViewed" @close-modal="isModalViewed = false"


<template>
   <!-- 모달창 -->
    <div class="black-bg" v-if="modalstatus == true" >
        <div class="white-bg">
            <h4>Child-Modal</h4>
            <h4>{{ rooms[roomid].title }}</h4>
            <img :src="rooms[roomid].image" class="room-img" />
            <p> {{ rooms[roomid].content }}</p>
            <p> {{ rooms[roomid].price }} 원</p>
            <Button @click="$emit('close', false)">닫기</button>
        </div>
    </div>
   <!-- 모달창 -->
</template>

<script>
export default{
    name : 'Modal',
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
        