 Лабораторная работа 1 по дисциплине "Базы данных"
# ФИО студента, номер учебной группы 
Ковальчук Никита Владимирович 2262
# Вариант 5 Магазины
Рассматривается система для учета товаров, реализуемых в различных магазинах. Каждый магазин имеет уникальные характеристики (номер, наименование, адрес, площадь). В магазинах реализуются товары различных наименований и сортов. Для каждого товара в конкретном магазине необходимо учитывать единицу измерения, цену за единицу и количество единиц товара.
Один и тот же товар может продаваться в разных магазинах по разной цене и в разном количестве

Сущности: Магазины, Товары, Наличие товара в магазине

Выходные документы:
1 Для каждого магазина из заданного списка номеров выдать информацию о товарах с подсчетом их стоимости, упорядоченную по наименованиям товаров.
2 Выдать информацию о магазинах, упорядоченную по их адресам, с подсчетом средней площади всех магазинов.
## ER-диаграмма
<img width="914" height="344" alt="Untitled" src="https://github.com/user-attachments/assets/5e5d8670-761e-4bb2-bbce-273bdfeae75d" />

**Описание таблиц**

**Магазины**
- id - идентификатор магазина
- наименование - название магазина
- адрес - адрес магазина
- площадь - площадь магазина

**Товары**
- id - идентификатор товара
- наименование - название товара
- сорт - сорт товара
  
**Товары в магазинах**
- id - идентификатор записи
- магазин_id - ссылка на магазин
- товар_id - ссылка на товар
- единица_измерения - единица измерения товара
- цена - цена за единицу товара
- количество - количество товара в магазине
# Лабораторная работа 2. Инсталляция БД на сервере
**Логическая модель**
сущности:
- **Магазины** — хранение информации о магазинах
- **Товары** — хранение информации о товарах
- **Товары в магазинах** — учет наличия товаров в конкретных магазинах с указанием цены и количества
Связь между сущностями **Магазины** и **Товары** является связью
многие-ко-многим и реализуется с помощью таблицы **Товары в магазинах**


**Физическая модель**
  <img width="1280" height="670" alt="image" src="https://github.com/user-attachments/assets/6ee9f413-ee0e-433a-af36-9c6aabcb5d6a" />

## Заполнение таблиц
<img width="828" height="838" alt="image" src="https://github.com/user-attachments/assets/a4fca135-67df-4ea9-bdbd-3077753bcdc9" />

**Вот таблицы**
<img width="564" height="1077" alt="image" src="https://github.com/user-attachments/assets/31401d6e-0ab8-496c-b9c5-5173f05ad258" />


## Проверка нормальных форм

**Первая нормальная форма (1НФ):**
- Все таблицы имеют первичные ключи
- Все атрибуты атомарны
- Повторяющиеся группы отсутствуют

**Вторая нормальная форма (2НФ):**
- Все таблицы находятся в 1НФ
- Все неключевые атрибуты полностью зависят от первичного ключа

**Третья нормальная форма (3НФ):**
- Транзитивные зависимости отсутствуют
- Данные разделены по сущностям

## SELECT-запросы
<img width="1280" height="833" alt="image" src="https://github.com/user-attachments/assets/eada9e43-9773-4357-90bf-5fb750d7fd8e" />
<img width="1008" height="846" alt="image" src="https://github.com/user-attachments/assets/43d7f1a2-0922-4f44-bbf8-3be8a63ecafd" />

## Лабораторная работа 3. Представления и процедуры

**Цель: Освоение механизмов абстракции данных и программных модулей.**

## Представления

### Представление 1: Отчет по товарам в магазинах

**Views**

Представление предназначено для формирования отчета по товарам в магазинах с подсчетом общей стоимости каждого товара
<img width="1139" height="823" alt="image" src="https://github.com/user-attachments/assets/f48267b8-3319-4d4f-ac84-c7db79ad67a8" />

**Пример использования представления:**

<img width="800" height="814" alt="image" src="https://github.com/user-attachments/assets/389aa462-4655-456a-8b03-283e6bc9ae15" />

### Представление 2: Статистика по магазинам

Представление формирует  информацию по каждому магазину: количество товаров, суммарное количество единиц товара и общую стоимость

<img width="881" height="604" alt="image" src="https://github.com/user-attachments/assets/d8c34e99-1572-43e2-9acc-90f13aa5c63b" />

**Пример использования представления:**
<img width="897" height="947" alt="image" src="https://github.com/user-attachments/assets/576591ea-d8f4-4f47-ac6d-5bd4b895c5ce" />

## Хранимая процедура

Процедура добавления товара в магазин

Процедура add_product_to_shop предназначена для добавления товара в конкретный магазин с проверкой корректности входных данных
Если товар уже присутствует в магазине, происходит обновление количества.

**Параметры процедуры**

- идентификатор магазина
- дентификатор товара
- единица измерения
- цена
- количество
<img width="1409" height="917" alt="image" src="https://github.com/user-attachments/assets/7ed42edd-68d2-4840-917f-0c23522ff80d" />

