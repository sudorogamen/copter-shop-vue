<template>
<div>
    <aside @click="" class="shoping-container">
      <div class="cart-title">
        <span>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 23 20">
            <path
              d="M4.258 0c.45 0 .842.31.944.738l.749 2.649h15.132a.972.972 0 01.945 1.207L20.21 11.94a.973.973 0 01-.945.74H7.643a.973.973 0 01-.947-.748l.005.017L3.503 1.947H.973A.973.973 0 01.973 0h3.285zM19.84 5.334H6.497l1.895 5.398h10.113l1.335-5.398zM8.857 13.699a2.719 2.719 0 012.715 2.717 2.719 2.719 0 01-2.715 2.716 2.719 2.719 0 01-2.716-2.716 2.719 2.719 0 012.716-2.717zm0 1.491a1.225 1.225 0 100 2.45 1.225 1.225 0 000-2.45zM17.901 13.699a2.719 2.719 0 012.715 2.717 2.719 2.719 0 01-2.715 2.716 2.719 2.719 0 01-2.715-2.716 2.719 2.719 0 012.715-2.717zm0 1.491a1.225 1.225 0 100 2.45 1.225 1.225 0 000-2.45z"
            ></path>
          </svg>
        </span>
        Корзина товаров
      </div>
      <ul class="shoping-list">
        <li v-if="buyItems.length == 0" class="null-item">Корзина пуста</li>
        <li class="cart-product-item" v-for="Item in buyItems" >   
            <div class="cart-product-image">
                <img :src= Item.src class="cart-item-image" />
              </div>
              <div class="cart-product-description">
                <h3 class="cart-product-title">{{Item.model}}</h3>
              </div>
              <div class="cart-product-price">
                <span class="cart-price">{{Item.price}}</span><span>₽</span>
              </div>
               <div class="cart-count-row" >
                <button class="count-button minus" @click="cardCountEdit($event)">-</button>
                <span class="cart-count">{{Item.count}}</span> 
                <button class="count-button plus"  @click="cardCountEdit($event)">+</button>
              </div>
        </li>
      </ul>
    </aside>
  
</div>
</template>
<script>
export default {
components: {
 },
data() {
 return {};
 },
 props: {
    buyItems:{
        type: Array,
    }

 },
methods: {
    cardCountEdit(e){
        this.$emit('cardCountEdit',e)
    },
   

},
};
</script>
<style scoped></style>