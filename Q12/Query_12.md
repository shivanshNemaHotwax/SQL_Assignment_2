Question:
Get all the appeasements in July month.
How do we differentiate between returns and appeasements?
Get all the below fields 
RETURN_ID
ENTRY_DATE 
RETURN_ADJUSTMENT_TYPE_ID
AMOUNT
COMMENTS 
ORDER_ID
ORDER_DATE 
RETURN_DATE
PRODUCT_STORE_ID

```sql
select 
rh.RETURN_ID,
rh.ENTRY_DATE ,
ra.RETURN_ADJUSTMENT_TYPE_ID,
ra.AMOUNT,
ra.COMMENTS ,
ra.ORDER_ID,
oh.ORDER_DATE, 
rh.RETURN_DATE,
oh.PRODUCT_STORE_ID
from return_adjustment as ra
join return_header as rh on rh.return_id = ra.return_id 
AND rh.return_date between '2023-07-01' AND '2023-07-30'
join order_header as oh on ra.order_id = oh.order_id
where ra.return_adjustment_type_id = 'APPEASEMENT';
```
