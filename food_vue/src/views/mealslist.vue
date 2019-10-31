<template>
    <div class="lmenu_three">
        <navTop></navTop>
        <div class="lmenu_top">
        <div class="lmenu_div">
            <div class="lmenu_tab">
                <span class="lmenu_word" @click="jump">食谱</span>
                <span class="lmenu_word2">·{{list[0].title}}</span>
            </div>
            <div class="limg_div">
                 <img :src="`http://127.0.0.1:3000/img/`+list[0].img" alt="" class="lmenu_img">
            </div>
                <p class="lmenu_p">{{list[0].title}}</p>
                <div v-if="list">
                    <div v-for="(item,index) in list" :key="index"> 
                    <div class="lcontent" >{{item.day}}</div>
                    <div class="lcontent">早餐:{{item.breakfast}}</div>
                    <p class="lcontent">午餐：{{item.lunch}}</p>    
                    <p class="lcontent">晚餐：{{item.dinner}}</p>
                    <div class="limg_div">
                        <img :src="`http://127.0.0.1:3000/img/`+item.d_img" alt="" class="lcontent_img">
                    </div>
                </div> 
               <p class="limg_bottom">{{list[0].content}}</p>
        </div>
        </div>
        <menuRecom></menuRecom>
        </div>
        <bottom></bottom>
    </div> 
</template>
<script>
import navTop from '@/components/navTop.vue';
import bottom from '@/components/bottom.vue';
import menuRecom from '@/components/detail/menuRecom.vue';
export default {
    components:{navTop,bottom,menuRecom},
    data() {
        return {
            list:[],
        }
    },
    props:["dayId"],
    created() {
        this.loadMeal_days();
    },
  methods:{
        loadMeal_days(){
           this.axios.get("index/meal_days",{params:{dayId:this.dayId}}).then(result=>{
               this.list=result.data;
           })
        },
        jump(){
            this.$router.push("/menu_two")
        }
    }
}
</script>
<style>
    .lmenu_three{}
    .lmenu_top{max-width: 60%;max-width: 1100px;margin: 0 auto;margin-top:120px;display:flex;justify-content: space-between;}
    .lmenu_div{width:70%;}
    .limg_div{max-width: 100%;}
    .limg_div img{width:100%}
    .lmenu_tab{text-align: left;margin-bottom: 40px;}
    .lmenu_word{color: #D8316C;font-size:22px;cursor: pointer;}
    .lmenu_word2{font-size: 24px;}
    .lmenu_img{text-align: left;margin-bottom: 25px;}
    .lmenu_p{font-size: 24px;color: #272B2C;font-weight:800;margin-bottom:0;line-height: 40px;text-align: left;margin-top: 0}
    .lcontent{text-align: left;line-height:40px;letter-spacing: 1px;margin-bottom: 0;margin-top: 0}
    .limg_bottom{text-align: left;text-indent: 2em;letter-spacing: 1px;line-height: 40px;}
</style>
