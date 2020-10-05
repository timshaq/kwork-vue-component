<template>

  <div class="products__card">
    <div class="card__ph">
      <img :src="this.img" alt="">
    </div>
    <h2 class="card__title">
      {{ this.title }}
    </h2>
    <p class="card__description">
      {{ this.description }}
    </p>

    <div class="card__param">
      <div class="card__param-title">
        Длина (метров):
      </div>

      <div class="card__options">
        <button type="button" name="button"
        :class="isActiveLength(lengthList[index]) ? 'active' : ''"
        v-for="(item, index) in lengthList" :key="lengthList[index]"
        @click.prevent="setLength(lengthList[index])"
        :disabled="isDisabledLength(lengthList[index])">
          {{ lengthList[index] }}
        </button>
      </div>

    </div>

    <div class="card__param">
      <div class="card__param-title">
        Дуги через (метров):
      </div>

      <div class="card__options">
        <button name="button" type="button"
        v-for="(item, index) in stepList" :key="stepList[index]"
        :class="isActiveStep(stepList[index]) ? 'active' : ''"
        :disabled="isDisabledStep(stepList[index])"
        @click.prevent="setStep(stepList[index])">
          {{ stepList[index] }}
        </button>
      </div>

    </div>

    <div class="card__order">
      <div class="card__price">
        Цена:
        {{ this.currentPrice }}  руб.
      </div>

      <div class="card__btn">
        <button type="button" name="button"
        @click.prevent="sendData">
          Заказать
        </button>
      </div>
    </div>

  </div>

</template>

<script>
export default {
  name: 'ProductItem',
  props: ['options', 'productData'],
  data() {
    return {
      currentLength: this.options.options[0][0],
      currentStep: this.options.options[0][1],
    };
  },
  computed: {
    option() {
      return this.options.options;
    },
    title() {
      return this.options.title;
    },
    description() {
      return this.options.description;
    },
    img() {
      return this.options.img;
    },
    lengthList() {
      const tmp = this.option.map((item) => item[0]);
      return Array.from(new Set(tmp));
    },
    stepList() {
      const tmp = this.option.map((item) => item[1]);
      return Array.from(new Set(tmp));
    },
    currentPrice() {
      const tmp = [this.currentLength, this.currentStep];
      const opt = this.option.find((item) => ((item[0] === tmp[0]) && (item[1] === tmp[1])));
      return opt[2];
    },
  },
  methods: {
    isActiveLength(val) {
      return (val === this.currentLength);
    },
    isActiveStep(val) {
      return (val === this.currentStep);
    },
    isDisabledLength() {
      const tmp = [this.currentLength, this.currentStep];
      const opt = this.option.filter((item) => ((item[0] === tmp[0]) && (item[1] === tmp[1])));
      return Boolean(!opt.length);
    },
    isDisabledStep(val) {
      const tmp = [this.currentLength, val];
      const opt = this.option.filter((item) => ((item[0] === tmp[0]) && (item[1] === tmp[1])));
      return Boolean(!opt.length);
    },
    setLength(length) {
      const tmp = [length, this.currentStep];
      const opt = this.option.filter((item) => ((item[0] === tmp[0]) && (item[1] === tmp[1])));
      if (!opt.length) {
        const firstFind = this.option.find((item) => item[0] === length)[1];
        this.currentStep = firstFind;
        this.currentLength = length;
      } else {
        this.currentLength = length;
      }
    },
    setStep(step) {
      this.currentStep = step;
    },
    sendData() {
      const tmp = {
        length: this.currentLength,
        step: this.currentStep,
        price: this.currentPrice,
      };
      return this.$emit('update:productData', tmp);
    },
  },
};
</script>

<style>
  *{
    padding: 0;
    margin: 0;
    border: 0;
  }
  *,*:before,*:after{
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
  }
  :focus,:active{outline: none;}
  a:focus,a:active{outline: none;}

  nav,footer,header,aside{display: block;}
  html,body{
    height: 100%;
    width: 100%;
    font-size: 100%;
    line-height: 1;
    font-size: 14px;
    -ms-text-size-adjust: 100%;
    -moz-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
  }
  input,button,textarea{font-family:inherit;}
  input::-ms-clear{display: none;}
  button{cursor: pointer;}
  button::-moz-focus-inner {padding:0;border:0;}
  a, a:visited{text-decoration: none;}
  a:hover{text-decoration: none;}
  ul li{list-style: none;}
  img{vertical-align: top;max-width: 100%;}
  h1,h2,h3,h4,h5,h6{font-size:inherit;font-weight: 400;}

  .products__card {
    width: 33.333%;
    max-width: 320px;
    min-width: 290px;
    box-shadow: 2px 5px 1rem rgba(0, 0, 0, 0.4);
    height: fit-content;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    margin: 20px 20px;
  }
  .card__ph img {
    width: 250px;
    height: 250px;
    object-fit: cover;
  }
  .card__title {
    font-size: 22px;
    font-weight: 600;
    margin: 10px 0;
  }
  .card__description {
    font-style: italic;
    font-size: 16px;
    margin: 10px 0;
  }
  .card__param {
    width: 100%;
    padding: 10px 40px;
  }
  .card__param-title {
    font-size: 16px;
    font-weight: 600;
  }
  .card__options {
    width: 100%;
    display: flex;
    justify-content: center;
    margin: 10px 0;
  }
  .card__options button {
    padding: 8px 15px;
    border-top: 2px solid #F2F5F8;
    background: #F2F5F8;
    border-radius: 8px;
    font-weight: 600;
    margin: 0 5px;
  }
  .card__options button:disabled {
    cursor: not-allowed;
  }
  .card__options button.active {
    background: linear-gradient(#5fc6e9, #598ecc);
    border-top: 2px solid #598ecc;
    box-shadow: 0 0 1px #5fc6e9;
    color: #FFFFFF;
  }
  .card__order {
    width: 100%;
    padding: 0 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .card__price {
    font-size: 16px;
    font-weight: 600;
    margin: 10px 0;
  }
  .card__btn button {
    padding: 15px 35px;
    background: #ffc107;
    font-size: 18px;
    font-weight: 600;
    margin: 10px 0;
  }
</style>
