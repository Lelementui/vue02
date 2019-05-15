<template>
    <div class="star" :class="starType">
        <span v-for='(itemClass,index) in itemClasses' :class="itemClass" class="star-item" :key="index"></span>
    </div>
</template>
<script>

const  len=5;
const  online='on';
const outline='off';
const hash='half';

export default {
    data(){
        return{

        }
    },
    props:{
        score:{
            type:Number
        },
        size:{
            type:Number
        }
    },
    computed:{
        starType(){
           return 'star-'+this.size;
        },
        itemClasses(){
            let result=[];
            let one=Math.floor(this.score*2)/2;
            let two=Math.floor(this.score);
            let three=this.score%1!==0;
            for(let i=0;i<two;i++){
                result.push(online);
            }
            if(three){
                result.push(hash);
            }
            while (result.length < len) {
                result.push(outline);
            }
            return result;
        }
    }
}
</script>
<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixin";
.star
    font-size: 0
    .star-item
      display: inline-block
      background-repeat: no-repeat
    &.star-48
      .star-item
        width: 20px
        height: 20px
        margin-right: 22px
        background-size: 20px 20px
        &:last-child
          margin-right: 0
        &.on
          bg-image('star48_on')
        &.half
          bg-image('star48_half')
        &.off
          bg-image('star48_off')
    &.star-36
      .star-item
        width: 15px
        height: 15px
        margin-right: 6px
        background-size: 15px 15px
        &:last-child
          margin-right: 0
        &.on
          bg-image('star36_on')
        &.half
          bg-image('star36_half')
        &.off
          bg-image('star36_off')
    &.star-24
      .star-item
        width: 10px
        height: 10px
        margin-right: 3px
        background-size: 10px 10px
        &:last-child
          margin-right: 0
        &.on
          bg-image('star24_on')
        &.half
          bg-image('star24_half')
        &.off
          bg-image('star24_off')
</style>


