# industry_project
 The purpose of the project is to build a model for predicting the temperature of steel (the last measured temperature for the entire batch) The metric for choosing the MAY model.  In order to optimize production costs, the metallurgical plant LLC "So Temper steel" decided to reduce electricity consumption at the steel processing stage.
Description of the processing stage
Steel is processed in a metal bucket with a capacity of about 100 tons. In order for the bucket to withstand high temperatures, it is lined with refractory bricks from the inside. The molten steel is poured into a ladle and heated to the desired temperature with graphite electrodes. They are installed in the bucket lid.

Sulfur is removed from the alloy (desulfurization), the chemical composition is corrected by adding impurities and samples are taken. Steel is alloyed — its composition is changed — by feeding pieces of alloy from a hopper for bulk materials or wire through a special tribe apparatus (English tribe, "mass").

Before the first time alloying additives are introduced, the temperature of the steel is measured and its chemical analysis is performed. Then the temperature is raised for a few minutes, alloying materials are added and the alloy is purged with an inert gas. Then it is mixed and measurements are carried out again. This cycle is repeated until the target chemical composition and optimal melting temperature are reached.

Then the molten steel is sent to the metal finishing or enters the continuous casting machine. From there, the finished product comes out in the form of slabs (English slab, "slab").

1. Research data analysis
The data is represented by 7 tables with data:

• data_wire_new.csv — data on wire materials (volume);

• data_wire_time_new.csv — data about wire materials (time).

• data_arc_new.csv — data about electrodes;

• data_bulk_new.csv — data on the supply of bulk materials (volume);

• data_bulk_time_new.csv — data on the supply of bulk materials (time);

• data_gas_new.csv — data on gas purging of the alloy;

• data_temp_new.csv — temperature measurement results;

In all files, the key column contains the batch number. There may be several lines with the same key value in the files: they correspond to different processing iterations.

After downloading the data, you need to

● make a work plan;

● prepare to study the number of duplicates, the number of omissions, the size of datasets;

● conduct a small research analysis of data (plotting the distribution of column values, statistics)

● write conclusions on the study of data.

2. Data preprocessing
After downloading and studying the data, it is necessary

● clear data from omissions; Delete columns with omissions of more than 70%, replace omissions in the volume of bulk and wire materials by 0.

● creation of new features for more productive training of models; Creation of a column with calculation by the formula (the root of the sum of squares of active and reactive power) of the total power, creation of a new column with arc heating time; aggregate into new columns the volume of bulk materials, the volume of wire materials for one batch.

● creating one table, changing column names;

● conduct a research analysis of the data in the processed table; Plotting in the processed table, identifying the dependence of the target on other features (correlation matrix), checking for multicollinearity for linear models (copy the dataframe with deletion if the correlation values are more than 0.9 only for linear models).

● write conclusions on data processing.

3. Temperature prediction using MO models
3.1 Machine Learning model training
● Separation into training and test samples; To scale the features.Divide the dataset into training and test samples in percentages of 75% and 25%, respectively. The target variable target is the last measured temperature for the entire batch. The MAY metric, additionally the calculation of R2.

● process anomalies in the columns on the training sample; Remove the negative value in the reactive power with the entire key removed. Remove low temperatures from the combined sample (below 1500 degrees).

● Model training. Using random_state(22052023), using automatic selection of hyperparameters using only RandomizedSearchCV, GridSearchCV, if parameter selection is not needed, then using cross_val_score.

● Write conclusions

3.2 Testing the best MO model on a test sample
● Test the best model After training the models, choose the best model and test the best model. Compare metric values, create graphs and draw conclusions.

3.3. Analysis of the significance of features for prediction
● Creating a table and plotting the influence of features on target predictions, draw conclusions

4. General conclusion
● Writing a general conclusion about the stages carried out for all the work done

5. Report
● Compare the solution and the work plan;

● indicate why some steps were not completed, or write that all steps were completed;

● describe the difficulties of the project and how they were solved;

● describe the key steps of the solution;

● list all the signs that were used for training and preprocessing;

● fully describe the models (with parameters and random_state if available);

● specify the final metric on the test
Цель проекта построение модели для предсказания температуры стали (последняя по времени измеренная температура по всей партии) Метрика для выбор модели МАЕ.

Чтобы оптимизировать производственные расходы, металлургический комбинат ООО «Так закаляем сталь» решил уменьшить потребление электроэнергии на этапе обработки стали.

