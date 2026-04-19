dynamo db advanced features \
1.Advanced Data Modeling \
Composite Primary Keys \
Partition key + sort key \

Enables hierarchical and range-based queries \
Example:
PK = USER#123 \
SK = ORDER#2026-01 \
Single Table Design \
Store multiple entity types in one table \
Use prefixes in keys (USER#, ORDER#, etc.) \
Reduces need for joins and improves performance \
Sparse Indexes \
Only items with certain attributes appear in the index \
Useful for filtering rare data (e.g., “active users only”) \
2. Indexing (Powerful Querying) \
Global Secondary Index (GSI) \
Different partition/sort key than base table \
Enables alternate query patterns \
Local Secondary Index (LSI) \
Same partition key, different sort key \
Must be created at table creation \
3. Streams & Event-Driven Architecture \
DynamoDB Streams \
Captures item-level changes (INSERT, MODIFY, DELETE) \
Integrates with: \
AWS Lambda \
Event-driven pipelines \
Use cases: 
Audit logs \
Real-time analytics \
Trigger workflows \
4. Transactions (ACID Support) \
TransactWriteItems / TransactGetItems \
Multi-item, multi-table transactions \
Ensures: \
Atomicity \
Consistency \
Isolation \
Durability \
Example:  Deduct balance + create order in one operation \
5. Caching & Performance \
DAX (DynamoDB Accelerator) \
In-memory cache \
Microsecond latency \
Fully managed \
Ideal for: \
Read-heavy workloads \
Gaming, ad-tech, real-time apps \
6. Global Tables (Multi-Region) \
Active-Active Replication \
Multi-region writes \
Automatic conflict resolution (last writer wins) \
Use cases:  \
Global apps \
Disaster recovery \
Low-latency access worldwide \
7. TTL (Time To Live) \
Automatic Expiry \
Set timestamp attribute \
DynamoDB deletes item automatically \
Use cases: 
Sessions 
Logs 
Temporary data \
8. Fine-Grained Access Control \
IAM + Condition Keys \
Control access at item level \
Example: \
User can only access their own records \
9. PartiQL Support \
SQL-like Queries \
Query DynamoDB using SQL syntax \
SELECT * FROM Users WHERE userId = '123' \
10. Backup & Restore \
On-Demand Backup \
Full table backup anytime \
Point-In-Time Recovery (PITR) \
Restore to any second in last 35 days \
11. Auto Scaling & Capacity Modes \
On-Demand Mode \
No capacity planning \
Pay per request \
Provisioned + Auto Scaling \
Control costs with predictable workloads \
12. Encryption & Security \
Encryption at Rest (KMS) \
AWS-managed or customer-managed keys \
VPC Endpoints \
Secure private access \
Advanced Query Features \
Filter Expressions \
Server-side filtering (after query) \
Projection Expressions \
Fetch only required attributes \
Conditional Writes \
ConditionExpression: "attribute_not_exists(userId)" \
Prevent overwrites \
Integration Ecosystem \
Works seamlessly with: \
AWS Lambda \
API Gateway \
Kinesis \
Step Functions \
S3 (via export) \
15. Export & Import \
Export to S3 (No impact on table) \
For analytics / data lake \
Import from S3 \
Bulk data loading \

