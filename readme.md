***
# Описание решения и применения модели:
---
Решение состоит из следующих шагов:
1. Построение кластеров предложений из тендеров. Для векторизации предложений используется предобученная модель. Используется файл **all_train_df.csv**, который является дополнением **all_applic.dat** информацией из **all_meta.dat** для случаев совпадение тендера. Этот шаг реализован в **Clustering.ipynb**. Результатом является файл **clusters.csv**;
2. Ручной анализ полученных кластеров и формирование классов (категорий), которые будут выделяться в документе. В файле **from_clusters_to_classes.ipynb** можно найти код для преобразования **clusters.csv** в **dataset.csv**. Теперь имеется размеченный набор данных, где каждое предложение относится к категории стоимость, дата составления, участники и другие;
3. На этом шаге обучается парсер на основе модели машинного обучения (**model_training.ipynb**). Сама модель - многослойный перцептрон. Результатом является файл **model.pkl**;
4. Файл **from_text_to_table.ipynb** является финальным и именно он используется для построения базы данных (таблицы) по текстовым описаниям тендеров. В нем может использоваться любой из (**all_applic.dat**, **all_meta.dat**, **all_test_df.csv**, **all_train_df.csv**) файлов и model.pkl для парсинга. В результате сохраняются **table.csv** и **table.xls**. Важно! **all_test_df.csv** никак не участвовала в формировании этого парсера и предпочтительная для проверки работоспособности системы.

Для запуска решения на новых данных нужно запустить ноутбук **from_text_to_table.ipynb**, предварительно изменив переменную **file_path** на необходимую. 
