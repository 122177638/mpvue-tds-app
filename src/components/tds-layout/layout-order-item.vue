<template>
  <div class="order-item"
       @click="$emit('click',item)">
    <div class="order-title">
      <div class="order-num">订单号：{{item.order_no}}</div>
      <div :class="['order-status',{'no':item.status===-1}]">{{item.mini_status}}</div>
    </div>
    <div class="order-goods">
      <img :src="item.goods_image_url"
           class="goods-img"
           alt="">
      <div class="goods-info">
        <div class="goods-name">{{item.goods_name}}</div>
        <div class="goods-money">￥<span>{{item.amount}}</span></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
.order-item {
  margin-top: 15px;
  padding: 15px;
  background-color: #ffffff;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.05);
  border-radius: 6px;
  .order-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    .order-num {
      font-size: 14px;
      color: #282828;
    }
    .order-status {
      font-size: 14px;
      color: #ff6666;
      &.no{
        color:#c7c7c7;
      }
    }
  }
  .order-goods {
    display: flex;
    align-items: center;
    margin-top: 15px;
    .goods-img {
      width: 90px;
      height: 90px;
      border-radius: 6px;
      display: block;
      margin-right: 15px;
      background: url('../../../static/images/CommodityNull.png') no-repeat;
      background-size: 100% 100%;
    }
    .goods-info {
      flex: 1;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      .goods-name {
        font-size: 16px;
        color: #282828;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 2;
        overflow: hidden;
      }
      .goods-money {
        margin-top: 12px;
        font-size: 14px;
        color: #ff0a0a;
        span {
          font-size: 22px;
          font-weight: bold;
        }
      }
    }
  }
}
</style>
