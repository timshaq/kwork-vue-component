<template>
  <div id="app">
    <div class="products">
      <ProductItem v-for="(item, i) in this.options" :key="i" :options="item"
      :productData.sync="productItemData"/>
    </div>
    <div class="fixed">
      productItemData:
      <br>
      <br>
      {{ this.productItemData }}
    </div>
  </div>
</template>

<script>
import ProductItem from '@/components/ProductItem.vue';

export default {
  name: 'App',
  data() {
    return {
      productItemData: {},
      options: [
        {
          title: 'Test',
          description: 'Оцинкованная труба 20х20 мм (2 м ширина 1.8 м высота)',
          img: 'https://clck.ru/Qny9X',
          options: [
            [1, 1.1, 200],
            [1, 2, 300],
            [2, 1.1, 400],

            [4, 1, 100],
            [4, 0.67, 200],
            [4, 0.5, 300],

            [6, 1, 400],
            [6, 0.67, 500],
            [6, 0.5, 600],
          ],
        },
        {
          title: 'Сибирская "Мини"',
          description: 'Оцинкованная труба 20х20 мм (2 м ширина 1.8 м высота)',
          img: 'https://clck.ru/Qny7w',
          options: [
            [4, 1, 100],
            [4, 0.67, 200],
            [4, 0.5, 300],

            [6, 1, 400],
            [6, 0.67, 500],
            [6, 0.5, 600],

            [8, 1, 700],
            [8, 0.67, 800],
            [8, 0.5, 900],

            [10, 1, 1000],
            [10, 0.67, 1100],
            [10, 0.5, 1200],
          ],
        },
        {
          title: 'Сибирская',
          description: 'Оцинкованная труба 20х20 мм (3 м ширина 2.1 м высота)',
          img: 'https://clck.ru/QnyAQ',
          options: [
            [4, 1, 362],
            [4, 0.67, 377],
            [4, 0.5, 394],

            [6, 1, 464],
            [6, 0.67, 487],
            [6, 0.5, 512],

            [8, 1, 565],
            [8, 0.67, 597],
            [8, 0.5, 728],

            [10, 1, 668],
            [10, 0.67, 705],
            [10, 0.5, 744],
          ],
        },
        {
          title: 'Ферма',
          description: 'Оцинкованная труба 20х20 мм (2 м ширина 3 м высота)',
          img: 'https://clck.ru/QnyAx',
          options: [
            [1, 1.1, 200],
            [1, 2, 300],
            [2, 1.1, 400],
          ],
        },
      ],
    };
  },
  components: {
    ProductItem,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.products {
  width: 100%;
  padding: 20px 15px;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
}
.fixed {
  position: fixed;
  top: 0;
  left: 0;
  padding: 15px;
  background: rgba(0,0,0,.5);
  color: #FFFFFF;
  font-size: 12px;
  font-weight: 600;
}
</style>
