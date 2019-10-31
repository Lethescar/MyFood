<template>
    <div>
        <navTop></navTop>
        <div  class="lose">

       
        <div class="three_day">
                <div class="three_top">
                    <h1>燃烧我的卡路里</h1>
                    <h2>一日三餐边吃边享<span>"瘦"</span></h2>
                    <div class="lose_img">
                        <img  :src="`http://127.0.0.1:3000/img/`+list[0].picture" alt="">
                        <div class="lose_content">
                            <p>{{list[0].text}}
                            </p>
                            <div class="bot">
                                <router-link :to="`/mealslist/${list[0].kid}`" class="jump" >
                                    {{list[0].title}}
                                </router-link>
                                 <router-link :to="`/mealslist/${list[1].kid}`" class="jump" >
                                    {{list[1].title}}
                                </router-link>
                                 <router-link :to="`/mealslist/${list[2].kid}`" class="jump" >
                                    {{list[2].title}}
                                </router-link>
                                 <router-link :to="`/mealslist/${list[3].kid}`" class="jump" >
                                    {{list[3].title}}
                                </router-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        <div class="lose_left" v-for='(item,index) of list' :key="index">
            <div class="box">
                <div class="box_one">
                    <div class="box_left">
                        <img :src="`http://127.0.0.1:3000/img/`+item.tupian" alt="">
                    </div>
                    <div class="box_right">
                        <a href="#">{{item.title}}</a>
                         <p class="box1">{{item.content}}</p>
                         <router-link :to="`/mealslist/${item.kid}`" class="jump1" >
                            <p>MORE</p>
                         </router-link>
                         
                    </div> 
                   
                </div>
                
            </div>
        </div>
        <div class="lose_right">
        </div>
         </div>
        <bottom></bottom>
    </div>
</template>
<script>
import navTop from '@/components/navTop.vue';
import bottom from '@/components/bottom.vue';
export default {
    components:{navTop,bottom},
    data(){
        return{
            list:[]
        }
    },
        created(){
        this.loadmenu_two()
    },
    methods:{
        loadmenu_two(){
           this.axios.get("index/menu_two").then(result=>{
               this.list=result.data.data;
               console.log(this.list);
           })
        },
    }
    
}
</script>
<style>
body{background-color:#f4f4f4;}
    .lose{max-width:1100px;margin:0 auto;margin-top:140px;}
    .lose_left{width:100%;}
    .three_day{padding-bottom: 45px;text-align:left;width:70%;}
    .three_top>h1{font-size: 28px;font-weight: bold;color: #333;margin-bottom: 0;cursor: pointer;}
    .three_top>h2{width: 100%;height: 56px;overflow: hidden;font-size: 18px;color: #333;margin-bottom: 0;cursor: pointer;}
    .lose_img img{width: 180px;height: 120px;margin-right: 15px;float:left;}
    .lose_content p{max-height: 75px;overflow: hidden;line-height: 25px;color: #666;font-size: 14px;}
    .bot a{margin: 0 5px 0 0;background-color: #fff;text-decoration:none;border: 1px solid #e8e8e8;height: 28px;line-height: 28px;padding: 6px 6px;border-radius: 3px;color: #999;font-size: 15px;overflow:hidden;}
    .bot a:hover{color:#d8316c;border:1px solid #d8316c;}
    .box{background: #fff;width: 100%;box-shadow: 0 0 1px 0 #f1f1f1;padding-bottom: 20px;border-radius: 5px;}
    .box_left img{width: 240px;height: 225px;}
    .box_left{width:40%;}
    .box_right{width:90%;}
    .box_right a{display: block;max-height: 60px;line-height: 60px;width: 345px;overflow: hidden;color: #222;text-decoration: none;font-size: 20px;}
    .box_right a:hover{color:#d8316c;}
    .box_right:first-child(a){text-align:left;}
    .box_right p{max-height: 75px;overflow: hidden;color: #999;} 
    .box_right .box1{line-height: 25px;;} 
    .box_one{padding:2%;display:flex;}
    .box_right .jump1{display: block;border: 1px solid #f03271;    width:85px;
    height:35px;margin-top:3.5%;text-align: center;line-height: 35px;}
    .jump1 p{color:#d8316c;}
    .three_top>h2>span{font-size:26px;color:#d8316c;}
</style>