# This project using Python and deployment with AWS EKS

## Form Data
Input your data in here:<br/>
Name Muhammad Rido <br/>
YourCity : Sungailiat

## Application Port
`Port application running on 2000`

## Environment Variable for Apps

- AWS_ACCESS_KEY_ID=ASIA2BU2LERS73LNAYAG
- AWS_SECRET_ACCESS_KEY=4CV170eGXUJaiT2D4iN5zPMYuFkx8JUWY/6Wff0O
- AWS_SESSION_TOKEN=IQoJb3JpZ2luX2VjELL//////////wEaCXVzLXdlc3QtMiJHMEUCIGKsgMAhNj8+adY/5xWmUTYgIHSYqb41yZ4x9H+OF68tAiEAw30bG7DAuQVFzT9pHJ+vDe2GBAK/vomQRWs092UMFlUqswIIm///////////ARABGgw2OTA3Mzk2ODQ0NTMiDEUZRkjQOeLjEABtXCqHAif+3sZmd9xV/D5RK9cOvSvirBedhKN7MS03+9NjzDhIkvdHHkzxSs8cDgCsTf2ZwOZphlawCAiObvkUou8KgcfuXciyzM1ZtIDb8sKjlR9dpevTNZxvXgw9CLBymwYk2NTjKHGs8bl6XBS22SsCzVJyuDfxs2aLDwMnH2U+hJObwrzI8ctWJqgj7ZR6VtgFehO/AnrBuqr6keeEqZKfInKg/Sf10RxEEdEdU91kkgUuwTfM48j1RO1dDXzV5Che/zxrQCoNu6L4ty+a1f+7dETdUzUkExjfqOScYnBewhJSwBk2JyyDt7hE/95A8yJ1NOKrApNrL3rZcvkKdkATDHQ7RJurVmLpMI/NzcIGOp0Bu1jEa49iTFNej8WMrze2IlTErinuHV9CzMVAs3habvzPwe9Pyy46+DcNXnYngF2NRdQvw8vBtwCuzlP2Koh5MPWfikneinwPWhKHR9OgjpCXpKaKwX+mmz8h6+ModLBYsPDRp9UjfQ3G2zDfu3tqjcCHvcGxZbX9t0nvGNpvIT9Q503nOZvozzlKQBUVLUf5xzWjvRMnqUFkHJPsBQ==
- AWS_REGION=your default region
- ATHENA_DB=your db athena
- S3_STAGING_DIR=your destination s3 bucket
- FLASK_SECRET_KEY=lks
- API_GATEWAY_URL=your url api gateway
- SNS_TOPIC_ARN=your sns topic
- ATHENA_SCHEMA_NAME=your db athena


## Environment for Github Action
- AWS_ACCESS_KEY_ID=your access key id
- AWS_SECRET_ACCESS_KEY=your secret access key
- AWS_SESSION_TOKEN=your session token
- AWS_REGION=your default region
- ECR_REGISTRY= your ecr registry id
- ECR_REPOSITORY = your ecr name
- CLUSTER_NAME = your name cluster EKS

## Install Dependencies
`pip install -r requirements.txt`

## 📊 Query Athena


```sql
CREATE EXTERNAL TABLE IF NOT EXISTS rekognition_results_db.rekognition_results_table (
  image_key string,
  labels array<struct<Name:string, Confidence:double>>
)
ROW FORMAT SERDE 'org.openx.data.jsonserde.JsonSerDe'
WITH SERDEPROPERTIES (
  'serialization.format' = '1'
)
LOCATION 's3://your-destination-bucket/results'
TBLPROPERTIES ('has_encrypted_data'='false');
