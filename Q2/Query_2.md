Question:
Fetch the following columns for completed return items of SM_STORE for ecom return channel.
RETURN_ID 
ORDER_ID
PRODUCT_STORE_ID 
STATUS_DATETIME
ORDER_NAME 
FROM_PARTY_ID 
RETURN_DATE 
ENTRY_DATE
RETURN_CHANNEL_ENUM_ID

```sql
select 
rh.RETURN_ID,
ri.ORDER_ID,
oh.PRODUCT_STORE_ID,
rs.STATUS_DATETIME,
oh.ORDER_NAME, 
rh.FROM_PARTY_ID, 
rh.RETURN_DATE, 
rh.ENTRY_DATE,
rh.RETURN_CHANNEL_ENUM_ID from return_header as rh
join return_item as ri on rh.return_id = ri.return_id
join order_header as oh on oh.order_id = ri.order_id
join return_status as rs on rs.return_id = ri.return_id
where rh.status_id = 'RETURN_COMPLETED' AND oh.product_store_id = 'SM_STORE' AND rh.RETURN_CHANNEL_ENUM_ID='ECOM_RTN_CHANNEL';

```