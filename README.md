# bash\_exporter\_lib

You need 2 global variables to use this lib:
* metrics\_prefix  
  Prefix ll be added to all metric names, string  
  Example: `metrics_prefix="my_exporter_prefix"`  

* metrics_array  
  Metrics receiver, array  
  Example: `metrics_array=()`  

## exporter\_add\_metric

Example:  
`exporter_add_metric remote_fetched gauge "Number of remote backups successfully fetched via scp" "remote_host:$remote_host;" 1`


Input options:
* $1  
  Metric name, string  
  Example: `"some_metric_name"`  

* $2  
  Metric type, "gauge" or "counter"  
  Example: `"gauge"`  

* $3  
  Metric description, string  
  Example: `"Number of numbers of something"`  

* $4  
  Metric labels struct, string pairs with ":" separator within pair and ";" separator between pairs  
  Example: `"label_one_name:label_one_value;label_two_name:label_two_value"`  
  _You cannot use any whitespace in label keys or values_

* $5  
  Metric value, int or float  
  Example: `"1.488"`  
# bash_prometheus_metrics