**Проверка работы процедуры**

<img width="1036" height="1046" alt="image" src="https://github.com/user-attachments/assets/b15009a0-3801-4b41-aff6-6d3bb901b0e8" />


**Проверка ошибка**

<img width="1083" height="879" alt="image" src="https://github.com/user-attachments/assets/16c1d670-cda3-4cbb-8232-8f32f8ce0af2" />


<img width="985" height="878" alt="image" src="https://github.com/user-attachments/assets/c72e0868-f3f7-4dc1-92ee-25a87a5db505" />

<img width="1211" height="878" alt="image" src="https://github.com/user-attachments/assets/12f53f5b-4e20-4140-be70-55d7673460d9" />

# Лабораторная работа 4  Анализ производительности базы данных 

**Цель - Освоение методов анализа и оптимизации производительности БД.**

**Для анализа производительности база данных была заполнена большим объемом данных**

<img width="607" height="511" alt="image" src="https://github.com/user-attachments/assets/102a00dc-bb3e-476e-b7b7-f45ed849e73f" />

<img width="576" height="278" alt="image" src="https://github.com/user-attachments/assets/56ecc337-74ed-4e5a-bbdb-c9a8c901c72a" />

<img width="844" height="446" alt="image" src="https://github.com/user-attachments/assets/455cba0b-a481-44f7-b208-0456fc125804" />

## Анализ производительности без оптимизации

<img width="940" height="1229" alt="image" src="https://github.com/user-attachments/assets/6ba8457e-707a-4bc2-bf51-d1381ce07e12" />

<img width="707" height="310" alt="image" src="https://github.com/user-attachments/assets/81d2f790-ee77-4a08-a783-1f9494dc53d4" />

**Создание индексов**

<img width="731" height="888" alt="image" src="https://github.com/user-attachments/assets/e2ade9ba-65e5-4fba-b16a-84a8130a349d" />

**Повторный анализ после оптимизации**

<img width="984" height="1301" alt="image" src="https://github.com/user-attachments/assets/4d05b024-655c-4f85-bdcf-d94d268d4dc7" />


<img width="773" height="309" alt="image" src="https://github.com/user-attachments/assets/e4eda99f-35d3-4306-9aaa-beb6e350ca53" />

**Без иднексов**

Тип сканирования Seq Scan

**C индексами** 

Bitmap Scan

До оптимизации время выполнения запроса состовляло 3.658 мc, происходило сканирование всей стаблицы из 20000 строк.
После оптимизации выполнение запроса происходит по индексу и составляет 0.083 мс, что в 45 раз быстрее.

# Лабораторная работа 5. Триггеры и аудит

**Цель - Реализация бизнес-логики на уровне БД и системы аудита**

## 1 Каскадное удаление товаров магазина

**При удалении магазина автоматически удаляются все связанные записи о товарах в этом магазине**

<img width="1114" height="948" alt="image" src="https://github.com/user-attachments/assets/78981f23-817b-4068-b177-72f1e492088b" />

**Триггер**
<img width="1020" height="944" alt="image" src="https://github.com/user-attachments/assets/9f500a67-d44d-4d5b-b5ee-ab320233007a" />

## 2 Каскадное удаление товара из всех магазинов

**Функция каскадного удаления**
**При удалении товара он автоматически удаляется из всех магазинов.**
<img width="1029" height="966" alt="image" src="https://github.com/user-attachments/assets/6f5b9582-9e21-4f9f-8a69-0dd2f0feca35" />

**trigger**
<img width="880" height="951" alt="image" src="https://github.com/user-attachments/assets/0cfee429-27d1-4480-88a6-dd48fcafcae7" />

## 3 Таблица аудита изменений
**Для хранения истории изменений создана универсальная таблица аудита**
<img width="935" height="1020" alt="image" src="https://github.com/user-attachments/assets/e795011e-1010-4124-8b01-64eea3e08d4d" />

## 4 Универсальная функция аудита изменений
**Функция фиксирует операции INSERT, UPDATE и DELETE для таблиц базы данных**
<img width="1046" height="900" alt="image" src="https://github.com/user-attachments/assets/d208e76d-e82e-474c-8d56-3467c2bd7d0f" />

## 5 Проверка работы аудита
**INSERT**
<img width="685" height="892" alt="image" src="https://github.com/user-attachments/assets/8fd34214-2ca8-4ae1-afc2-d6e6a8153973" />
**UPDATE**
<img width="823" height="892" alt="image" src="https://github.com/user-attachments/assets/f615b5c4-bc37-4d24-b9ba-6f60fc4fd08a" />
**DELETE**
<img width="844" height="880" alt="image" src="https://github.com/user-attachments/assets/de8ca8a7-8274-4c98-a3d4-14ef9bc3a30f" />

## 6 Просмотр журнала аудита
<img width="1404" height="1122" alt="image" src="https://github.com/user-attachments/assets/12309e9b-d29d-4c3a-94e2-96b8a734c662" />

