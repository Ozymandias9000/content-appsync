# Content-Appsync

## Start

```
npm i -g serverless
npm i
sls offline start
```

## Seeding Local DynamoDB

The raw files exported from AWS DataPipeline were not valid JSON. Below are the steps to make those files work:

- Used `sed '$!s/$/,/' ./ddb_data_export_1-10-20/rawData/data1.json > ./ddb_data_export_1-10-20/seedData.json` to add
  commas to the end of each line except last
- Manually wrapped json in `[]` and removed comma from first line
- Did find and replace on attribute values to capitalize all, ex: `"s"` ⇒ `"S"`
- make sure sources in serverless.yml uses key `rawsources` for seed file

If another data dump from DDB is needed, this looks like an easier option:
[https://pypi.org/project/export-dynamodb/](https://pypi.org/project/export-dynamodb/)
