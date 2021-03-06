# Сборный проект
Задача:

- разобраться, как ведут себя пользователи мобильного приложения.
- изучить воронку продаж, узнайть, как пользователи доходят до покупки.
- исследовать результаты A/A/B-эксперимента

Описание данных
Каждая запись в логе — это действие пользователя, или событие.
ExpId — номер эксперимента: 246 и 247 — контрольные группы, а 248 — экспериментальная.

Используемые библиотеки:
- pandas
- datetime
- numpy
- matplotlib.pyplot
- seaborn
- scipy.stats
- warnings
- math
- pandas.plotting.register_matplotlib_converters
- plotly.graph_objects

# Выводы
1. В данных нет пропусков. В данных обнаружено и удалено 413 дубликатов.
2. Всего в логе 243713 событий. Всего уникальных событий - 5. В среднем на каждого пользователя приходится 32 события.
3. В логах хранятся события за период 2019-07-25 - 2019-08-07 (14 дней). При этом за период 2019-07-25 - 2019-07-31 данные не выглядят полными. Их слишком мало. Фактически анализируемый период принят 2019-08-01 - 2019-08-07.
4. Исключив первую неделю из исследования, убрали 1.2% данных. После удаления данных остались пользователи всех трех групп. Разница между количеством пользоателей до удаления данных и после не превышает 0.3%
5. Исходя из анализа данных, предполагаю такую последовательность прохождения этапов для пользователя: "MainScreenAppear", "OffersScreenAppear", "CartScreenAppear", "PaymentScreenSuccessful". Количество посетителей, проходящих этапы последовательно, равны:
- "MainScreenAppear": 7419
- "OffersScreenAppear" 4201
- "CartScreenAppear": 1767
- "PaymentScreenSuccessful" 454
6. Самый большой % потери клиентов видно с этапа CartScreenAppear на этап PaymentScreenSuccessful. Возможно что-то не так с оплатой картой он-лайн, ведь 74% пользователей прошедших этап CartScreenAppear не проходят этап PaymentScreenSuccessful (это только 6.12% от пользователей, прошедших первый этап)
7. По результатам А/А-теста статистической разницы между группами не выявлено.
8. По результатам А/А/В- теста не получилось найти статистически значимой разницы ни по одной из 12 гипотез между группами 246,247 и 248 при выбранном значеннии порога статистической значимсоти в 0.01 и 0.05.
9. Результаты тестов показывают, что можно смело менять шрифты (или не менять) - пользователи не изменят свое поведение.
