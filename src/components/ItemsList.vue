<template >
  <div  class="products-container">
    <ul class="js-products-list">
      
        <li  class="js-product-item" :id="Item.id" v-for="Item in Items">
            <div class="product-image">
                  <img :src= Item.photo  class="image-card" />
                </div>
                <div class="product-description">
                  <h3 class="product-title">{{Item.model}}</h3>
                </div>
                <div class="product-price">
                  <span class="price">{{Item.prices[0]}}</span><span>₽</span>
                </div>
                <button @click="$emit('ItemBuy', $event)"  type="button" class="buy-button" >В корзину</button>
        </li>
    </ul>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
    };
  },
  props: {
    Items: {
      type: Array,
    },
  },

  methods: {


  },
};
</script>
<style scoped></style>
