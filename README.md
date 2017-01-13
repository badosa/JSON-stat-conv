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

Get unemployment rate time series by country from Eurostat and convert it to CSV.

```
curl 'http://ec.europa.eu/eurostat/wdds/rest/data/v2.1/json/en/tesem120?sex=T&precision=1&age=TOTAL&s_adj=NSA' -o unr.json
jsonstat2csv unr.json unr.csv
```

Or using the stream interface:

```
curl 'http://ec.europa.eu/eurostat/wdds/rest/data/v2.1/json/en/tesem120?sex=T&precision=1&age=TOTAL&s_adj=NSA' | jsonstat2csv > unr.csv -t
```

## Shared options

### --help (-h)

Shows command's help.

```
jsonstat2csv --help
```

### --stream (-t)

Use the stream interface:

```
jsonstat2csv < oecd.json > oecd.csv -t
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

#### --status (-s)

Boolean. Includes status information.

```
jsonstat2array oecd.json oecd-array.json --status
```

#### --vlabel (-v)

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2array oecd.json oecd-array.json --vlabel val
```

#### --slabel (-l)

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2array oecd.json oecd-array.json --status --slabel stat
```

#### --fid (-f)

Boolean. Identifies dimensions, value and status by ID instead of label.

```
jsonstat2array oecd.json oecd-array.json --fid
```

#### --cid (-c)

Boolean. Identifies categories by ID instead of label.

```
jsonstat2array oecd.json oecd-array.json --cid
```

## jsonstat2arrobj

Converts JSON-stat into an array of objects.

```
jsonstat2arrobj oecd.json oecd-arrobj.json
```

#### --status (-s)

Boolean. Includes status information.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --status
```

#### --cid (-c)

Boolean. Identifies categories by ID instead of label.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --cid
```

#### --unit (-u)

Boolean. Includes unit information when available.

```
jsonstat2arrobj oecd.json oecd-arrobj.json --unit
```

## jsonstat2csv

Converts JSON-stat into CSV.

```
jsonstat2array oecd.json oecd.csv
```

#### --status (-s)

Boolean. Includes status information.

```
jsonstat2csv oecd.json oecd.csv --status
```

#### --vlabel (-v)

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2csv oecd.json oecd.csv --vlabel val
```

#### --slabel (l)

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2csv oecd.json oecd.csv --status --slabel stat
```

#### --na (-n)

String. Not available symbol. Default is "n/a".

```
jsonstat2csv oecd.json oecd.csv --na ":"
```

#### --column (-c)

String. Column separator. Default is ",".

```
jsonstat2csv oecd.json oecd.csv --column ";"
```

#### --decimal (-d)

String. Decimal separator. Default is ".", unless column separator is ";" (then default is ",").

```
jsonstat2csv oecd.json oecd.csv --column "\t" --decimal ","
```

## jsonstat2object

Converts JSON-stat into an object of arrays in the [Google DataTable format](https://developers.google.com/chart/interactive/docs/reference#dataparam).

```
jsonstat2object oecd.json oecd-object.json
```

#### --status (-s)

Boolean. Includes status information.

```
jsonstat2object oecd.json oecd-object.json --status
```

#### --vlabel (-v)

String. Specifies the label of the value field. Default is "Value".

```
jsonstat2object oecd.json oecd-object.json --vlabel val
```

#### --slabel (-l)

String. Specifies the label of the status field. Default is "Status".

```
jsonstat2object oecd.json oecd-object.json --status --slabel stat
```

#### --fid (-f)

Boolean. Identifies dimensions, value and status by ID instead of label.

```
jsonstat2object oecd.json oecd-object.json --fid
```

#### --cid (-c)

Boolean. Identifies categories by ID instead of label.

```
jsonstat2object oecd.json oecd-object.json --cid
```
