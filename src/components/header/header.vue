
<template>
   <div class="header">
       <div class="header_content">
            <div class="header_left">
                <img width="64" height="64" :src="seller.avatar" alt="">
            </div>
           <div class="header_right">
               <div class="shop-name">{{seller.name}}</div>
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

<style>
.header{
    width:100%;background-color: rgba(7,17,27,0.5);height:130px;
}
.header img{padding:22px 0 0 15px}
.header_left{width:30%;float: left;box-sizing: border-box}
.header_right{width:70%;float: right;box-sizing: border-box;padding:22px 0 0 10px;}
.header_right .shop-name{}
</style>
