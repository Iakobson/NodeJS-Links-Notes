_Асинхронність представляє можливість одночасно виконувати відразу кілька завдань. Асинхронність відіграє велику роль у Node.js._

```javascript
// async.js
// Цей код представляє собою простий модуль, який демонструє асинхронну роботу з колбеками.
console.log("Початок роботи програми");

function display(data, callback){
  console.log("Запуск дисплею...");
  // рандомно визначаємо число користувачів
  let randInt = (Math.random() * (10 - 1) + 1).toFixed(2);
	console.log("Число користувачів:", randInt);
  // якщо число > 5, то генерується об'єкт помилки з повідомленням
  let err = randInt>5? new Error("Помилка виконання: randInt більше 5"): null;
    // запускається асинхронний таймер, який 
	// викликає передану функцію з callback і передає їй err і data 
    setTimeout(function(){
	  // це загальна модель функцій зворотного виклику
        callback(err, data);
    }, 0);
}
 

display("Обробка даних...", function (err, data){ 
  // в разі помилки програма припиняє свою роботу
    if(err) throw err;
  // якщо помилки немає, то виводиться data
    console.log(data);
});
 
console.log("Завершення роботи програми");
```




