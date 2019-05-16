
<template>
    <div class="header">
        <div class="header_content">
                <div class="header_left">
                    <img width="64" height="64" :src="seller.avatar" alt="">
                </div>
            <div class="header_right">
                <div class="shop-name">
                    <span class="brand"></span>
                    <span>{{seller.name}}</span>
                </div>
                <div class="shop-peisong">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
                <div v-if="seller.supports" class="shop-content">
                    <div v-if="seller.supports" class="shop-peisong">
                        <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                        <span class="yangshi">{{seller.supports[0].description}}</span>
                    </div>
                    <div v-if="seller.supports" class="shop-active-num" @click="showDialog">{{seller.supports.length}}个</div>
                </div>
            </div>
            <div style="clear:both"></div>
            <div class="all_notice" @click="showDialog">
                    <span class="notice_one">公告</span>
                    <span class="notice_two">{{seller.bulletin}}</span>
            </div>
        </div>
        <transition name="fade">
            <div v-show="datatail" class="detail">
                <div class="detail-main">
                    <h1 class="name">{{seller.name}}</h1>
                    <div class="detail-xing">
                        <star :size="48" :score="seller.score"></star>
                    </div>
                    <div v-if="seller.supports">
                        <p class="youhui-xin">优惠信息</p>
                    </div>
                    <div class="youhui-active" v-if="seller.supports">
                        <ul>
                            <li class="youhui-list" v-for="(item,index) in seller.supports" :key="index">
                                <span class="icon" :class="classMap[seller.supports[index].type]"></span>
                                <span class="text">{{seller.supports[index].description}}</span>
                            </li>
                        </ul>
                    </div>
                    <div class="shopNotice">
                         <p>商家公告</p>
                    </div>
                    <div class="notive_content">{{seller.bulletin}}</div>
                    <div class="del_f">
                        <a @click="hideDialog" href="javascript:">×</a>
                    </div>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
import star from '../star/star'

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
    },
    created(){
        this.classMap=['decrease', 'discount', 'special', 'invoice', 'guarantee'];
    },
    components:{
         star
    }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixin";
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
        .brand
            display: inline-block
            vertical-align: top
            width: 30px
            height: 18px
            bg-image('brand')
            background-size: 30px 18px
            background-repeat: no-repeat
    .shop-peisong 
        font-size: 1.3rem;color: #fff;height:2rem;position:relative
        .yangshi
            font-size: 1.3rem;color: #fff;height:2rem;margin-left:2rem
        .icon
                display: inline-block
                width: 1.3rem
                height:1.3rem
                margin-right: 1rem
                position:absolute
                top:0.2rem
                background-size: 1.3rem 1.3rem
                background-repeat: no-repeat
                &.decrease
                    bg-image('decrease_2')
                &.discount
                    bg-image('discount_2')
                &.guarantee
                    bg-image('guarantee_2')
                &.invoice
                    bg-image('invoice_2')
                &.special
                    bg-image('special_2')   
    .all_notice
        height:2.6rem;width:100%;margin-top:0.3rem;padding:0.1rem 0.5rem;box-sizing:border-box;background-color:#333
    .notice_one 
        display:inline-block;width:3rem;height:2rem;text-align:center;line-height:2rem;color:#333;vertical-align:top;background-color:#fff;margin-top:0.3rem;border-radius:0.5rem
    .notice_two
        display:inline-block;width:27rem;height:2.2rem;line-height:2.2rem;overflow: hidden;white-space: nowrap;text-overflow: ellipsis;color:#fff;margin-top:0.2rem
    .detail
        position:fixed;
        top:0;
        left:0;
        width:100%;
        height:100%;
        overflow:auto;
        opacity:1;
        background-color:rgba(7,17,27,0.8);
        z-index 100;
        &.fade-enter-active, &.fade-leave-active
            transition: all 0.5s
        &.fade-enter, &.fade-leave-active
            opacity: 0
            background: rgba(7, 17, 27, 0)
    .detail-main
        margin-top:6rem;width:100%;padding:0 
    .name
        text-align:center ;color:#fff 
    .detail-xing
        height:2.5rem;text-align:center 
    .youhui-xin
        width:100%;text-align:center;color:#fff;font-size:1.4rem;font-weight:600  
    .youhui-active
        .youhui-list
            list-style :none;height:3rem;line-height:2rem
            .icon
                display: inline-block
                width: 2rem
                height:2rem
                margin-right: 1rem
                background-size: 2rem 2rem
                background-repeat: no-repeat
                &.decrease
                    bg-image('decrease_2')
                &.discount
                    bg-image('discount_2')
                &.guarantee
                    bg-image('guarantee_2')
                &.invoice
                    bg-image('invoice_2')
                &.special
                    bg-image('special_2')   
            .text
                color:#fff;vertical-align: top;  
    .shopNotice
        p
           padding:0;text-align:center;color:#fff;font-size:1.4rem;font-weight:600   
    .notive_content
        padding:1rem 3.6rem;color:#fff  ;line-height:2rem  
    .del_f
        margin-top:5rem  
        a
            font-size:3rem;font-weight:600;color:#fff;text-decoration:none;display:inline-block;width:100%;padding:0;text-align:center                
</style>
