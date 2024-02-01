Question:
Fetch all the customers created in June 2023.

```sql
select per.party_id, per.first_name, per.last_name from person as per
join party as pa on pa.party_id = per.party_id
join party_role as pr on pa.party_id = pr.party_id
where pr.role_type_id = 'CUSTOMER' AND pa.created_date between '2023-06-01' AND '2023-06-30';
```
