# toxic_tweets
Это скорее проба пера работы с моделью BERT и классификацией тескста, чем оеальный проект.
![image](https://user-images.githubusercontent.com/104565128/169793664-07341e31-7232-4721-bbea-b1070ed51bfb.png)

Мы получили лучшее значение f1-меры равное 0.758.
Основная проблема заключалась в ограничении вычислительной мощности моего домашнего компьютера.в изначальном датасете было <strong>160к</strong> наблюдений,
если взять больше 75 токенов и 80к наблюдений компьютер не вывозил и перезагружался с синим экраном. изначально я уменьшил количество токенов до 50, но модели,
обученные на предсказаниях берта, основанных на этом соотношении показывали посредственные результаты
![image](https://user-images.githubusercontent.com/104565128/169795527-2bbe2a77-febc-44e2-ad97-fa156a1bea7f.png)
в конечном итоге я пришел к тому, чтобы убрать стоп слова(снизить зашумленность и повысить среднюю ценность токена для предсказания) и взять наблюдения с разными 
категориями в одинаковом отношении 1:1 это позволило безболезненно снизить количество данных.
В данных была проблема. Твиты с большим количеством повторений одного слова или фразы, очевидно, это не очень бы сказалось на прогнозе. TF_IDF, например бы с легкостью
решил юы  эту проблему, потому что он учитывает вес слова в предложении и в тексте, но и берт не дурак, так что было принято решение ничего с ними не делать.
но если бы такая задача стояла, то можно было бы написать свою функцию,Ю которая удаляет такие записи из датафрейма. с примерами можете ознакомиться ниже(осторожно,
плохие слова)
![image](https://user-images.githubusercontent.com/104565128/169801321-19a6ecca-1819-4e2f-9844-2cb32dfe8a3d.png)
![image](https://user-images.githubusercontent.com/104565128/169801348-1a4447e0-b298-4380-9d5e-fd389dad0acc.png)
![image](https://user-images.githubusercontent.com/104565128/169801403-519f2536-f27b-442c-9cec-f0e93f8b5b1f.png)
Из-за того, что берт достаточно мощная модель, для задачи классификации нужно надстроить над ней простую модель. катбуст и алгоритм, основанные на решающих деревьях 
показывали плохой результат, поэтому я особо не развивал этот подход.
Вот список технологий и методов, которые я использовал:
<ol>
  <li>Апсемплинг</li>
  <li>Токенизация</li>
  <li>AUC-ROC</li>
  <li>List comprehension</li>
  <li>Масштабирование данных</li>
  <li>Confusion matrix</li>
</ol>
