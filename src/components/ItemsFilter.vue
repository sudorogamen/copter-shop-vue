<template>
  <div class="filters-box">
    <svg
      fill="#000000"
      width="40px"
      height="40px"
      viewBox="-1 0 19 19"
      xmlns="http://www.w3.org/2000/svg"
      @click="toggleFiters"
      class="filter-toggle-button"
    >
      <path
        d="M16.417 9.583A7.917 7.917 0 1 1 8.5 1.666a7.917 7.917 0 0 1 7.917 7.917zm-2.882-2.625a.396.396 0 0 0-.396-.396h-.855a1.58 1.58 0 0 0-3.058 0H3.912a.396.396 0 0 0 0 .792h5.314a1.58 1.58 0 0 0 3.058 0h.855a.396.396 0 0 0 .396-.396zm0 2.63a.396.396 0 0 0-.396-.396H7.825a1.58 1.58 0 0 0-3.058 0h-.855a.396.396 0 0 0 0 .792h.855a1.58 1.58 0 0 0 3.058 0h5.314a.396.396 0 0 0 .396-.396zm0 2.63a.396.396 0 0 0-.396-.396h-.855a1.58 1.58 0 0 0-3.058 0H3.912a.396.396 0 1 0 0 .791h5.314a1.58 1.58 0 0 0 3.058 0h.855a.396.396 0 0 0 .396-.396zm-6.452-2.63a.788.788 0 1 1-.787-.788.788.788 0 0 1 .787.788zm4.46-2.63a.787.787 0 1 1-.788-.787.788.788 0 0 1 .787.787zm0 5.26a.787.787 0 1 1-.788-.788.788.788 0 0 1 .787.787z"
      />
    </svg>
    <div class="filter-container">
      <ul class="series-list">
        <li
          @click="activeSeries($event)"
          class="series-item active"
          value="All"
        >
          All
        </li>
        <li @click="activeSeries($event)" class="series-item" value="Mavic">
          Mavic
        </li>
        <li @click="activeSeries($event)" class="series-item" value="Air">
          Air
        </li>
        <li @click="activeSeries($event)" class="series-item" value="Mini">
          Mini
        </li>
        <li @click="activeSeries($event)" class="series-item" value="Inspire">
          Inspire
        </li>
      </ul>
      <div class="prise-select">
        <select @change="activeOption" name="prise" id="js-prise-select">
          <option class="prise-select-option" value="def">
            Без сортировки
          </option>
          <option class="prise-select-option" value="up">По возрастанию</option>
          <option class="prise-select-option" value="down">По убыванию</option>
        </select>
      </div>
      <form class="filter-price-inputs">
        <p>Некорректный диапазон</p>
        <label class="filter-price-label">
          <span class="filter-text">от</span>
          <input
            @input="activePriceRange"
            min="0"
            max="2000000"
            type="number"
            class="filter-price-input"
            placeholder="40000"
          />
          <span class="filter-text">₽</span>
        </label>
        <label class="filter-price-label">
          <span class="filter-text">до</span>
          <input
            @input="activePriceRange"
            min="0"
            max="2000000"
            type="number"
            class="filter-price-input"
            placeholder="2000000"
          />
          <span class="filter-text">₽</span>
        </label>
      </form>
      <button @click="itemsFilter" class="filter-button">Применить</button>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      filteredItems: this.Items,
      addSeries: null,
      addOptions: null,
      addPriceRange: [],
    };
  },
  props: {
    Items: {
      type: Array,
    },
  },
  methods: {
    toggleFiters() {
      document.querySelector(".filter-container").classList.toggle("active");
    },
    activeOption(e) {
      if (e.target.value === "def") {
        this.addOptions = null;
      } else {
        this.addOptions = e.target.value;
      }
    },
    activeSeries(e) {
      let series = document.querySelectorAll(".series-item");
      series.forEach((item) => {
        item.classList.remove("active");
      });
      e.target.classList.add("active");
      //обновляем значение активного фильтра
      if (e.target.getAttribute("value") == "All") {
        this.addSeries = null;
      } else {
        this.addSeries = e.target.getAttribute("value");
      }
    },

    activePriceRange() {
      let form = document.querySelector(".filter-price-inputs");
      this.addPriceRange = [];
      let inputs = document.querySelectorAll(".filter-price-input");
      let error = form.querySelector("p");
      error.style.display = "none";
      inputs.forEach((item) => {
        this.addPriceRange.push(item.value);
      });
    },

    itemsFilter() {
      let error = document
        .querySelector(".filter-price-inputs")
        .querySelector("p");
      this.filteredItems = this.Items;
      this.filteredItems = this.filteredItems.filter((product) => {
        if (this.addSeries && product.series !== this.addSeries) {
          return false;
        } else {
          return true;
        }
      });

      if (parseInt(this.addPriceRange[0]) > parseInt(this.addPriceRange[1])) {
        error.style.display = "block";
      } else {
        let min = parseInt(this.addPriceRange[0])
          ? parseInt(this.addPriceRange[0].replace(/\s/g, ""))
          : -100000000000;
        let max = parseInt(this.addPriceRange[1])
          ? parseInt(this.addPriceRange[1].replace(/\s/g, ""))
          : 100000000000;

        this.filteredItems = this.filteredItems.filter((item) => {
          let itemPrice = parseInt(item.prices[0].replace(/\s/g, ""));
          if (min > itemPrice || itemPrice > max) {
            return false;
          }
          return true;
        });
        if (
          document
            .querySelector(".products-container")
            .querySelector(".emptyCardInRange")
        ) {
          document
            .querySelector(".products-container")
            .querySelector(".emptyCardInRange")
            .remove();
        }
        if (this.filteredItems == 0) {
          let emptySearch = document.createElement("div");
          emptySearch.classList.add("emptyCardInRange", "error-render");
          emptySearch.innerHTML = `Нет подходящих товаров`;
          document.querySelector(".products-container").append(emptySearch);
        }
      }
      //сортируем и перерендерим мссив
      this.filteredItems = this.filteredItems.toSorted((a, b) => {
        if (this.addOptions) {
          const priceA = parseInt(a.prices[0].replace(/\s/g, ""));
          const priceB = parseInt(b.prices[0].replace(/\s/g, ""));
          if (this.addOptions === "up") {
            return priceA - priceB;
          } else {
            return priceB - priceA;
          }
        } else {
          return;
        }
      });
      this.$emit("filteredItems", this.filteredItems);
    },
  },
};
</script>
<style scoped>
.filters-box {
  max-width: 1200px;
  margin: 0 auto 10px;
  text-align: right;
}
.filter-toggle-button {
  cursor: pointer;
}
.filter-button {
  padding: 8px 15px;
  border-radius: 15px;
  background: #ffffff;
}
</style>
