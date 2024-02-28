Question:
Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.
```sql
select ii.product_id, sum(iiv.available_to_promise_var) from inventory_item as ii 
join inventory_item_variance as iiv on ii.inventory_item_id = iiv.inventory_item_id
where iiv.variance_reason_id in ('VAR_LOST' ,'VAR_DAMAGED')
group by ii.product_id;
```
