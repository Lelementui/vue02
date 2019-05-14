
<template>
   <div class="header">
       <div class="header_content">
            <div class="header_left">
                <img width="64" height="64" :src="seller.avatar" alt="">
            </div>
           <div class="header_right">
               <div class="shop-name">{{seller.name}}</div>
               <div class="shop-peisong">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
               <div class="shop-peisong">{{seller.supports[0].description}}</div>
           </div>
       </div>
   </div>
</template>

<script>
export default {
    data(){
      return{
          
      }
    },
    props:{
        seller:{
            type:Object
        }
    }
}
</script>

<style lang="stylus">
.header
    width:100%;background-color: rgba(7,17,27,0.5);height:12rem
    .header_left
        width:25%;float: left;box-sizing: border-box;padding:1.3rem  0 0 1rem
    .header_right
        width:70%;float: right;box-sizing: border-box;padding:1rem 0 0 0.1rem;height:8rem
    .shop-name
        color:#fff;height:2.2rem;font-size:1.4rem;font-weight:600
    .shop-peisong 
        font-size: 1.2rem;color: #fff
</style>
