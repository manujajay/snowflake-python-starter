# Snowflake Python Starter

This README provides a guide on how to get started with Snowflake using Python. It includes setting up your environment, connecting to Snowflake, and running basic SQL queries using Python.

## Prerequisites

- Snowflake account
- Python environment
- `pip` for installing Python packages

## Setting Up Your Environment

1. **Install the Snowflake Connector for Python:**
   ```bash
   pip install snowflake-connector-python
   ```

## Configuring Snowflake Credentials

1. **Create a `creds.json` file with your Snowflake credentials:**
   Make sure to replace `your_account`, `your_user`, and `your_password` with your actual Snowflake account details.
   ```json
   {
       "user": "your_user",
       "password": "your_password",
       "account": "your_account",
       "warehouse": "your_warehouse",
       "database": "your_database",
       "schema": "your_schema"
   }
   ```

## Connecting to Snowflake

1. **Create a Python script to connect to Snowflake:**

   Create a file named `connect_snowflake.py` and add the following code:

   ```python
   import snowflake.connector
   import json

   # Load Snowflake credentials
   with open('creds.json') as f:
       config = json.load(f)

   # Create a connection object
   conn = snowflake.connector.connect(
       user=config['user'],
       password=config['password'],
       account=config['account'],
       warehouse=config['warehouse'],
       database=config['database'],
       schema=config['schema']
   )

   print("Successfully connected to Snowflake!")

   # Clean up
   conn.close()
   ```

## Running Queries

1. **Extend the script to run a query:**
   Add this code snippet to the `connect_snowflake.py` file to execute a simple SQL query.
   ```python
   # Open a cursor
   cur = conn.cursor()

   try:
       cur.execute("SELECT CURRENT_VERSION()")
       version = cur.fetchone()
       print(f"Snowflake version: {version[0]}")
   finally:
       cur.close()
   ```

## Conclusion

You've now successfully set up a Python environment to connect and interact with Snowflake. This basic setup allows you to run SQL queries and can be expanded for more complex data operations.

For more detailed information, visit the [Snowflake documentation](https://docs.snowflake.com).
