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
#
getBalance - Получает баланс по айди пользователей

getMyBalance - Получает баланс текущего пользователя

```js
async function run() {
    const balances = await RichCoin.getBalance([1, 100, 236908027]);
    const myBalance = await RichCoin.getMyBalance();
    console.log({ balances, myBalance });
}
run();
```

Среди этих методов аргумент принимает только getBalance:

|Параметр|Тип|Описание|
|-|-|-|
|userIds|Number\|Number[]|Массив айди пользователей|
#
**startPolling** - Запускает обмен запросами между клиентом и сервером в режиме реального времени (**WebSocket**). Является **лучшим** и **быстрым** способом получения событий:

```js
RichCoin.startPolling(callback);
/* Тут ваши действия со слушателем */
```

|Параметр|Тип|Описание|
|-|-|-|
|callback|Function|Функция обратного вызова, принимает в себя аргумент **event**|
