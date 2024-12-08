<template @click="openCart($event)">
  <div class="dd">
    <header>
      <div class="header-container">
        <div class="header-logo">
          <svg
            version="1.2"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 300 300"
            width="100"
            height="100"
            fill="#000"
          >
            <path
              id="Layer"
              fill-rule="evenodd"
              class="s0"
              d="m233.2 101.5c-4.8 17.9-9.6 35.8-14.3 53.8c-2.4 9-4.7 17.9-7.4 26.8c-2.6 8.7-5.9 17.9-10.6 25.7c-4.9 8.2-11.2 14.6-20 18.7c-3.6 1.6-7.2 2.7-10.9 3.5c-5.4 1.2-10.8 1.6-16.3 1.9c-13.5 0.8-42.1 0.7-55.6 0.7l8.2-30.7c6.3 0 12.6 0 18.8-0.2c6.1-0.1 12.7-0.4 18.7-1.9c6.5-1.5 11.4-4.1 15.8-9.4c3.9-4.9 6.5-10.9 8.7-16.6c3.9-10.4 8-25.3 10.8-36c3.3-12.1 6.4-24.2 9.5-36.3zm11.1 0l-24 89.2h44.6l24.1-89.2zm-58-33.5h-44.6l-7.8 29.1l-7.8 29.1c-2.7 9.7-5.2 19.4-8.1 29.1c-0.7 2.5-1.4 5-2.5 7.4c-0.4 1-0.8 1.9-1.5 2.8c-1 1.2-2.2 1.8-3.7 2.1c-2 0.5-3.9 0.6-6 0.6c-2.9 0.2-5.8 0.2-8.7 0.2q-9.5 0.1-19 0q-3.5 0-6.9-0.1c-1.4 0-2.8-0.1-4.3-0.3c-1.2-0.2-2.5-0.4-3.3-1.6c-0.8-1.2-0.8-2.8-0.6-4.1c0.1-1.1 0.3-2.3 0.5-3.4q0.6-2.5 1.2-4.9q1.7-6.6 3.5-13.1c0.8-2.8 1.5-5.7 2.4-8.5c0.5-1.8 1-3.7 1.8-5.4c0.6-1.2 1.3-2 2.6-2.5c1-0.4 2-0.4 3.1-0.5c2.9-0.2 5.8-0.2 8.8-0.2c10 0 20.1 0 30.1 0l6-22.3h-16.9h-16.9c-6.8 0-13.5 0-20.3 0.2c-4.8 0-9.6 0.2-14.3 0.5c-2.9 0.2-5.7 0.5-8.5 1.1c-3.8 0.7-7.2 1.9-10.4 4.1c-5.9 3.8-9 9.9-11.3 16c-3 7.8-6.8 22.7-8.8 30.7c-1.1 4.2-2.2 8.4-3.1 12.7c-0.6 3-1.2 5.9-1.1 9c0.2 5.5 2.8 9.9 7.9 12.2c1.5 0.6 3.1 1 4.8 1.4c2.4 0.4 4.8 0.6 7.3 0.8c3.7 0.2 7.4 0.3 11.1 0.4q7.6 0.1 15.3 0.1c14.2 0.1 40 0.1 54.1-0.1c6.2-0.1 12.4-0.3 18.5-0.8c4.3-0.3 8.5-0.8 12.7-2.1c3.2-1 5.9-2.4 8.5-4.7c3.4-3.1 5.2-6.7 6.9-10.8c2-5.1 3.6-10.4 5.1-15.6c3.6-12.1 6.9-24.2 10.2-36.3c4.7-17.4 9.4-34.9 14-52.3z"
            />
          </svg>
        </div>
        <div class="header-content-row">
          <Search/>
          <div class="icons">
            <div @click="openCart($event)" class="shopping-cart">
              <span>{{ this.sumBuyItems }}</span>
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 23 20">
                <path
                  d="M4.258 0c.45 0 .842.31.944.738l.749 2.649h15.132a.972.972 0 01.945 1.207L20.21 11.94a.973.973 0 01-.945.74H7.643a.973.973 0 01-.947-.748l.005.017L3.503 1.947H.973A.973.973 0 01.973 0h3.285zM19.84 5.334H6.497l1.895 5.398h10.113l1.335-5.398zM8.857 13.699a2.719 2.719 0 012.715 2.717 2.719 2.719 0 01-2.715 2.716 2.719 2.719 0 01-2.716-2.716 2.719 2.719 0 012.716-2.717zm0 1.491a1.225 1.225 0 100 2.45 1.225 1.225 0 000-2.45zM17.901 13.699a2.719 2.719 0 012.715 2.717 2.719 2.719 0 01-2.715 2.716 2.719 2.719 0 01-2.715-2.716 2.719 2.719 0 012.715-2.717zm0 1.491a1.225 1.225 0 100 2.45 1.225 1.225 0 000-2.45z"
                ></path>
              </svg>
            </div>
          </div>
        </div>
      </div>
    </header>

    <main>
      <ItemsFilter @filteredItems="filteredItems" :Items="products" />
      <ItemsList @ItemBuy="ItemBuy($event)" :Items="renderItems" />
      <ul class="shop-effect"></ul>
    </main>
  </div>

  <ItemsCart @cardCountEdit="cardCountEdit($event)" :buyItems="buyItems" />
  <div @click="openCart($event)" class="close-shoping-container"></div>
