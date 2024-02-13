Question:

Fetch the following details for orders completed in August of 2023.
PRODUCT_ID
PRODUCT_TYPE_ID
PRODUCT_STORE_ID 
TOTAL_QUANTITY
INTERNAL_NAME 
FACILITY_ID
EXTERNAL_ID 
FACILITY_TYPE_ID 
ORDER_HISTORY_ID 
ORDER_ID
ORDER_ITEM_SEQ_ID
SHIP_GROUP_SEQ_ID

```sql
select 	oi.PRODUCT_ID,
p.PRODUCT_TYPE_ID,
oh.PRODUCT_STORE_ID,
oi.QUANTITY,
oisg.FACILITY_ID,
oi.EXTERNAL_ID ,
f.FACILITY_TYPE_ID ,
oi.ORDER_ID,
oi.ORDER_ITEM_SEQ_ID,
oisg.SHIP_GROUP_SEQ_ID,
ohi.order_history_id,
p.internal_name
from order_item as oi 
join order_item_ship_group_assoc as oisga on oisga.order_id = oi.order_id and oisga.order_item_seq_id = oi.order_item_seq_id
join order_item_ship_group as oisg on oisg.order_id = oisga.order_id and oisga.ship_group_seq_id = oisg.ship_group_seq_id
join product as p on p.product_id = oi.product_id
join facility as f on oisg.facility_id = f.facility_id
join order_status as os on os.order_id = oi.order_id and os.order_item_seq_id = oi.order_item_seq_id and os.status_id = oi.status_id
join order_header as oh on oi.order_id = oh.order_id
join order_history as ohi on ohi.order_id = oisga.order_id and ohi.order_item_seq_id = oisga.order_item_seq_id and ohi.ship_group_seq_id= oisga.ship_group_seq_id
where oh.status_id = 'ORDER_COMPLETED' AND os.status_datetime between '2023-08-01' and '2023-08-30';

```
