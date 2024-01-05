## Week 2 Homework

We'll be working with a _customers_ dataset. Use the following url to download the dataset:

`https://github.com/datablist/sample-csv-files/raw/main/files/customers/customers-500000.zip?raw=True`

### Assignment

The following are steps to constructing an ETL pipeline using Mage that were covered in the course. 

- Create a new pipeline, call it `customers_etl`
- Add a data loader block and use Pandas to read data directly from the url above (hint: the file is compressed)
  - Add an assertion that checks the number of rows in the dataset is 500,000.
  - `BONUS`: Add an assertion that ensures _all_ `Customer IDs` have the same length.
- Add a transformer block and perform the following:
  - Drop the `Index` column.
  - Rename all of the columns to lowercase, replace spaces with underscores. BONUS: do this dynamically.
  - Create a `protocol` column that extracts the protocol from the `website` column.
  - Drop customers with unsecure websites (i.e. `http` protocol).
- Using a Postgres data exporter (SQL or Python), write the dataset to a table called `customers` in a schema `mage`. Replace the table if it already exists.
  - `BONUS`: Write your data as Parquet files to a bucket in GCP, partioned by `subscription_date`.
- Schedule your pipeline to run daily at 5AM UTC.
- Join the [Mage Slack](https://mage.ai/chat) channel and say hi 👋

### Solution

Want to check your project? Save your changes (in a branch using Git), then run

```bash
git checkout solutions
&& docker compose up
```

Then navigate to `http://localhost:6789/pipelines/homework/edit?sideview=tree` to see the solution.