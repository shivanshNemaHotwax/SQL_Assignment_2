
Question:
Fetch the order id and contact mech id for the shipping address of the orders completed in October of 2023.

```sql
select ocm.order_id, ocm.contact_mech_id 
from order_header as oh
join order_status as os on oh.order_id = os.order_id 
and oh.status_id = os.status_id and os.status_id = 'ORDER_COMPLETED'
and os.status_datetime between '2023-10-01' and '2023-11-01'
join order_contact_mech as ocm on ocm.order_id = oh.order_id 
and ocm.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
```
