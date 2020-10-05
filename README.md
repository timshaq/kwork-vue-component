# kwork vue component
## Demo
[Watch the demo](https://timshaq.github.io/kwork-vue-component/ "Demo").

### Task description
<details><summary>Read task</summary>
Здравствуйте, необходимо разработать на Vue калькулятор стоимости теплицы в зависимости от выбранных параметров. Пример тут: https://promo.агродача.бел/teplica/
Собственно само тз:
1. Параметры длины, шага и цены взаимосвязаны (Например 1/1.1 - цена 300, 1/2.1 - цена 400). По умолчанию должны быть активны 1-ые элементы.
2. В калькуляторе должна быть возможность выбора длины и шага (на примере называется - Дуги через (метров)) и чтобы от выбора того или иного параметра менялась цена. (Желательно сделать выбор через button)
3. Параметры с длиной и шагом могут быть разные у каждого товара (Например у товара 1 будет 1/1.2 - цена 300, у другого 1/1.1 - цена 400)
4. Обязательна должна быть привязка параметров к товару.
P.S. Также необходимо сделать компонент на vue для добавления этих полей (Длина, шаг, цена) и вывода в виде массива (Json).
</details>

### Customer feedback 
![Review](screenshots/revue.PNG "feedback")

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
