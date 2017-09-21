# Elasticsearch

[Elasticsearch](https://www.elastic.co/products/elasticsearch) ElasticSearch是一个基于Lucene的搜索服务器。

## TL;DR;

```bash
$ helm install stable/rabbitmq-cluster
```

## 介绍

该应用模板会使用 [Helm](https://helm.sh) 包管理工具在 [Kubernetes](http://kubernetes.io) 上启动一个 [Elasticsearch](https://www.elastic.co/products/elasticsearch) 集群.

## 安装要求

- Kubernetes 1.4+ 支持 Beta APIs
- 集群内部满足供给相应PV

## 安装应用



通过应用名来安装应用 `my-release`:

```bash
$ helm install --name my-release stable/elasticsearch-cluster
```

该命令会部署一个默认配置的Elasticsearch集群.  [configuration](#configuration) 配置目录列出了所有安装期间可使用的的参数.

> **Tip**: 查看所有release请使用 helm list

## 卸载应用

卸载/删除 `my-release` :

```bash
$ helm delete my-release
```

该命令会移除所有与之相关的Kubernetes组件,并删除release.

## 配置参数

下面的表格列出了RabbitMQ可配置的参数和参数的默认值.

|         Parameter          |                       Description                       |                         Default                          |
|----------------------------|---------------------------------------------------------|----------------------------------------------------------|
| `image.image`               | Elasticsearch cluster image                                  | `kayrus/docker-elasticsearch-kubernetes:2.4.4`                             |
| `image.pullPolicy`         | Image pull policy                                       | `IfNotPresent`                                                  |
| `esMaster.replicas`                 | Master replicas number                                | `3`                                                      |
| `esClient.replicas`                 | Client replicas number                                | `2`                                                      |
| `esData.replicas`                 | Data replicas number                                | `2`                                                      |

使用 `--set key=value[,key=value]` 指定各个参数, 在 `helm install` 时使用. 例如,

```bash
$ helm install --name my-release \
  --set namespace=default \
    stable/elasticsearch-cluster
```

或者, 可以在安装阶段使用YAML文件来指定参数. 例如,

```bash
$ helm install --name my-release -f values.yaml stable/elasticsearch-cluster
```
如需修改上面参数,请参照( 以下为默认参数 ):

```
{
    "name": "elasticsearch-cluster-example",
    "namespace": "elasticsearch-cluster",
    "repo": "dcos",
    "chart": "elasticsearch-cluster",
    "version": "latest",
    "values": {
        "image": {
          "name": "kayrus/docker-elasticsearch-kubernetes:2.4.4",
          "pullPolicy": "IfNotPresent"
        },
        "esMaster.replicas": 3,
        "esClient.replicas": 2,
        "esData.replicas": 2
    }  
}

```
