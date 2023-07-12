# Предсказание коэффициента восстановления золота из золотосодержащей руды
<h1>Содержание<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Предсказание-коэффициента-восстановления-золота-из-золотосодержащей-руды" data-toc-modified-id="Предсказание-коэффициента-восстановления-золота-из-золотосодержащей-руды-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Предсказание коэффициента восстановления золота из золотосодержащей руды</a></span><ul class="toc-item"><li><span><a href="#Описание-проекта" data-toc-modified-id="Описание-проекта-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Описание проекта</a></span></li><li><span><a href="#Технологический-процесс" data-toc-modified-id="Технологический-процесс-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Технологический процесс</a></span></li><li><span><a href="#Параметры-этапов" data-toc-modified-id="Параметры-этапов-1.3"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Параметры этапов</a></span></li><li><span><a href="#Наименование-признаков" data-toc-modified-id="Наименование-признаков-1.4"><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Наименование признаков</a></span><ul class="toc-item"><li><span><a href="#Возможные-значения-для-блока-[этап]" data-toc-modified-id="Возможные-значения-для-блока-[этап]-1.4.1"><span class="toc-item-num">1.4.1&nbsp;&nbsp;</span>Возможные значения для блока [этап]</a></span></li><li><span><a href="#Возможные-значения-для-блока-[тип_параметра]" data-toc-modified-id="Возможные-значения-для-блока-[тип_параметра]-1.4.2"><span class="toc-item-num">1.4.2&nbsp;&nbsp;</span>Возможные значения для блока [тип_параметра]</a></span></li><li><span><a href="#Целевые-признаки" data-toc-modified-id="Целевые-признаки-1.4.3"><span class="toc-item-num">1.4.3&nbsp;&nbsp;</span>Целевые признаки</a></span></li></ul></li><li><span><a href="#Формула-расчёта-эффективности" data-toc-modified-id="Формула-расчёта-эффективности-1.5"><span class="toc-item-num">1.5&nbsp;&nbsp;</span>Формула расчёта эффективности</a></span></li><li><span><a href="#Формула-итоговой-метрики" data-toc-modified-id="Формула-итоговой-метрики-1.6"><span class="toc-item-num">1.6&nbsp;&nbsp;</span>Формула итоговой метрики</a></span></li><li><span><a href="#Вывод" data-toc-modified-id="Вывод-1.7"><span class="toc-item-num">1.7&nbsp;&nbsp;</span>Вывод</a></span></li></ul></li></ul></div>



## Описание проекта
Необходимо подготовить прототип модели машинного обучения для «Цифры». Компания разрабатывает решения для эффективной работы промышленных предприятий.
Модель должна предсказать коэффициент восстановления золота из золотосодержащей руды. В моем распоряжении данные с параметрами добычи и очистки.
Модель поможет оптимизировать производство, чтобы не запускать предприятие с убыточными характеристиками.
Описание данных

## Технологический процесс
- Rougher feed — исходное сырье
- Rougher additions (или reagent additions) — флотационные реагенты: Xanthate, Sulphate, Depressant
- Xanthate **— ксантогенат (промотер, или активатор флотации);
- Sulphate — сульфат (на данном производстве сульфид натрия);
- Depressant — депрессант (силикат натрия).
- Rougher process (англ. «грубый процесс») — флотация
- Rougher tails — отвальные хвосты
- Float banks — флотационная установка
- Cleaner process — очистка
- Rougher Au — черновой концентрат золота
- Final Au — финальный концентрат золота  


## Параметры этапов
air amount — объём воздуха
fluid levels — уровень жидкости
feed size — размер гранул сырья
feed rate — скорость подачи  


## Наименование признаков

Наименование признаков формируется по следующему принципу:  

__[этап].[тип_параметра].[название_параметра]__  

Пример: rougher.input.feed_ag

### Возможные значения для блока [этап]
- rougher — флотация
- primary_cleaner — первичная очистка
- secondary_cleaner — вторичная очистка
- final — финальные характеристики  


### Возможные значения для блока [тип_параметра]
- input — параметры сырья
- output — параметры продукта
- state — параметры, характеризующие текущее состояние этапа
- calculation — расчётные характеристики

### Целевые признаки
- эффективность обогащения чернового концентрата rougher.output.recovery;
- эффективность обогащения финального концентрата final.output.recovery.

## Формула расчёта эффективности 

![](http://latex.codecogs.com/gif.latex?\dpi{110}&space;\bg_white&space;Recovery&space;=&space;\frac{C\times(F&space;-&space;T)}{F\times(C&space;-&space;T)}&space;*&space;100\%)

где:
 - C — доля золота в концентрате после флотации/очистки;
 - F — доля золота в сырье/концентрате до флотации/очистки;
 - T — доля золота в отвальных хвостах после флотации/очистки.
 
 ## Формула итоговой метрики
 ![](http://latex.codecogs.com/gif.latex?%5Cdpi%7B110%7D%20%5Cbg_white%20final-%20sMAPE%20=%2025%5C%25%20%5Ctimes%20sMAPE(rougher)%20&plus;%2075%5C%25%20%5Ctimes%20sMAPE(final)%20)
 
 
## Вывод

Проведена предобработка данных. Проверена правильность расчета обогощения. Обработаны пропуски.

Обнаружено, что в тестовом наборе данных отутствуют целевые переменные. Вернули их из полного набора данных методом Merge по переменной date.

Лучшей моделью для предсказания коэффициента восстановления золота оказалась - RandomForestRegressor(). sMAPE на тестовом наборе данных составил 8,7. На константной модели sMAPE - 8.9.
