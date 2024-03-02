# resmonio/kubernetes-event-exporter

## 概要

- K8s Eventをどこかしらに出力するための機能

## Getting Started

### Install
```
kubectl create ns monitoring
kubectl apply -f ./yaml
```

### 確認
```
kubectl logs 
```

## 設定

送信先の一覧

| 送信先          | 補足 |
| --------------- | --- |
| Opsgenie        |     |
| Webhook         |     |
| Elasticsearch   |     |
| OpenSearch      |     |
| Slack           |     |
| Kinesis         |     |
| Firehose        |     |
| SNS             |     |
| SQS             |     |
| File            |     |
| Stdout          |     |
| Kafka           |     |
| OpsCenter       |     |
| Pubsub          |     |
| Teams           |     |
| Syslog          |     |
| BigQuery        |     |
| Pipe            |     |
| AWS EventBridge |     |
| Loki            |     |

## ログフォーマット

いくつかの通知先はログのレイアウトを設定可能

全部出す

```
    receivers:
      - name: "dump"
        stdout: {}
```

```
event-exporter-6d778fb78d-glr2z event-exporter {"metadata":{"name":"event-exporter-6d778fb78d.17b8e2c11220dc04","namespace":"monitoring","uid":"756accaa-7558-49b1-be8c-2f004ace2824","resourceVersion":"1529","creationTimestamp":"2024-03-02T07:42:57Z"},"reason":"SuccessfulCreate","message":"Created pod: event-exporter-6d778fb78d-glr2z","source":{"component":"replicaset-controller"},"firstTimestamp":"2024-03-02T07:42:57Z","lastTimestamp":"2024-03-02T07:42:57Z","count":1,"type":"Normal","eventTime":null,"reportingComponent":"","reportingInstance":"","clusterName":"","involvedObject":{"kind":"ReplicaSet","namespace":"monitoring","name":"event-exporter-6d778fb78d","uid":"d85633d0-6dd3-4240-b164-714aee5c9a63","apiVersion":"apps/v1","resourceVersion":"1074","labels":{"app":"event-exporter","pod-template-hash":"6d778fb78d","version":"v1"},"annotations":{"deployment.kubernetes.io/desired-replicas":"1","deployment.kubernetes.io/max-replicas":"2","deployment.kubernetes.io/revision":"1"},"ownerReferences":[{"apiVersion":"apps/v1","kind":"Deployment","name":"event-exporter","uid":"17b26be7-5667-45eb-b466-77b298b0442b","controller":true,"blockOwnerDeletion":true}],"deleted":false}}
```

メッセージだけ出す
```
    receivers:
      - name: "dump"
        stdout:
          layout:
            message: "{{ .Message }}"
```

```
event-exporter-6d778fb78d-f7jt7 event-exporter {"message":"Created pod: event-exporter-6d778fb78d-f7jt7"}
```

## まとめ

- vmware-archive/eventrouterはもう更新されないのでこっち使う方がよさそう
- robusta-dev/kubewatchも良さそうだけど、あれはstdoutできないかも
  - sinkとかの細かいコントロールはrobusta runnerでやらせたいはず