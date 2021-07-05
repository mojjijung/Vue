<template>
    <div class="menu">
        <a v-for="menu in menulist" :key="menu">{{ menu }}</a>
    </div>

    <div  style="text-align:center; margin: auto;" >
        <img alt="Vue logo" style="width:50%;" src="./assets/mojjilogo.jpg">
        <button>반값할인</button>
    </div>

    <div>
        <h4 :style="style">{{ products[0] }}</h4>
        <p>{{ price1 }} 만원</p>
    </div>
    <div>
        <h4 :style="style">{{ products[1] }}</h4>
        <p>{{ price2 }} 만원</p>
    </div>
    <div>
        <h4 :style="style">{{ products[2] }}</h4>
        <p>{{ price3 }} 만원</p>
    </div>
</template>

<script>

    
export default {
  name: 'App',
  data(){
      return{
          //데이터 보관함 데이터 바인딩 실시간 자동 렌더링을 하기위해서임 
          price1 : 60,
          price2 : 80,
          price3 : 100,
          products : ['역삼동원룸','천호동원룸','마포구원룸'],
          menulist : ['Home', 'Shop' , 'About'],
      }
  },
  components: {
  }
}
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
</style>
