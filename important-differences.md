# Important SQL differences between Snowflake and BigQuery:

1. Type handling in UNION operations:
   - BigQuery requires exact data type matching between corresponding columns in UNION operations.
   - Snowflake is more lenient and performs implicit type conversions in UNION operations.
   - Always check date/timestamp fields, numeric fields, and string types when assessing cross-compatibility.
   - Common type mismatches occur between: 
     * TIMESTAMP and STRING
     * FLOAT and INTEGER
     * VARCHAR and STRING

2. When assessing SQL for cross-compatibility:
   - Explicitly identify all column data types in each part of UNION queries
   - For date/time columns, check if they need explicit casting
   - Add explicit CAST() operations to ensure type consistency across UNION branches
   - Remember that what works in Snowflake may fail in BigQuery due to stricter type enforcement

3. Best practices for cross-compatible SQL:
   - Always use explicit type casting in UNION operations
   - Use CAST() functions to ensure matching types
   - When in doubt, convert temporal data to consistent formats
   - Test queries on both platforms before declaring them cross-compatible
