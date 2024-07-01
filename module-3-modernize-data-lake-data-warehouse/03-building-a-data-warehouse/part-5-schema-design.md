# Why normalization is not always good

- The original data can be interpreted and stored in many ways in a database. normalizing the data means turning it into a relational system.
- This stores the data efficiently and makes query processing a clear and direct task. Normalizing increases the orderliness of the data, it is useful for saving space.
- Normalizing data usually happens when a schema is designed for a database.
- Denormalizing is the strategy of allowing duplicate field values for a column in a table in the data to gain processing performance. Data is repeated rather than being relational.
- Flattened data takes more storage, but the flattened non-relational organization makes queries more efficient because they can be processed in parallel using columnar processing.
- Specifically, denormalizing data enables BigQuery to more efficiently distribute processing among slots resulting in more parallel processing and better query performance.
- You would usually denormalize data before loading it into BigQuery.
- However, there are cases where denormalizing data is bad for performance. Specifically, if you have to group by a column with a one to many relationship.
- For example, to group the data, it must be shuffled. That often happens by transferring the data over a network between servers or systems. Shuffling is slow.

## Solution - Use Nested and Repeated Fields

- BigQuery supports columns with nested and repeated data.
- A denormalized flattened table is compared with one that has been denormalized and the schema takes advantage of nested and repeated fields.
- Because this is declared in advance, BigQuery can store and process the data respecting some of the original organization in the data.
- Specifically, all order details for each order are co-located, which makes retrieval of the whole order more efficient.
- For this reason, nested and repeated fields are useful for working with data that originates in relational databases.
- Nested columns can be understood as a form of repeated field.
- It preserves the relational qualities of the original data and schema while enabling columnar and parallel processing of the repeated nested fields.
- It is the best alternative for data that already has a relational pattern to it.
- Turning the relation into a nested or repeated field improves BigQuery Performance.
- Nested and repeated fields help BigQuery work with data source in relational databases.
