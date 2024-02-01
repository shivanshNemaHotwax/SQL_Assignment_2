Question:
Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.
```sql
select * from inventory_item_variance where variance_reason_id in ('VAR_LOST' ,'VAR_DAMAGED');
```
