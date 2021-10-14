# rich-coin-sdk
Модуль для работы с API Rich Coin

# Установка
* Пропишите в командную строку: **npm i rich-coin-sdk**

# Начало работы
Импортируем библиотеку:
```js
const RichCoinInit = require('rich-coin-sdk');
const RichCoin = new RichCoinInit("key api", merchantId);
```
# API
getHistory - Получает список переводов

```js
async function run() {
    const result = await RichCoin.getHistory(lastTx);
    console.log(result);
}
run();
```

|Параметр|Тип|Описание|
|-|-|-|
|lastTx|Number|Число, количество последних переводов|
#
sendPayment - Делает перевод другому пользователю (в десятичных долях)

```js
async function run() {
    const result = await RichCoin.sendPayment(toId, amount, fromShop); // 1 коин = 1000 ед.
    console.log(result);
}

run();
```

|Параметр|Тип|Описание|
|-|-|-|
|toId|Number|Айди получателя|
|amount|Number|Сумма перевода|
|fromShop|Boolean|Если true, то платеж отправится от имени магазина|
