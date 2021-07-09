// 1. Vue파일 import
// 2. 등록하고 사용
v-if="isModalViewed" @close-modal="isModalViewed = false"
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
            <p> {{ rooms[roomid].price }} 원</p>
            <Button @click="$emit('close', false)">닫기</button>
        </div>
    </div>
   <!-- 모달창 -->
</template>

<script>
export default{
    name : 'Modal',
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
        