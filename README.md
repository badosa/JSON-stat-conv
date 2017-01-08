# JSON-stat-conv

Command line tools for converting [JSON-stat](https://json-stat.org) documents.

```
npm install -g jsonstat-conv
```

Available commands:

* [jsonstat2array](#jsonstat2array) - converts JSON-stat into an array of arrays
* [jsonstat2arrobj](#jsonstat2arrobj) - converts JSON-stat into an array of objects
* [jsonstat2csv](#jsonstat2csv) - converts JSON-stat into CSV
* [jsonstat2object](#jsonstat2object) - converts JSON-stat into an object

## Example

Get unemployment rate time series from Eurostat and convert to CSV.

```
curl 'http://ec.europa.eu/eurostat/wdds/rest/data/v2.1/json/en/tesem120?sex=T&precision=1&age=TOTAL&s_adj=NSA' -o unr.json
jsonstat2csv unr.json unr.csv
```

## Shared options

### --help

Shows command's help.

```
jsonstat2csv --help
```

### --version

Shows jsonstat-conv version.

```
jsonstat2csv --version
```

## jsonstat2array

Converts JSON-stat into an array of arrays.

```
jsonstat2array oecd.json oecd-array.json
```

### Options

#### --status

Boolean. Includes status information.

```
jsonstat2array oecd.json oecd-array.json --status
```

#### --vlabel

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2array oecd.json oecd-array.json --vlabel val
```

#### --slabel

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2array oecd.json oecd-array.json --status --slabel stat
```

#### --fid

Boolean. Identifies dimensions, value and status by ID instead of label.

```
jsonstat2array oecd.json oecd-array.json --fid
```

#### --cid

Boolean. Identifies categories by ID instead of label.

```
jsonstat2array oecd.json oecd-array.json --cid
```

## jsonstat2arrobj

Converts JSON-stat into an array of objects.

```
jsonstat2arrobj oecd.json oecd-arrobj.json
```

#### --status

Boolean. Includes status information.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --status
```

#### --cid

Boolean. Identifies categories by ID instead of label.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --cid
```

#### --unit

Boolean. Includes unit information when available.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --unit
```

## jsonstat2csv

Converts JSON-stat into CSV.

```
jsonstat2array oecd.json oecd.csv
```

#### --status

Boolean. Includes status information.

```
jsonstat2csv oecd.json oecd.csv --status
```

#### --vlabel

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2csv oecd.json oecd.csv --vlabel val
```

#### --slabel

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2csv oecd.json oecd.csv --status --slabel stat
```

#### --na

String. Not available symbol. Default is "n/a".

```
jsonstat2csv oecd.json oecd.csv --na ":"
```

#### --column

String. Column separator. Default is ",".

```
jsonstat2csv oecd.json oecd.csv --column ";"
```

To use as column separator a string that starts with "-", write "\\-":

```
jsonstat2csv oecd.json oecd.csv --column "\-|-"
```

#### --decimal

String. Decimal separator. Default is ".".

```
jsonstat2csv oecd.json oecd.csv --column "\t" --decimal ","
```

## jsonstat2object

Converts JSON-stat into an object.

```
jsonstat2object oecd.json oecd-object.json
```

#### --status

Boolean. Includes status information.

```
jsonstat2object oecd.json oecd-object.json --status
```

#### --vlabel

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2object oecd.json oecd-object.json --vlabel val
```

#### --slabel

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2object oecd.json oecd-object.json --status --slabel stat
```

#### --fid

Boolean. Identifies dimensions, value and status by ID instead of label.

```
jsonstat2object oecd.json oecd-object.json --fid
```

#### --cid

Boolean. Identifies categories by ID instead of label.

```
jsonstat2object oecd.json oecd-object.json --cid
```
