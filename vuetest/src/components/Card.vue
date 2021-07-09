<template>
     <div>
        <img :src="room.image" class="room-img" />
        <!-- <h4 @click="modalstatus = true; ">{{room.title}}</h4> -->
        <h4 @click="$emit('open', true ,this.roomid)">{{room.title}}</h4>      
        <p>{{room.price}}원 </p>    
        <!-- <p>{{roomid}}</p> -->
     </div> 
</template>


<script>
export default{
    name : 'Card',
    // 데이터를 받아왔다라는 문법이 props
    props : {
        room : Object,
        roomid : Number,
        modalstatus : Boolean,
        open: Function
    },
}
</script>

<style>

</style>
        