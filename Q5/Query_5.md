Question:
Fetch the following data for completed order items in July of 2023
ORDER_ID
ORDER_ITEM_SEQ_ID
SHOPIFY_ORDER_ID
SHOPIFY_PRODUCT_ID

```sql
SELECT
oi.ORDER_ID,
oi.order_item_seq_id,
oid.id_value AS SHOPIFY_ORDER_ID,
gi.id_value AS SHOPIFY_PRODUCT_ID
FROM order_item oi
JOIN order_status AS os ON oi.order_id=os.order_id and oi.status_id = os.status_id and oi.order_item_seq_id = os.order_item_seq_id
JOIN good_identification AS gi ON gi.product_id=oi.product_id
JOIN order_identification AS oid ON oid.order_id=oi.order_id
WHERE oi.status_id='ITEM_COMPLETED' AND os.status_datetime>='2023-07-01 00:00:00.000' AND os.status_datetime<'2023-08-01' AND gi.good_identification_type_id='SHOPIFY_PROD_ID' AND oid.order_identification_type_id='SHOPIFY_ORD_ID'

```
