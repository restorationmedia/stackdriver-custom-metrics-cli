# StackDriver Custom Metrics CLI

This tool is designed to send custom metrics from any \*nix system with an easy to use cli tool - `stackc`

To get started just globally install this package:
```
npm install -g stackdriver-custom-metrics-cli
```

**Note**: You MUST have `gcloud` cli installed and have a default service account activated for this software to work as is.

# Create Metrics

Here's how to insert your custom metrics...

```
stackc -p [PROJECT_NAME] create -b [JSON RESOURCE STRING HERE]
```

Sample JSON Resource:

```
{
  "timeSeries": 
  [
    {
      "metric": 
      {
        "type": "custom.googleapis.com/my/custom/metric",
        "labels": 
        {
          "key": "val"
        }
      },
      "metricKind": "GAUGE",
      "valueType": "INT64",
      "points": 
      [
        {
          "interval": 
          {
            "startTime": "2016-08-19T09:00:00.000Z",
            "endTime": "2016-08-19T09:00:00.000Z"
          },
          "value": 
          {
            "int64Value": "100"
          }
        }
      ]
    }
  ]
}
```

# Read Metrics

```
stackc -p [PROJECT_NAME] read -f [FILTER STRING HERE] --start-time [START TIME] --end-time [END TIME] 
```

The previous codeblock will read a metric of your specified filter between the time ranges set. If no start and end time are set it will default to the last 10 minutes.

**Metrics List:** [https://cloud.google.com/monitoring/api/metrics]()

**Filter Docs:** [https://cloud.google.com/monitoring/custom-metrics/reading-metrics#time_series_filters]()

-------

Built under the [ISC](http://opensource.org/licenses/ISC) License
