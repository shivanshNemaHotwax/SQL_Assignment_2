Question:
Fetch the following columns for completed order items for sales orders of SM_STORE product store and that are physical items.
ORDER_ID
ORDER_ITEM_SEQ_ID
PRODUCT_ID
PRODUCT_TYPE_ID
IS_PHYSICAL
IS_DIGITAL
SALES_CHANNEL_ENUM_ID
ORDER_DATE
ENTRY_DATE
STATUS_ID
STATUS_DATETIME
ORDER_TYPE_ID
PRODUCT_STORE_ID 

```sql
select
oi.ORDER_ID,
oi.ORDER_ITEM_SEQ_ID,
p.PRODUCT_ID,
pt.PRODUCT_TYPE_ID,
pt.IS_PHYSICAL,
pt.IS_DIGITAL,
oh.SALES_CHANNEL_ENUM_ID,
oh.ORDER_DATE,
oh.ENTRY_DATE,
oi.STATUS_ID,
os.STATUS_DATETIME,
oh.ORDER_TYPE_ID,
oh.PRODUCT_STORE_ID
from order_header as oh
join order_item as oi on oh.order_id = oi.order_id AND oi.status_id = 'ITEM_COMPLETED'
join order_status as os on oi.order_id = os.order_id 
AND oi.order_item_seq_id = os.order_item_seq_id AND oi.status_id = os.status_id
join product as p on oi.product_id = p.product_id
join product_type as pt on p.product_type_id = pt.product_type_id
where oh.order_type_id ='SALES_ORDER' AND oh.product_store_id = 'SM_STORE' 
AND pt.is_physical ='Y';
```
