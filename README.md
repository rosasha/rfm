﻿**Предпроектная работа по сегментации клиентов на основе  RFM-анализа.**

1. **Что такое RFM-анализ**

Сегментация — один из столпов, на котором стоит эффективный смс-маркетинг. Я рассмотрю подход на основе RFM-анализа

В основе подхода лежит RFM-анализ клиентов (Recency — давность, Frequency — частота, Monetary — деньги). Все покупатели распределяются по сегментам в зависимости от давности совершенных покупок, частоты этих покупок и размера суммы заказа.

На основе анализа получаем примерно такую таблицу (изначально планировалось 64 сегмента, сократил до  27). Так же приведены оценочные варианты работы по сегментам:


|**Уходящие**||Таблица 1 «Сегменты»|
| :-: | :- | -: |
|**Сегмент**|**Характеристика сегмента**|**Что отправляем**|
|333|Потерянные экономные|Скорее всего, эти клиенты уже ушли от нас, и не стоит тратить слишком больших усилий на этот сегмент. Отправляем автоматическую цепочку реактивации.|
|332|Одноразовые|см. выше|
|331|Одноразовые|см. выше|
|323|Уходящие редкие|Эти клиенты сделали у нас несколько покупок, а потом перестали покупать. Их можно попытаться вернуть и обязательно получить обратную связь, почему они от нас ушли. Отправляем реактивационную рассылку с опросом.|
|322||см. выше|
|321||см. выше|
|313|Уходящие постоянные|Этих клиентов обязательно нужно попытаться вернуть. Отправляем им реактивационные письма, запрашиваем обратную связь, предлагаем бонусы, программы лояльности.|
|312|Уходящие хорошие постоянные|см. выше|
|311|Уходящие VIP|см. выше|
|**Спящие**|||
|**Сегмент**|**Характеристика сегмента**|**Что отправляем**|
|233|Спящие разовые с маленьким чеком|Эти клиенты ещё помнят о нас. Нужно попробовать расшевелить их стимулирующими акциями. Отправляем им рассылки с интересными акциями и выгодными предложениями.|
|232||см. выше|
|231||см. выше|
|223|Спящие редкие с маленьким чеком|см. выше|
|222|Спящие редкие со средним чеком|см. выше|
|221|Спящие редкие с высоким чеком|см. выше|
|213|Спящие постоянные с маленьким чеком|Ещё не так давно они часто покупали у вас, а сейчас перестали. Нужно обязательно узнать, в чём дело, и попытаться вернуть их. Отправляем им рассылку с интересными акциями и рассылку с опросом.|
|222|Спящие постоянные со средним чеком|см. выше|
|221|Спящие постоянные с высоким чеком|см. выше|
|**Постоянные**|||
|**Сегмент**|**Характеристика сегмента**|**Что отправляем**|
|133|Новички с маленьким чеком|Отправялем welcome-цепочку с описанием преимуществ, ответами на частые вопросы, обучающие материалы|
|132|Новички со средним чеком|см. выше|
|131|Новички с высоким чеком. Потенциальные VIP.|В дополнение к welcome-цепочке отправляем им интересное предложение, чтобы удержать интерес|
|123|Постоянные с маленьким чеком|Нужно попытаться увеличить средний чек допродажей. Отправляем им рассылки с сопутствующими товарами|
|122|Постоянные со средним чеком|см. выше|
|121|Постоянные с высоким чеком|Эти клиенты и так хорошо покупают, не стоит утомлять их лишними рассылками. Отправляем только обычные рассылки|
|113|Постоянные с маленьким чеком|Можно попытаться увеличить сумму чека допродажей. Отправляем им рассылки с сопутствующими товарами|
|112|Постоянные со средним чеком|Наши самые хорошие клиенты, можно попробовать увеличить сумму чека. Отправляем им специальные предложения, сопутствующие товары|
|111|VIP|Отправляем им особые предложения, например, участие в программе лояльности — приглашение в клуб любимых клиентов|

2. **Варианты отслеживания эффективности:**

1. Отслеживать за счет смещения границ (динамика смещения квантилей разбиения)
2. Разбить клиентов на тестовую (рассылка на основе RFM анализа) и контрольную (без рассылки)  группы и сравнить конвертации. (Создать пул клиентов для тестовой и контрольной группы из каждого сегмента  в одинаковой пропорции)

Для экономии денежных ресурсов,  рассылку писем в дальнейшем  осуществлять по ячейкам с долей откликов более 3% (Типа порог рентабельности задаем)

3. Задание четких границ сегментов (тогда автоматически исключается первый пункт). Анализируем  динамику наполняемости каждой группы по количеству. 

*Например:* 

*1 покупка (этих большинство)*

*2 покупки (преодолели психологический барьер, и пришли  снова, уже зная о том, как работает магазин)*

*3-4 покупки (несмотря ни на что, продолжают покупать, надо удержать любой ценой)*

*5-15 покупок (поверили, на них вся надежда, тут верхняя граница бывает очень разная)*

*больше 15 покупок (маньяки, к ним надо присмотреться отдельно)*

3. **Пути реализации алгоритма:**
1. Выгрузка данных из базы 1С. Создана обработка *ВыгрузкаРозничныхПродаж\_2019-08-27.epf*, позволяющая выгружать данные из 1С в формате csv, для дальнейшей работы с ними в оболочке **Python,- Jupyter notebook**.  Данные выгружаются блоками примерно по 300-400МБ в количестве более 8 шт. (Ограничение на выгрузку из базы по размеру)
2. Далее работа с данными производится в трех исполняемых файлах **Python:**  

Предобработка данных (слияние, очистка, приведение к нужному формату  и т.д.):

<https://github.com/rosasha/rfm/blob/master/raw_RFM_1_clean.ipynb>

Реализация самого алгоритма RFM (на основе <https://github.com/joaolcorreia/RFM-analysis/blob/master/RFM%20Analysis.ipynb>):

<https://github.com/rosasha/rfm/blob/master/to_RFM_2.ipynb>

Анализ алгоритма:

<https://github.com/rosasha/rfm/blob/master/working_RFM_3.ipynb>

*Файлы рабочие и приведены только для ознакомления*

4. **Выводы:**
1. Данный алгоритм обладает достаточной гибкостью для целей сегментации на этапе внедрения интеллектуального смс-маркетинга. 
2. В дальнейшем, при обкатке данного алгоритма в «полевых условиях» и выработке основ концепции  построения сегментов именно для наших условий, возможно дальнейшее развитие смс-маркетинга   и прохождения цепочки: RFM-анализ----сегментация на основе регрессии—сегментация на основе решающих деревьев—сегментация на основе XG-boost (возможно пропускать и перепрыгивать цепочку алгоритмов и нахождения наиболее подходящего для нашей сети)

5. **P.S:**
1. Параллельно ведется работа над  предпроектной работой по рекомендательной системе  на основе алгоритма **APRIOPI**. Ознакомиться можно здесь:  <http://datascientist.one/apriori-algorithm/>  (ссылка на реализацию алгоритма:  <http://rasbt.github.io/mlxtend/api_subpackages/mlxtend.frequent_patterns/>)
2. ` `Выгрузка данных из базы 1С делалась расширенной с учетом возможной реализации алгоритма **APRIORI.** 
3. Реализация и совместное использование этих двух алгоритмов (сможем  осуществить полностью индивидуальный подход к клиентам) окажет синергетический эффект и даст толчок  к дальнейшему увеличению прибыли нашей сети

6. **ОТ СЕБЯ:**

**Готов начать реализовывать и претворять в жизнь алгоритм RFM ** 











