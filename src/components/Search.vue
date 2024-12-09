<template>
<div>
    <div class="search-bar">
        <form @submit="Itemssearch($event)" action="#">
              <input type="search" placeholder="Поиск" class="input-search" />
            <button type="submit">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="30"
                height="25"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <circle cx="11" cy="11" r="8"></circle>
                <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
              </svg>
            </button>
        </form>
          
          </div>
</div>
</template>
<script>
export default {
components: {
 },
data() {
 return {
    searchItems:[]
 };
 },
 props: {
    Items: {
      type: Array,
    },},
methods: {
    Itemssearch(e){
        let input = e.target.querySelector('input').value.replace(/\s/g, "").toUpperCase().trim();
        this.searchItems = this.Items.filter((item) => {
      let itemText = item.model.replace(/\s/g, "").toUpperCase();
      if (!itemText.includes(input) && input) {
        return false;
      } else {
        return true;
      }
    });

   
       

    this.$emit('searchItems',this.searchItems)
    }



},
};
</script>
<style scoped></style>