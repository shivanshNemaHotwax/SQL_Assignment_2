Question:
Fetch the following columns for created orders. These should be sales orders.
ORDER_ID
TOTAL_AMOUNT
PAYMENT_METHOD
SHOPIFY_ORDER_NAME
NOTE: 
The total amount represents the total amount of the order.
The payment method is the method by which payment was made, like Cash, mastercard, visa, paypal, etc.

```sql
select 
oh.ORDER_ID,
oh.GRAND_TOTAL as TOTAL_AMOUNT,
opp.payment_method_type_id as PAYMENT_METHOD,
oid.ID_VALUE as SHOPIFY_ORDER_NAME
from order_header as oh 
join order_payment_preference as opp on oh.order_id = opp.order_id
join order_identification as oid on oid.order_id = oh.order_id
where oh.status_id = 'ORDER_CREATED' AND  oh.order_type_id ='SALES_ORDER' AND oid.order_identification_type_id = 'SHOPIFY_ORD_NAME'
```
