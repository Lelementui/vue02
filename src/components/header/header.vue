
<template>
    <div class="header">
        <div class="header_content">
                <div class="header_left">
                    <img width="64" height="64" :src="seller.avatar" alt="">
                </div>
            <div class="header_right">
                <div class="shop-name">{{seller.name}}</div>
                <div class="shop-peisong">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
                <div v-if="seller.supports" class="shop-content">
                    <div v-if="seller.supports" class="shop-peisong">{{seller.supports[0].description}}</div>
                    <div v-if="seller.supports" class="shop-active-num" @click="showDialog">{{seller.supports.length}}个</div>
                </div>
            </div>
            <div style="clear:both"></div>
            <div class="all_notice" @click="showDialog">
                    <span class="notice_one">公告</span>
                    <span class="notice_two">{{seller.bulletin}}</span>
            </div>
        </div>
        <transition>
            <div v-show="datatail" class="detail">
                 
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    data(){
      return{
          datatail:false
      }
    },
    props:{
        seller:{
            type:Object
        }
    },
    methods:{
        showDialog(){
            this.datatail=true;
        },
        hideDialog(){
            this.datatail=false;
        }
    }
}
</script>

<style lang="stylus">
.header
    width:100%;background-color: rgba(7,17,27,0.5);height:11rem
    .header_left
        width:25%;float: left;box-sizing: border-box;padding:1.5rem  0 0 1.5rem
    .header_right
        width:70%;float: right;box-sizing: border-box;padding:1.5rem 0 0 0.1rem;height:8rem
    .shop-content
        position:relative;height:2rem  
    .shop-active-num
        position:absolute;right:0.5rem;width:4rem;height:2rem;top:0;line-height:2rem;text-align:center;background-color:rgba(0,0,0,0.2);border-radius:1rem;color:#fff;opacity:0.9
    .shop-name
        color:#fff;height:2.2rem;font-size:1.6rem;font-weight:600
    .shop-peisong 
        font-size: 1.3rem;color: #fff;height:2rem
    .all_notice
        height:2.6rem;width:100%;margin-top:0.3rem;padding:0.1rem 0.5rem;box-sizing:border-box;background-color:#333
    .notice_one 
        display:inline-block;width:3rem;height:2rem;text-align:center;line-height:2rem;color:#333;vertical-align:top;background-color:#fff;margin-top:0.3rem;border-radius:0.5rem
    .notice_two
        display:inline-block;width:27rem;height:2.2rem;line-height:2.2rem;overflow: hidden;white-space: nowrap;text-overflow: ellipsis;color:#fff;margin-top:0.2rem
    .detail
        position:fixed;top:0;left:0;width:100%;height:100%;overflow:auto;opacity:0.9;background-color:rgba(7,17,27,0.8);z-index 100
</style>
