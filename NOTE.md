# Short note

**a.** `customer_id` is a new id that Olist creates for every order, so it is unique and matches exactly one order, while `customer_unique_id` stays the same for the same person (96,096 distinct values for 99,441 rows, and one person has 17 customer_ids). To count customers I would use `count(DISTINCT customer_unique_id)`, because counting `customer_id` really counts orders.

**b.** `order_items` is the junction table: it resolves the many-to-many between orders and products (an order can have many products and a product can be in many orders), and also the one between orders and sellers.

**c.** The data is stricter than my diagram for customers *places* orders: I drew "one or many" but every customer_id has exactly one order (min = max = 1). The circle on orders *contains* order_items is justified by the data because 775 orders have no items at all, mostly `unavailable` and `canceled` ones.
