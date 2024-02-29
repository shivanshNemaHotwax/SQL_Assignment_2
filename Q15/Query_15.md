Question:
Find all the orders that have more than one return.

```sql
select order_id from return_item 
where order_id is not null
group by order_id having count(distinct return_id) >1;

```

OR
```sql
select order_id from return_item as ri
join return_header as rh on rh.return_id = ri.return_id 
and rh.status_id <> 'RETURN_CANCELLED'
where ri.order_id is not null
group by ri.order_id having count(distinct ri.return_id) >1;
```
