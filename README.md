Датасет ods_payment:
Поле pay_doc_type
Внедрены проверки на not null - поле должно быть заполнено,
проверка на наличие всех платежных систем batch.expect_column_distinct_values_to_equal_set(column='pay_doc_type', value_set=['MASTER', 'MIR', 'VISA']) - набор данных достаточно большой и отсутствие одной из платежных систем требует проверки
внедрена проверка batch.expect_column_proportion_of_unique_values_to_be_between(column='pay_doc_type', max_value=0.0003, min_value=0.0003) для контроля распределения платежей между системами. Резкое изменение пропорций требует анализа причин изменения, возможна потеря части данных.

Поле pay_doc_num
Внедрена проверка not null, поле должно быть заполнено.

user_id
Внедрена проверка not null, поле должно быть заполнено.
Внедрены проверки на минимальное и максимальное значения. т.к. это суррогатный ключь - можно предположить монотонно возрастающую последовательность, значения менее минимальног появлятся не должны.
внедрена проверка batch.expect_column_proportion_of_unique_values_to_be_between(column='user_id', max_value=0.0123, min_value=0.0123) для контроля пропорций уникальных значений, при резком изменении возможна потеря данных или наоборот дублирование.
Внедрена проверка на тип данных INTEGER

account
Внедрена проверка not null, поле должно быть заполнено.
внедрена проверка  для контроля пропорций уникальных значений при резком изменении возможна потеря данных или наоборот дублирование.
Внедрена проверка на соответствие шаблону ^FL-([0-9]){8,10}$. Шаблон составлен на основе анализа данных.

phone
Внедрена проверка not null, поле должно быть заполнено.
Внедрена проверка на соответствие шаблону ^\+7(\d){10}. Шаблон составлен на основе анализа данных.

billing_period
Внедрена проверка not null, поле должно быть заполнено.
Внедрена проверка на соответствие шаблону ^\d{4}-\d{2}$. Шаблон составлен на основе анализа данных.
Внедрена проверка на диапазон значенй с 2012-01  по 2020-12 для выявления ошибочных значений.

sum
Внедрена проверка not null, поле должно быть заполнено.
Внедрена проверка на соответствие типа.

Pay_date 
Внедрена проверка not null, поле должно быть заполнено.
Внедрена проверка на диапазон значенй с 2012-01-01  по 2020-12-31 для выявления ошибочных записей.
