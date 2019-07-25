1. 添加elastic源
helm repo add elastic https://helm.elastic.co
2. 创建命名空间
kubectl create namespace efk
3. 部署elasticsearch
helm install elastic/elasticsearch  -n efk-es --namespace efk -f elasticsearch/values.yaml
4. 部署kibana
helm install elastic/kibana  -n efk-kibana --namespace efk -f kibana/values.yaml
5. fluentd参考
https://www.qikqiak.com/post/install-efk-stack-on-k8s/#%E9%83%A8%E7%BD%B2-fluentd
给节点打标签
kubectl label nodes docker-desktop  beta.kubernetes.io/fluentd-ds-ready=true
通过
nodeSelector:
  beta.kubernetes.io/fluentd-ds-ready: "true"
来限制启动服务的节点
