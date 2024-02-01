Question:

Fetch all the order items that are in the created status and the order type should be a sales order
ORDER_ID
PRODUCT_TYPE_ID
ORDER_LINE_ID
EXTERNAL_ID
SALES_CHANNEL
QUANTITY
ITEM_STATUS 
PRODUCT_ID
BILL_CITY
BILL_COUNTRY
BILL_POSTALCODE
BILL_ADDRESS1
BILL_ADDRESS2
SHIP_CITY
SHIP_COUNTRY
SHIP_POSTALCODE
SHIP_ADDRESS1
SHIP_ADDRESS2

```sql
select 
oi.ORDER_ID,
p.PRODUCT_TYPE_ID,
oi.order_item_seq_id,
oi.EXTERNAL_ID,
oh.sales_channel_enum_id,
oi.QUANTITY,
oi.status_id,
oi.PRODUCT_ID
from order_item as oi 
join order_header as oh on oi.order_id = oh.order_id
join product as p on oi.product_id = p.product_id
where oi.status_id = 'ITEM_CREATED' AND oh.order_type_id = 'SALES_ORDER';
```
