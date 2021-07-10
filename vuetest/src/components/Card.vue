
//부모가 건네준 데이터는 수정할 수 없다. 
<template>
     <div>
        <img :src="room.image" class="room-img" />
        <!-- <h4 @click="modalstatus = true; ">{{room.title}}</h4> -->
        <!-- $ Vue 에 있는 특별한 변수 --> 
        <!-- 내가 한 방법 -->
        <!-- <h4 @click="$emit('open', true ,this.roomid)">{{room.title}}</h4> -->
         <!-- 강사가 한 방법 -->
         <!-- <h4 @click="$emit('open',i)">{{room.title}}</h4> -->
         <!-- 코드를 줄이고 싶으면 method를 만들고 한다. -->
         <h4 @click="openModalChild">{{room.title}}</h4> 
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
    methods : {
        openModalChild(){
            //alert(this.room.id);
            this.$emit('open', this.room.id);
        }
    }
}
</script>

<style>

</style>
        