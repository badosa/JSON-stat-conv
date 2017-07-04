# JSON-stat-conv

Command line tools for converting [JSON-stat](https://json-stat.org) documents.

```
npm install -g jsonstat-conv
```

Available commands:

* [csv2jsonstat](#csv2jsonstat) - converts CSV into JSON-stat
* [jsonstat2array](#jsonstat2array) - converts JSON-stat into an array of arrays
* [jsonstat2arrobj](#jsonstat2arrobj) - converts JSON-stat into an array of objects
* [jsonstat2csv](#jsonstat2csv) - converts JSON-stat into CSV
* [jsonstat2object](#jsonstat2object) - converts JSON-stat into an object

## Example

Get unemployment rate time series by country from Eurostat and convert it to CSV.

```
curl http://ec.europa.eu/eurostat/wdds/rest/data/v2.1/json/en/tesem120?precision=1 -o unr.jsonstat

jsonstat2csv unr.jsonstat unr.csv
```

Or using the stream interface:

```
curl http://ec.europa.eu/eurostat/wdds/rest/data/v2.1/json/en/tesem120?precision=1 | jsonstat2csv > unr.csv -t
```

More in the [Examples page](https://github.com/badosa/JSON-stat-conv/wiki/Examples).

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

## csv2jsonstat

Converts CSV into JSON-stat.

```
csv2jsonstat galicia.csv galicia.json
```

#### --vlabel (-v)

String. Specifies the name of the value column. When not provided, the value column must be the last one.

```
csv2jsonstat galicia.csv galicia.json --vlabel val
```

#### --slabel (l)

String. Specifies the name of the status column. Default is "Status". If no column has the specified name, no status information will be included in the output.

```
csv2jsonstat oecd.csv oecd.json --slabel stat
```

#### --column (-c)

String. Column separator. Default is ",".

```
csv2jsonstat galicia.ssv galicia.json --column ";"
```

#### --decimal (-d)

String. Decimal separator. Default is ".", unless column separator is ";" (then default is ",").

```
csv2jsonstat galicia.tsv galicia.json --column "\t" --decimal ","
```

#### --label (-a)

String. Dataset label.

```
csv2jsonstat galicia.csv galicia.json --label "Imported from galicia.csv"
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

#### --meta (-m)

Boolean. Returns a metadata-enriched output (object of objects, instead of array of objects).

```
jsonstat2arrobj oecd.json oecd-objobj.json --meta
```

#### --comma (-k)

Boolean. Represents values as strings instead of numbers with comma as the decimal mark.

```
jsonstat2arrobj canada.json canada-comma.json --comma
```

#### --by (-b)

String. Transposes data by the specified dimension. String must be an existing dimension ID. Otherwise it will be ignored.

```
jsonstat2arrobj oecd.json oecd-transp.json --by area
```

#### --bylabel (-l)

Boolean. Uses labels instead of IDs to identify categories of the transposed dimension, unless --cid has been specified.

```
jsonstat2arrobj oecd.json oecd-transp.json --by area --label
```

#### --prefix (-p)

String. Text to be used as a prefix in the transposed categories. Only valid in combination with --by.

```
jsonstat2arrobj oecd.json oecd-transp.json --by area --prefix "AREA:"
```

#### --drop (-d)

String. Comma-separated dimension IDs to be dropped from the output. Dimensions with more than one category cannot be dropped. Only valid in combination with --by.

```
jsonstat2arrobj canada.json canada-transp.json --by concept --drop country,year
```

## jsonstat2csv

Converts JSON-stat into CSV.

```
jsonstat2csv oecd.json oecd.csv
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
jsonstat2csv oecd.json oecd.ssv --column ";"
```

#### --decimal (-d)

String. Decimal separator. Default is ".", unless column separator is ";" (then default is ",").

```
jsonstat2csv oecd.json oecd.tsv --column "\t" --decimal ","
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
