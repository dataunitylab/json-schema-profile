# JSON Schema Profile

The goal of JSON Schema Profile is to augment the vocabulary of [JSON Schema](http://json-schema.org/) to represent properties of the data as opposed to focusing only on the structure.

## Definitions
### Bloom filter
This is a string which represents a serialized Bloom filter. Currently this is a Base64 encoded serialized value of the specific Bloom filter class used by [JSONoid](https://github.com/dataunitylab/jsonoid-discovery), but we plan to make this a more reusable format.

Bloom filters are useful to check if specific values were observed for a particular property without the need to store all the values.

### Histogram
property           | description
:--                | :--
`bins`             | An array of two-element arrays where the first element is the mean of the bin and the second is the number of elements in the bin
`hasExtremeValues` | A Boolean indicating whether the histogram contains values which cannot be represented in the given bounds. This usually only occurs for extremely large absolute values and is rarely observed in practice

### Statistics
property   | description
:--        | :--
`variance` | The variance of all values of this property
`stdev`    | The standard deviation of all values of this property
`skewness` | The skewness of all values of this property
`kurtosis` | The kurtosis of all values of this property

## Arrays
property          | description
:--               |:--
`lengthHistogram` | A [histogram](#Histogram) of array lengths

## Booleans

property  | description
:--       |:--
`pctTrue` | Percentage of the Boolean values which are `true`

## Integers

property         | description
:--              | :--
`bloomFilter`    | A [Bloom filter](#bloom-filter) of integer values
`distinctValues` | An estimate of the number of distinct values (cardinality) of this property
`histogram`      | A [histogram](#histogram) of integer values
`statistics`     | A set of [statistics](#statistics) of integer values

## Numbers

property         | description
:--              | :--
`bloomFilter`    | A [Bloom filter](#bloom-filter) of number values
`distinctValues` | An estimate of the number of distinct values (cardinality) of this property
`histogram`      | A [histogram](#histogram) of number values
`statistics`     | A set of [statistics](#statistics) of number values

## Objects

property         | description
:--              | :--
`fieldPresence`  | An object where the value represents the percentage of the time the corresponding key appears

## Strings
property          | description
:--               |:--
`bloomFilter`     | A [Bloom filter](#bloom-filter) of string values
`distinctValues`  | An estimate of the number of distinct values (cardinality) of this property
`lengthHistogram` | A [histogram](#Histogram) of string lengths
