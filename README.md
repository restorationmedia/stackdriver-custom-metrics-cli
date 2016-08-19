# StackDriver Custom Metrics CLI

This tool is designed to send custom metrics from any *nix system with an easy to use cli tool - `stackc`

To get started just globally install this package:
```
npm install -g stackdriver-custom-metrics-cli
```

**Note**: You MUST have `gcloud` cli installed and have a default service account activated for this software to work as is.

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

This cli currently only supports creating metrics timeSeries events, however support for other Google Monitoring api features may be added upon request.

-------

Built under the [ISC](http://opensource.org/licenses/ISC) License
