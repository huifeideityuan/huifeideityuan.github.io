<template lang="html">
  <div class="foodinfo">

    <div class="button" @click='close'> < </div>
    <div  id="ratings">
      <div >
          <img :src="foodinfo.image" alt="">
          <div class="infor">
            <h2>{{foodinfo.name}}</h2>
            <p class='sellCount'>月售{{foodinfo.sellCount}}份  好评率{{foodinfo.rating}}%</p>
            <p class='price'><strong><span>¥</span>{{foodinfo.price}}</strong><del v-show='foodinfo.oldPrice'><span>¥</span>{{foodinfo.oldPrice}}</del></p>
          </div>
          <div class="intro">
            <h2>商品介绍</h2>
            <p> {{foodinfo.info}}</p>
            <p> {{foodinfo.info}}</p>
            <p> {{foodinfo.info}}</p>
          </div>
          <div class="ratings">
            <h2>商品评价</h2>
              <ul>
                <li v-for='(item,index) in foodinfo.ratings' >
                    <div class="rating-info">
                      <span class="data">{{item.rateTime}}</span>
                      <i class="user">{{item.username}}</i>
                    </div>
                    <div class="content">
                    {{item.text}}
                    </div>
                    <p>1</p>
                    <p>1</p>
                    <p>1</p>
                    <p>1</p>
                    <p>1</p>
                    <p>1</p>
                    <p>1</p>
                </li>
              </ul>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import IScroll from '../../../static/js/iscroll-probe'
export default {
  props:{
    foodinfo:{
      type:Object,
      required:true
    }
  },
  methods:{
    close(){
      this.$emit('close')
    }
  },
  mounted(){
    console.info(new IScroll('#ratings'))
  }
}
</script>

<style lang="less" scoped>
    .foodinfo{
      #ratings{
        position:fixed;
        top:0;
        left:0;
        right:0;
        bottom:48px;
        background-color: #fff;
        z-index:10;
        overflow: hidden;
      }

        // display:none;


      img{
        width:375px;
        height:375px;
      }
      .infor{
        padding:18px;
        h2{
          font-size: 14px;
          color:rgb(7,17,27);
          line-height: 14px;
        }
        .sellCount{
          font-size: 10px;
          height:10px;
          color:rgb(147,153,159);
          line-height: 10px;
          margin-top:8px;
          margin-bottom: 18px;
        }
        .price{
          strong{
            font-size: 14px;
            color:rgb(240,20,20);
            line-height:24px;
            font-weight: 700;
            margin-right:8px;
            span{
              font-weight: normal;
              font-size: 10px;
            }
          }
            del{
              font-size: 10px;
              color:rgb(147,15,159);
              height:24px;
              line-height: 24px;
              font-weight: 700;
              span{
                font-weight: normal;
              }
            }
          }
      }


    }
    .button{
      position:absolute;
      top:12px;
      left:12px;
      font-size:10px;
      font-weight:700;
      color:red;
    }
</style>
