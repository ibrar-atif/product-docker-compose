Build docker image for input and product service in repective location

Step1. product service directory
mvn clean install
Step2.
docker build -f Dockerfile -t product-service .

Step 3. input service directory
mvn clean install

docker build -f Dockerfile -t input-service .

Step 4. Create docker network
docker network create product-network

Step 5. Run docker compose
docker-compose -f product-docker.yml up


Input Service api
http://localhost:8086/swagger-ui.html#/reader-controller

1. Read File and push to Kafka
http://localhost:8086/read/{filename}
---http://localhost:8086/read/dataExample.csv

2. Upload File
http://localhost:8086/upload?replace=true

Replace existing file from new file
http://localhost:8086/upload?replace=true


Product Service
http://localhost:8087/swagger-ui.html#/product-controller


1. Get All record

Returns 20 records
http://localhost:8087/allproduct

with param 
For pagination
http://localhost:8087/allproduct?index=0&size=40

2. count for today's date
http://localhost:8087/count

Count for specific range
http://localhost:8087/count?startDate=2019-09-10&endDate=2019-09-10
