# QUESTION 1

```bash
docker run -it --entrypoint bash python:3.12.8
pip --version
```
Answer: 24.2

# QUESTION 2 

Answer: db:5432

# QUESTION 3

```
SELECT COUNT(*) 
FROM green_trip
WHERE Lpep_pickup_datetime >= '2019-10-01' AND Lpep_pickup_datetime < '2019-11-01' AND trip_distance > 1 AND  ;
```