Описание этапа обработки
Сталь обрабатывают в металлическом ковше вместимостью около 100 тонн. Чтобы ковш выдерживал высокие температуры, изнутри его облицовывают огнеупорным кирпичом. Расплавленную сталь заливают в ковш и подогревают до нужной температуры графитовыми электродами. Они установлены в крышке ковша.

Из сплава выводится сера (десульфурация), добавлением примесей корректируется химический состав и отбираются пробы. Сталь легируют — изменяют её состав — подавая куски сплава из бункера для сыпучих материалов или проволоку через специальный трайб-аппарат (англ. tribe, «масса»).

Перед тем как первый раз ввести легирующие добавки, измеряют температуру стали и производят её химический анализ. Потом температуру на несколько минут повышают, добавляют легирующие материалы и продувают сплав инертным газом. Затем его перемешивают и снова проводят измерения. Такой цикл повторяется до достижения целевого химического состава и оптимальной температуры плавки.

Тогда расплавленная сталь отправляется на доводку металла или поступает в машину непрерывной разливки. Оттуда готовый продукт выходит в виде заготовок-слябов (англ. slab, «плита»).

1. Исследовательский анализ данных
Данные представлены 7 таблицами с данными:

• data_wire_new.csv — данные о проволочных материалах (объём);

• data_wire_time_new.csv — данные о проволочных материалах (время).

• data_arc_new.csv — данные об электродах;

• data_bulk_new.csv — данные о подаче сыпучих материалов (объём);

• data_bulk_time_new.csv — данные о подаче сыпучих материалов (время);

• data_gas_new.csv — данные о продувке сплава газом;

• data_temp_new.csv — результаты измерения температуры;

Во всех файлах столбец key содержит номер партии. В файлах может быть несколько строк с одинаковым значением key: они соответствуют разным итерациям обработки.

После загрузки данных необходимо

● составить план работы;

● подготовить изучить количество дубликатов количество пропусков, размера датасетов;

● провести небольшой исследовательский анализ данных(построение графиков распределения значений столбцов, статистики)

● написать выводы по изучению данных.

2. Предобработка данных
После загрузки и изучения данных необходимо

● очистить данные от пропусков; Удаление столбцов с пропусками более 70%, замена пропусков в объёме сыпучих и проволочных материалов на 0.

● создание новых признаков для более продуктивного обучения моделей; Создание столбца с вычислением по формуле(корень из суммы квадратов активной и реактивной мощностей) полной мощности, создание нового столбца с временем нагрева дугой; агрегировать в новые столбцы объем сыпучих материалов, объём проволочных материалов для одной партии.

● создание одной таблицы, изменение названия столбцов;

● провести исследовательсикй анализ данных в обработанной таблице; Построение графиков в обработанной таблице, выявление зависимости таргета от других признаков( матрица корреляций), проверка на мультиколлинеарность для линейных моделей(скопировать датафрейм с удалением, если корреляционных значений более 0.9 только для линейных моделей).

● написать выводы по обработке данных.

3. Прогнозирование температуры с использование моделей МО
3.1 Обучение моделей машинного обучения
● Разделение на обучающую и тестовую выборки; Провести масштабирование признаков.Разделить датасет на обучающую и тестовую выборки в процентном соотношении 75 % и 25 % соответственно. Целевая переменная target - последняя по времени измеренная температура по всей партии. Метрика МAE, дополнительно вычисление R2.

● обработать аномалии в столбцах на обучающей выборке; Удалить отрицательное значение в реактивной мощности с удалением ключа целиком. Удалить низкие температуры из объединенной выборки(ниже 1500 градусов).

● Обучение моделей. Использование random_state(22052023), применение автомтатичекого подбора гиперпараметров с использованием только RandomizedSearchCV, GridSearchCV, если подбор параметров не нужен, то использование cross_val_score.

● Написать выводы

3.2 Тестирование лучшей модели МО на тестовой выборке
● Протестировать лучшую модель После обучения моделей выбрать лучшую модель и произвести тестирование лучшей модели. Сравнить значения метрик, создать графики и сделать выводы.

3.3. Анализ значимости признаков для предсказания
● Создание таблицы и построение графика по влиянию признаков на предсказания таргета, сделать выводы

4.Общий вывод
● Написание общего вывода о проведенных этапах по всей проделанной работе

5. Отчет
● Сравненить решение и план работы;

● указать, почему какие-то шаги не были выполнены, или написать, что все шаги были выполнены;

● описать трудности проекта и того как они были решены;

● описать ключевых шагов решения;

● перечислить все признаки, которые были использованы для обучения и о проводении преобработки;

● описать полностью модели (с параметрами и random_state при наличии);

● указать итоговой метрики на тесте
