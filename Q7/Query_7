Question:
Fetch all the physical items ordered in the month of September 2023.

```sql
select oi.order_id,oi.order_item_seq_id,pt.is_physical 
FROM order_item as oi
JOIN product as p ON p.product_id=oi.product_id
JOIN product_type as pt ON pt.product_type_id=p.product_type_id and pt.is_physical='Y'
JOIN order_header as oh ON oh.order_id=oi.order_id and oh.order_date between '2023-09-01'
AND '2023-10-01'
Join order_status as os on os.order_id = oi.order_id 
and oi.order_item_seq_id = os.order_item_seq_id 
and os.status_id = oi.status_id;
```
OR

```sql
select oi.order_id,oi.order_item_seq_id,pt.is_physical 
FROM order_item as oi
JOIN product as p ON p.product_id=oi.product_id
JOIN product_type as pt ON pt.product_type_id=p.product_type_id and pt.is_physical='Y'
JOIN order_header as oh ON oh.order_id=oi.order_id and oh.order_date between '2023-09-01'
AND '2023-10-01'
Join order_status as os on os.order_id = oi.order_id and os.status_id <> 'ITEM_CANCELLED'
and oi.order_item_seq_id = os.order_item_seq_id 
and os.status_id = oi.status_id;
```
