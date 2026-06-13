
# Custom Project

## Dataset

The dataset used by my Kafka producer was
`sales_sowers.csv`.

The dataset contains sales transaction records
for products sold in different regions.

Each record includes:

- order_id
- datetime
- region_id
- currency_code
- product_id
- unit_price
- quantity
- is_online
- customer_id
- is_new_customer
- device_type
- payment_method
- referral_source
- discount_code
- customer_note

I used a copied version of the original sales
dataset named `sales_sowers.csv` so I could
make changes without affecting the instructor's
example files.

## Kafka Messages

My producer reads records from
`sales_sowers.csv` and sends them as Kafka
messages.

- Topic: `product-sales-case`
- Message key: `region_id`
- Message value: sales transaction data

The producer streamed six sales records during
each producer run. During testing, multiple
producer runs resulted in twelve messages being
available for consumption.

## Consumer Processing

The consumer receives sales transaction
messages from Kafka.

For each message, the consumer:

- Reads the sales record
- Looks up region tax rates
- Calculates subtotal, tax, and total
- Logs processing details to the console
- Writes valid records to
  `consumed_sales_sowers.csv`
- Stores records in
  `sales_sowers.duckdb`

The consumer processed twelve messages and
displayed running sales statistics.

## Experiments

### Phase 4 Modification

I created personalized project files using the
`_sowers` naming convention.

This included a custom consumer, output CSV
file, and DuckDB database so my work would not
overwrite the example project files.

### Phase 5 Application

I created a Jupyter notebook named
`sales_by_region_sowers.ipynb`.

The notebook grouped sales records by region,
counted orders, ranked regions from highest
to lowest, and created a visualization of
order counts by region.

## Results

The producer successfully streamed sales
records to Kafka.

The consumer successfully processed
12 messages, calculated totals, and saved
the results to both a CSV file and a DuckDB
database.

During the final run, the consumer reported:

- Total sales: $943.74
- Average sale: $78.65
- Minimum sale: $43.19
- Maximum sale: $194.82

The notebook analysis showed that US-CA had
the highest number of sales orders, followed
by US-MO and US-TX.

## Interpretation

### What Changed From the Original Example

I created my own Sowers versions of the project
files and outputs.

The consumer writes processed records to:

- `consumed_sales_sowers.csv`
- `sales_sowers.duckdb`

I also added a Jupyter notebook and chart to
analyze order counts by region.

### What I Learned From Watching Messages Move Through Kafka

Watching messages move through Kafka helped me
understand how producers and consumers work
together in a streaming system.

The producer sent sales records to the Kafka
topic, and the consumer received each record,
calculated tax and totals, enriched the data,
and stored the results.

### What the Stream Could Tell a Business

This stream could help a business monitor sales
activity in near real time.

The business could track incoming orders,
regional activity, and sales performance as
transactions occur.

### Business Intelligence Gained

The consumed messages provided useful business
information, including:

- total sales revenue
- average sale amount
- minimum sale amount
- maximum sale amount
- order activity by region

During my final run, the consumer processed
12 messages and reported:

- Total sales: $943.74
- Average sale: $78.65
- Minimum sale: $43.19
- Maximum sale: $194.82

The regional analysis showed that US-CA had
the highest number of orders, followed by
US-MO and US-TX.

This information could help decision makers
identify strong sales regions and better
understand customer demand patterns.
