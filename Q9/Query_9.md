Question:
Find all the orders whose two or more items are canceled but the orders are still in the approved status.

```sql
select * from order_header as oh
join order_item as oi on oh.order_id = oi.order_id
where oi.status_id ='ITEM_CANCELLED' AND oh.status_id = 'ORDER_APPROVED'
GROUP BY oh.order_id having COUNT(oi.order_item_seq_id) >=2;

```
