# Проект по базам данных
## Тема: Сервис по распределения заказов

В данном проекте я моделирую ПО овтоматизации работы доставки магазина. На складе имеются товары, которые необходимо распределить среди заказчиков. местоположения каждого заказчика для формирования плана поездки для курьера и другая информация. Так же на основе заказов и факта наличия товаров на складе можут фомироваться заказы у производителя. Заказы клиентов преобразуются в план доставки для курьера. Курьер развозит товары по плиентам.

**Таблица Товаров**  Уникальный ключ - id товара, его цена, описание.

**Наименования товаров на складе**  Список товаров на складе и их количество

**Заказы**  Товары, которые ожидает получить заказчик, их количество, время доставки. Для каждого заказа.

**История заказов** SCD 4 т.к. это по умолчанию разделяет заказы на активные и выполненные

**Заказчики**  Указаны местоположения каждого заказчика для формирования плана поездки для курьера и другая информация.

**Производители**  Указаны производители каждого товара

## Физическая модель
#### customers
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| customer_id | customer`s ID | SERIAL | NOT NULL UNIQUE PRIMARY KEY |
| customer_name |  customer`s name | VARCHAR(20) | NOT NULL |
| customer_adress | customer`s adress | VARCHAR(40) | NOT NULL |

#### products
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| product_id | product`s ID | SERIAL | NOT NULL UNIQUE PRIMARY KEY |
| producer_id | product`s producer ID | SERIAL | NOT NULL |
| product_name |  product`s name | VARCHAR(40) | NOT NULL |
| product_description |  product`s description | VARCHAR(40) | NOT NULL |
| price | price | INGEGER | NOT NULL |

#### Orders (версионная таблица)
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| order_id | orders`s ID | SERIAL | NOT NULL |
| customer_id | user`s ID | SERIAL | NOT NULL |
| product_id | product`s ID | SERIAL | NOT NULL |
| product_num | product`s number | INTEGER | NOT NULL |
| product | product`s number | INTEGER | NOT NULL |

#### Orders_hist
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| order_id | orders`s ID | SERIAL | NOT NULL |
| customer_id | user`s ID | SERIAL | NOT NULL |
| product_id | product`s ID | SERIAL | NOT NULL |
| product_num | product`s number | INTEGER | NOT NULL |
| product | product`s number | INTEGER | NOT NULL |
| date_time | version_control | timestamp | NOT NULL |

#### stock
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| product_id | product`s ID | SERIAL | NOT NULL |
| product_num | product`s number | INTEGER | NOT NULL |

#### producers
| Field name | Description | Data type | Restrictions |
|---|---|---|---| 
| producer_id | producer`s ID | SERIAL | NOT NULL UNIQUE PRIMARY KEY |
| producer_name |  producer`s name | VARCHAR(40) | NOT NULL |
