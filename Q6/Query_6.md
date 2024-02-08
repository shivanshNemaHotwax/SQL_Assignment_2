Question:
Fetch all the physical items completed from Warehouse in September of 2023.

```sql
select oi.order_id, oi.order_item_seq_id from  order_item as oi
join order_item_ship_group_assoc as oisga on oi.order_id = oisga.order_id AND oi.order_item_seq_id = oisga.order_item_seq_id
join order_item_ship_group as oisg on oisga.order_id = oisg.order_id AND oisga.ship_group_seq_id = oisg.ship_group_seq_id
join product as p on oi.product_id = p.product_id
join product_type as pt on pt.product_type_id = p.product_type_id
join facility as f on oisg.facility_id = f.facility_id
join order_status as os on os.order_id = oi.order_id AND os.order_item_seq_id = oi.order_item_seq_id and os.status_id = oi.status_id
where oi.status_id = 'ITEM_COMPLETED' AND f.facility_type_id = 'WAREHOUSE' AND pt.is_physical = 'Y' AND os.status_datetime between '2023-09-01' AND '2023-09-30';
```
