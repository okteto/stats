# Okteto Stats

Prometheus HTTP statistic helper

## Installation

```golang
go get github.com/okteto/stats
```

## HTTP Stats

| name                                 | type      | labels                             |
|--------------------------------------|-----------|------------------------------------|
| http_server_requests_in_flight       | guage     | instance, job                      |
| http_server_requests_total           | counter   | instance, job, code, method, uri |
| http_server_request_duration_seconds | histogram | instance, job, method, uri |


### Stats

### http_server_requests_in_flight
The current number of requests in flight for a given job/service.

### http_server_requests_total
Total number of requests.

### http_server_request_duration_seconds
Request latency histogram. Note that the buckets need to be tuned if more precision is required from the histogram

### Labels

#### instance
Current instance. Added automatically by kube
#### job
The name of the scrape job in the prometheus config. Should be the same as the name of the service. Querying for jobs should provide all the stat of that type for the service. Added automatically.
#### code
The http status code of the response. The instrumentation code must add this label.
#### method
The http method used for the request. The instrumentation code must add this label.
#### uri
This is the actual api used and is added by instrumentation code
