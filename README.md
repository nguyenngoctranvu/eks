# EKS
Elasticsearch Kibana Filebeat Kubernetes

## Information
```
elastic version: 7.0.1
kibana version: 7.0.1
filebeat version: 7.3.2
```

## Install elastic with namespace logging
```
helm upgrade -i elastic elastic -n logging 
```
## Install kibana with namespace logging
```
helm upgrade -i kibana kibana -n logging 
```
## Install filebeat with namespace logging
```
helm upgrade -i filebeat filebeat -n logging 
```

## Enabling security
In order to enable security it is necessary to have either a Gold or Platinum subscription, or a trial license enabled via Kibana or API. For example, the following command would enable a trial license via the API:
```
curl -X POST "localhost:9200/_xpack/license/start_trial?acknowledge=true"
```

## Define built-in user’s passwords
We must now define passwords for the built-in users as described in Setting built-in user passwords. If we are running with a Gold or Platinum license, the previous steps to enable TLS/SSL for the transport communications must be executed before the cluster will start. Additionally, defining built-in user’s passwords should be completed before we enable TLS/SSL for http communications, as the command to set passwords will communicate with the cluster via unsecured http.

Built-in users passwords can be setup with the following command:


```
bin/elasticsearch-setup-passwords interactive
```

## Reference
Setup authentication elasticsearch
```
https://www.elastic.co/blog/elasticsearch-security-configure-tls-ssl-pki-authentication
```
Filebeat example
```
https://github.com/elastic/beats/blob/master/deploy/kubernetes/filebeat-kubernetes.yaml
```
Cert-manager get free ssl
```
https://cert-manager.io/
```

