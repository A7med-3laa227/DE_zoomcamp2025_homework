# Question 1

```bash
docker run -it --entrypoint bash python:3.12.8
pip --version
```
Answer: 24.2

# Question 2 

Answer: db:5432

# Question 3

```SQL
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance <= 1  ;
```
```SQL
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance > 1 AND trip_distance <= 3 ;
```
```SQL
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance > 3 AND trip_distance <= 7 ;
```
```SQL
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance > 7 AND trip_distance <= 10 ;
```
```SQL
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance > 10 ;
```
Answer: 104,838; 199,013; 109,645; 27,688; 35,202

# Question 4

```sql
SELECT Lpep_pickup_datetime , MAX(trip_distance) as max
FROM green_trip
GROUP BY Lpep_pickup_datetime
ORDER BY max DESC;
```
Answer: 2019-10-31

# Question 5
```sql
SELECT z."Zone" , SUM(total_amount) as total
FROM zones z JOIN green_trip g
ON z."LocationID" = g."PULocationID"
WHERE DATE(lpep_pickup_datetime) = '2019-10-18' 
GROUP BY z."Zone"
ORDER BY total DESC;
```
Answer: East Harlem North, East Harlem South, Morningside Heights

# Question 6

```sql
SELECT 
    z."Zone", 
    SUM(g.tip_amount) AS largest_tip
FROM 
    zones z 
JOIN 
    green_trip g 
ON 
    z."LocationID" = g."PULocationID"
WHERE 
    EXTRACT(MONTH FROM g.lpep_pickup_datetime::timestamp) = 10
    AND EXTRACT(YEAR FROM g.lpep_pickup_datetime::timestamp) = 2019
GROUP BY 
    z."Zone"
ORDER BY 
    largest_tip DESC;
```
Answer: East Harlem North

# Question 7 

Answer: terraform init, terraform apply -auto-approve, terraform destroy