</template>
<script>
import ItemsCart from "./components/ItemsCart.vue";
import ItemsFilter from "./components/ItemsFilter.vue";
import ItemsList from "./components/ItemsList.vue";
import Search from "./components/Search.vue";

export default {
  components: {
    ItemsCart,
    ItemsList,
    ItemsFilter,
    Search,
  },
  data() {
    return {
      products: [
        {
          id: "1",
          category: "quadcopter",
          series: "Mavic",
          model: "DJI Mavic 2",
          prices: ["362 000", "400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0001-front-view.jpg",
          ],
          maximumFlightTime: "46 мин",
          info: "DJI Mavic 3 — мощный флагманский дрон с камерой, оснащенный камерой Hasselblad с CMOS-матрицей 4/3 для упрощения создания изображения профессионального уровня. Устройство предлагает всенаправленное распознавание препятствий для оптимального опыта полета, максимальное время полета до 46 минут и максимальную дальность передачи сигнала 15 км. Каждое из обновлений DJI Mavic 3 устанавливает новые стандарты аэросъемки.",
        },
        {
          id: "2",
          category: "quadcopter",
          series: "Air",
          model: "DJI AIR 2S",
          prices: ["129 000", "150 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0002-front-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "DJI Air 2S с 1-дюймовой CMOS-матрицей, мощным арсеналом функций, компактным корпусом и массой менее 600 г — идеальный дрон для аэрофотосъемки в любом месте и в любое время. Возьмите этот универсальный дрон с собой, чтобы запечатлеть мир в потрясающих деталях.",
        },
        {
          id: "3",
          category: "quadcopter",
          series: "Mini",
          model: "DJI Mini 2",
          prices: ["49 000", "70 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0003-front-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "Крохотный, но мощный, DJI Mini 2 поможет вам создавать 4K-видео c 4-кратным зумом и потрясающие панорамные снимки.",
        },
        {
          id: "4",
          category: "quadcopter",
          series: "Inspire",
          model: "DJI Inspire 2",
          prices: ["1 239 000", "1 400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0004-front-view.png",
          ],
          maximumFlightTime: "31 мин",
          info: "Мы оснастили Inspire 2 новой технологией обработки изображения - CineCore 2.1, записывающей видео с разрешением 6K при 4,44 Гбит/с в CinemaDNG*1 и 5.2К при 2,08 Гбит/с в Adobe, Apple ProRes*2 и H.265/H.264 при 100 Мбит/с. CineCore 2.1 поддерживает серийную съемку (10 одновременных JPEG + DNG снимков и непрерывную DNG съемку*3 при 20 кадрах/с (разрешением 24 Мп) - при использовании камеры Zenmuse X7.",
        },
        {
          id: "5",
          category: "quadcopter",
          series: "Mavic",
          model: "DJI Mavic 3",
          prices: ["364 000", "400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0001-folded-view.jpg",
          ],
          maximumFlightTime: "46 мин",
          info: "DJI Mavic 3 — мощный флагманский дрон с камерой, оснащенный камерой Hasselblad с CMOS-матрицей 4/3 для упрощения создания изображения профессионального уровня. Устройство предлагает всенаправленное распознавание препятствий для оптимального опыта полета, максимальное время полета до 46 минут и максимальную дальность передачи сигнала 15 км. Каждое из обновлений DJI Mavic 3 устанавливает новые стандарты аэросъемки.",
        },
        {
          id: "6",
          category: "quadcopter",
          series: "Air",
          model: "DJI AIR 2S",
          prices: ["129 000", "150 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0002-folded-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "DJI Air 2S с 1-дюймовой CMOS-матрицей, мощным арсеналом функций, компактным корпусом и массой менее 600 г — идеальный дрон для аэрофотосъемки в любом месте и в любое время. Возьмите этот универсальный дрон с собой, чтобы запечатлеть мир в потрясающих деталях.",
        },
        {
          id: "7",
          category: "quadcopter",
          series: "Mini",
          model: "DJI Mini 2",
          prices: ["49 000", "70 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0003-folded-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "Крохотный, но мощный, DJI Mini 2 поможет вам создавать 4K-видео c 4-кратным зумом и потрясающие панорамные снимки.",
        },
        {
          id: "8",
          category: "quadcopter",
          series: "Inspire",
          model: "DJI Inspire 2",
          prices: ["1 239 000", "1 400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0004-folded-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "Мы оснастили Inspire 2 новой технологией обработки изображения - CineCore 2.1, записывающей видео с разрешением 6K при 4,44 Гбит/с в CinemaDNG*1 и 5.2К при 2,08 Гбит/с в Adobe, Apple ProRes*2 и H.265/H.264 при 100 Мбит/с. CineCore 2.1 поддерживает серийную съемку (10 одновременных JPEG + DNG снимков и непрерывную DNG съемку*3 при 20 кадрах/с (разрешением 24 Мп) - при использовании камеры Zenmuse X7.",
        },
        {
          id: "9",
          category: "quadcopter",
          series: "Mavic",
          model: "DJI Mavic 3",
          prices: ["367 000", "400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0001-above-view.jpg",
          ],
          maximumFlightTime: "46 мин",
          info: "DJI Mavic 3 — мощный флагманский дрон с камерой, оснащенный камерой Hasselblad с CMOS-матрицей 4/3 для упрощения создания изображения профессионального уровня. Устройство предлагает всенаправленное распознавание препятствий для оптимального опыта полета, максимальное время полета до 46 минут и максимальную дальность передачи сигнала 15 км. Каждое из обновлений DJI Mavic 3 устанавливает новые стандарты аэросъемки.",
        },
        {
          id: "10",
          category: "quadcopter",
          series: "Air",
          model: "DJI AIR 2S",
          prices: ["129 000", "150 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0002-above-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "DJI Air 2S с 1-дюймовой CMOS-матрицей, мощным арсеналом функций, компактным корпусом и массой менее 600 г — идеальный дрон для аэрофотосъемки в любом месте и в любое время. Возьмите этот универсальный дрон с собой, чтобы запечатлеть мир в потрясающих деталях.",
        },
        {
          id: "11",
          category: "quadcopter",
          series: "Mini",
          model: "DJI Mini 2",
          prices: ["49 000", "70 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0003-above-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "Крохотный, но мощный, DJI Mini 2 поможет вам создавать 4K-видео c 4-кратным зумом и потрясающие панорамные снимки.",
        },
        {
          id: "12",
          category: "quadcopter",
          series: "Inspire",
          model: "DJI Inspire 2",
          prices: ["1 239 000", "1 400 000"],
          photo: [
            "https://sudorogamen.github.io/copter/img/products/quadcopters/quadcopter0004-above-view.jpg",
          ],
          maximumFlightTime: "31 мин",
          info: "Мы оснастили Inspire 2 новой технологией обработки изображения - CineCore 2.1, записывающей видео с разрешением 6K при 4,44 Гбит/с в CinemaDNG*1 и 5.2К при 2,08 Гбит/с в Adobe, Apple ProRes*2 и H.265/H.264 при 100 Мбит/с. CineCore 2.1 поддерживает серийную съемку (10 одновременных JPEG + DNG снимков и непрерывную DNG съемку*3 при 20 кадрах/с (разрешением 24 Мп) - при использовании камеры Zenmuse X7.",
        },
      ],
      renderItems: [],
      buyItems: [],
      sumBuyItems: 0,
    };
  },
  props: {},
  watch: {
    $props: {
      handler() {
        this.renderItems = this.products;
      },
      deep: true,
      immediate: true,
    },
  },
  methods: {
    filteredItems(items) {
      this.renderItems = items;
    },
    openCart(e) {
      let cartButton = document.querySelector(".shopping-cart");
      let cartsRow = document.querySelector(".shoping-container");
      let closeCartsRow = document.querySelector(".close-shoping-container");

      if (e.target == cartButton || e.target == closeCartsRow) {
        if (!cartsRow.classList.contains("active")) {
          cartsRow.classList.add("active");
          cartsRow.style.left = "0";
          closeCartsRow.style.display = "block";
          document.querySelector("body").style.overflowY = "hidden";
          document.querySelector("main").style.pointerEvents = "none";
        } else {
          closeCartsRow.style.display = "none";
          cartsRow.classList.remove("active");
          cartsRow.style.left = "-100%";
          document.querySelector("body").style.overflowY = "visible";
          document.querySelector("main").style.pointerEvents = "initial";
        }
      } else {
        return;
      }
      // this.emptyCart();
    },
    emptyCart() {
      if (
        !document
          .querySelector(".shoping-container")
          .querySelector(".shoping-list")
          .querySelector("li")
      ) {
        document
          .querySelector(".shoping-container")
          .querySelector(".shoping-list").innerHTML = `
  <li class="null-item">
    Корзина пуста
  </li>`;
      }
    },
    ItemBuy(e) {
      let item = e.target.closest("li");
      let src = item.querySelector(".image-card").src;
      let model = item.querySelector(".product-title").innerHTML;
      let price = item.querySelector(".price").innerHTML;
      let newItem = true;

      this.buyItems.forEach((element) => {
        if (element.model == model) {
          element.count++;
          newItem = false;
        }
      });
      if (newItem) {
        this.buyItems.push({ src: src, model: model, price: price, count: 1 });
      }

      this.shopEffetc({ src: src, model: model, price: price }, e);
      this.sumBuyItems++;
    },

    shopEffetc(Item, e) {
      let effectContainer = document.querySelector(".shop-effect");

      let li = document.createElement("li");
      li.innerHTML = `<div class="product-image">
                  <img src="${Item.src}" alt="" class="image-card" />
                </div>
                <div class="product-description">
                  <h3 class="product-title">${Item.model}</h3>
                </div>
                <div class="product-price">
                  <span class="price">${Item.price}</span><span>₽</span>
                </div>
                <button type="button" class="buy-button">В корзину</button>`;
      li.classList.add("cart-product-item", "js-effect-item");
      effectContainer.append(li);
      li.style.left = e.target.closest("li").offsetLeft - 10 + "px";
      li.style.top = e.target.closest("li").offsetTop + "px";
      let card = document.querySelector(".shopping-cart");
      li.style.left = card.offsetLeft + 10 + "px";
      li.style.top = card.offsetTop + 20 + "px";
      li.style.width = 10 + "px";
      li.style.height = 10 + "px";

      setTimeout(() => {
        li.remove();
      }, 650);
    },

    cardCountEdit(e) {
      this.buyItems.forEach((el, i) => {
        if (
          el.model ===
          e.target.closest("li").querySelector(".cart-product-title").innerHTML
        ) {
          if (e.target.classList.contains("plus")) {
            this.sumBuyItems++;
            el.count++;
          } else {
            if (
              parseInt(
                e.target.closest("div").querySelector("span").innerHTML
              ) > 1
            ) {
              this.sumBuyItems--;
              el.count--;
            } else {
              this.sumBuyItems--;

              this.buyItems = this.buyItems.filter((item) => {
                if (item.model == el.model) {
                  return false;
                } else {
                  return true;
                }
              });
            }
          }
        }
      });
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  border: none;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

/* Links */

a,
a:link,
a:visited a {
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

/* Common */

aside,
nav,
footer,
header,
section,
main {
  display: block;
}

h1,
h2,
h3,
h4,
h5,
h6,
p {
  font-size: inherit;
  font-weight: inherit;
}

ul,
ul li {
  list-style: none;
}

img {
  vertical-align: top;
}

img,
svg {
  max-width: 100%;
  height: auto;
}

address {
  font-style: normal;
}

/* Form */

input,
textarea,
button,
select {
  font-family: inherit;
  font-size: inherit;
  color: inherit;
  background-color: transparent;
}

input::-ms-clear {
  display: none;
}

button,
input[type="submit"] {
  display: inline-block;
  box-shadow: none;
  background-color: transparent;
  background: none;
  cursor: pointer;
}

input:focus,
input:active,
button:focus,
button:active,
textarea:focus,
textarea:active {
  outline: none;
}

button::-moz-focus-inner {
  padding: 0;
  border: 0;
}

label {
  cursor: pointer;
}

legend {
  display: block;
}

body {
  user-select: none;
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  background: #858282;
}
header {
  background: #85828228;
}
.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}
.header-logo {
}
.header-content-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
.search-bar {
  border-radius: 8px;
  position: relative;
  width: clamp(1px, 60vw, 300px);
  background: #ffffff;
}

.search-bar button {
  position: absolute;
  right: 1px;
  top: 0;
  bottom: 0;
}
.input-search {
  border-radius: 8px;
  height: 30px;
  width: 90%;
}
.input-search::placeholder {
  padding: 5px 5px;
}
.icons {
}
.shopping-cart span {
  z-index: -1;
  text-align: right;
  color: white;
  position: absolute;
  font-size: 18px;
  top: -10px;
  right: 30%;
  cursor: default;
}

.shopping-cart {
  position: relative;
  z-index: 5;
  cursor: pointer;
}

.shopping-cart svg {
  position: relative;
  z-index: -1;
  width: 60px;
  height: 60px;
}

.filter-container {
  transition: all 0.2s ease-in;
  overflow: hidden;
  height: 0px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}
.filter-container.active {
  height: 70px;
  margin: 0 auto 10px;
}
.series-list {
  display: flex;
  gap: 10px;
}

.series-item {
  cursor: pointer;
  background: #ffffff;
  border-radius: 15px;
  font-size: 16px;
  padding: 8px 15px;
}
.series-item.active {
  color: #ffffff;
  background: #000;
}
.prise-select select {
  background: #ffffff;
  width: clamp(1px, 60vw, 200px);
  padding: 8px 15px;
  border-radius: 15px;
}
.prise-select option {
  font-size: 18px;
  background: #838383;
  color: #ffffff;
}

option:hover {
  background-color: yellow;
}

.filter-price-inputs {
  position: relative;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}
.filter-price-inputs p {
  font-size: 18px;
  z-index: 4;
  display: none;
  color: red;
  position: absolute;
  top: -20px;
  right: 0;
  left: 0;
  text-align: center;
}

.filter-price-label {
  padding: 8px 15px;
  border-radius: 15px;
  background: #ffffff;
}
.filter-text {
}
.filter-price-input {
}
.products-container {
  display: flex;
  justify-self: center;
  flex-direction: column;
  max-width: 1200px;
  margin: 0 auto;
}
.error-render {
  align-self: center;
  font-size: 26px;
  font-weight: 900;
}
.js-products-list {
  display: grid;
  gap: 10px;
  grid-template-columns: repeat(auto-fill, minmax(200px, 290px));
  justify-content: center;
}

.js-product-item {
  background: #ffffff;
  border: px solid rgba(3, 3, 3, 0.5);
  border-radius: 15px;
  display: flex;
  overflow: hidden;
  flex-direction: column;
  align-items: center;
  gap: 5px;
  padding-bottom: 10px;
}
.product-image {
}
.image-card {
  width: 100%;
  height: 300px;
}
.product-description {
}
.product-title {
  font-size: 24px;
  font-weight: 500;
}
.product-price {
  font-weight: 600;
}
.price {
  margin-right: 5px;
}
.buy-button {
  border: 1px black solid;
  font-size: 20px;
  font-weight: 600;
  width: 150px;
  height: 40px;
}
body input {
  background: #ffffff;
}

.shoping-container {
  color: #000000;
  background: #d4d4d4;
  overflow-y: auto;
  position: fixed;
  transition: 0.2s;
  left: -100%;
  top: 0;
  width: clamp(1px, 60vw, 300px);
  height: 100%;
  z-index: 5;
}
.close-shoping-container {
  display: none;
  z-index: 1;
  position: fixed;
  inset: 0 0 0 0;
}

.cart-title {
  border-bottom: #000000 solid 2px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  background: #c0c0c0;
  font-weight: 900;
}
.cart-title span {
  margin-right: 10px;
  height: 30px;
  width: 30px;
}
.shoping-list {
  margin: 10px 0;
  flex-wrap: wrap;
  display: flex;
  gap: 10px;
}
.null-item {
  position: absolute;
  top: 20%;
  left: 20%;
  font-size: 28px;
}
.cart-product-item {
  overflow: hidden;
  border-radius: 12px;
  margin: 0 10px;
  background: white;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.cart-product-image {
  width: 280px;
  height: 280px;
}
.cart-count-row {
  align-items: center;
  display: flex;
  gap: 10px;
}
.cart-count-row button {
  display: flex;
  align-items: self-start;
  font-weight: 900;
  font-size: 24px;
}
.cart-item-image {
}
.cart-product-description {
}
.cart-product-title {
}
.cart-product-price {
}
.cart-price {
}

.shop-effect {
}
.shop-effect li {
  z-index: 1;
  transition: 0.7s;
  position: absolute;
  width: 290px;
  height: 410px;
  border: #000000 solid 1px;
}

@media (max-width: 960px) {
  .filters-box {
    position: relative;
  }
  .filter-container {
    margin: 0;
    flex-direction: column;
  }
  .filter-toggle-button {
  }
  .filter-container.active {
    height: 180px;
  }
  .series-item {
    border-radius: 10px;
    font-size: 12px;
    padding: 8px;
  }
  .prise-select select {
    width: clamp(1px, 60vw, 200px);
    border-radius: 10px;
    font-size: 12px;
    padding: 8px;
  }

  .series-list {
    gap: 10px;
  }
  .prise-select {
    margin: 5px 0;
  }

  .filter-price-inputs {
    margin-bottom: 5px;

    justify-content: center;
    gap: 3px;
  }
  .filter-price-label {
    padding: 8px;
    border-radius: 10px;
  }
  .emptySearch {
    font-size: 20px;
    font-weight: 600;
  }

  .cart-title {
    height: 50px;
    font-size: 22px;
    font-weight: 900;
  }
}
</style>
