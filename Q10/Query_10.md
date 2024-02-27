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
oi.PRODUCT_ID,
paBill.city,
paBill.country_geo_id,
paBill.postal_code,
paBill.address1,
paBill.address2,
paShip.city,
paShip.country_geo_id,
paShip.postal_code,
paShip.address1,
paShip.address2
from order_item as oi 
join order_header as oh on oi.order_id = oh.order_id
join product as p on oi.product_id = p.product_id
join order_contact_mech as ocmB on oh.order_id = ocmB.order_id and ocmB.contact_mech_purpose_type_id ='BILLING_LOCATION'
join order_contact_mech as ocmS on oh.order_id = ocmS.order_id and ocmS.contact_mech_purpose_type_id ='SHIPPING_LOCATION'
join postal_address as paBill on ocmB.contact_mech_id = paBill.contact_mech_id 
join postal_address as paShip on ocmS.contact_mech_id = paShip.contact_mech_id 
where oi.status_id = 'ITEM_CREATED' AND oh.order_type_id = 'SALES_ORDER';
```
