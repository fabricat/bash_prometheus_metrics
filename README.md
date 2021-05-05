# bash_prometheus_metrics

The following global variables *can* be used:
* `metrics_prefix` (string, optional, default: no prefix)\
  If present, will be prefixed to all metric names ("_" is implicit).\
  *Example: metrics_prefix="my"*
* `metrics_array` (array, optional, default: empty array)\
  The metrics will be appended to this initial array.\
  *Example: metrics_array=("my_metric1 1.31" "my_metric2 90.0")*

`exporter_add_metric` example:

    exporter_add_metric remote_fetched gauge "Number of remote backups successfully fetched via scp" 1.0 "remote_host:$remote_host;"

`exporter_add_metric` input parameters:
  - `$1` (string)\
    Metric **name**\
    *Example: "storage_bytes"*
  - `$2` ("gauge" or "counter")\
    Metric **type**
  - `$3` (string)\
    Metric **description**\
    *Example: "Number of numbers of something"*
  - `$4` (int or float)\
    Metric **value**\
    *Example: `1.488`*
  - `$5` (string, optional, default: no labels)\
    Metric **labels** (string pairs with ":" as key/value separator and ";" separator between multiple pairs)\
    *Example: "label_one_name:label_one_value;label_two_name:label_two_value"*\
    Important: you cannot use any whitespace in label keys nor values!
  - `$6` (int or float, optional)\
    Additional metric value (identical to `$4` but, if present, **must** be followed by `$7`)
  - `$7` (string, optional)\
    Labels for the additional value (identical to `$5`)

Note: `$6` and `$7` can be repeated several times (each with a unique label set).

Take always into account the best practices about [metric and label naming](https://prometheus.io/docs/practices/naming/).