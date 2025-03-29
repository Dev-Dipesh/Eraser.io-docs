# Eraser Notation Guide ①

Eraser is a documentation and diagram platform for engineering teams. It uses a unique notation to create visually expressive documents. This guide explains Eraser's notation in detail and demonstrates how to use it with various examples.

## Basic Syntax

Eraser's notation uses a concise syntax similar to YAML. The basic syntax is written as follows:

```yaml
// Node definition
NodeName [Attributes] {
  // Subnode definition
  SubNodeName [Attributes]
}

// Relationship definition
Node1 > Node2: [Label]
```

**Explanation:**

* `//` indicates a comment.
* `NodeName` is the name of the element (node) in the diagram.
* `Attributes` specify the shape, color, icon, text, etc., of the node.
* `SubNodeName` is the name of an element nested within a node.
* `Node1 > Node2` indicates a relationship from Node1 to Node2.
* `[Label]` is an optional label to add a description to the relationship.

## Defining Nodes

Nodes represent elements of the diagram. In a node definition, you specify the `NodeName`, `Attributes`, and `Subnodes`.

### Attributes

Node attributes are specified within `[]`. The following attributes can be used:

* `shape`: Specifies the shape of the node.
    * `oval`: Oval
    * `rectangle`: Rectangle
    * `diamond`: Diamond
    * `rounded_rectangle`: Rounded Rectangle
    * `cylinder`: Cylinder
    * `hexagon`: Hexagon
    * `triangle`: Triangle
    * `parallelogram`: Parallelogram
    * `cloud`: Cloud
    * `star`: Star
    * `database`: Database
* `icon`: Specifies the icon displayed on the node.
    * `file-text`: File
    * `bug`: Bug
    * `copy`: Copy
    * `repeat`: Repeat
    * `zap`: Lightning
    * `check-square`: Checkbox
    * `package`: Package
    * `send`: Send
    * `user`: User
    * `users`: Multiple Users
    * `home`: Home
    * `folder`: Folder
    * `message-circle`: Message
    * `mail`: Mail
    * `clock`: Clock
    * `list`: List
    * `key`: Key
    * `grid`: Grid
    * `link`: Link
    * `calendar`: Calendar
    * `oracle`: Oracle
    * `twitter`: Twitter
    * `facebook`: Facebook
    * `aws-api-gateway`: AWS API Gateway
    * `aws-lambda`: AWS Lambda
    * `aws-simple-storage-service`: AWS S3
    * `aws-ec2`: AWS EC2
    * `aws-rds`: AWS RDS
    * `aws-auto-scaling`: AWS Auto Scaling
    * `aws-redshift`: AWS Redshift
    * `kafka`: Kafka
    * `gcp-pubsub`: GCP Pub/Sub
    * `gcp-cloud-logging`: GCP Cloud Logging
    * `gcp-dataflow`: GCP Dataflow
    * `gcp-cloud-storage`: GCP Cloud Storage
    * `gcp-datastore`: GCP Datastore
    * `gcp-bigtable`: GCP Bigtable
    * `gcp-bigquery`: GCP BigQuery
    * `gcp-app-engine`: GCP App Engine
    * `gcp-container-registry`: GCP Container Registry
    * `gcp-compute-engine`: GCP Compute Engine
    * `azure-active-directory`: Azure Active Directory
    * `azure-load-balancers`: Azure Load Balancers
    * `azure-virtual-networks`: Azure Virtual Networks
    * `azure-network-security-groups`: Azure Network Security Groups
    * `azure-virtual-machine`: Azure Virtual Machine
    * `k8s-control-plane`: Kubernetes Control Plane
    * `k8s-api`: Kubernetes API
    * `k8s-sched`: Kubernetes Scheduler
    * `k8s-c-c-m`: Kubernetes Controller Manager
    * `k8s-c-m`: Kubernetes Cloud Controller Manager
    * `k8s-etcd`: Kubernetes etcd
    * `k8s-node`: Kubernetes Node
    * `k8s-kubelet`: Kubernetes Kubelet
    * `k8s-k-proxy`: Kubernetes KProxy
    * `databricks`: Databricks
    * `snowflake`: Snowflake
    * `slack`: Slack
    * `tensorflow`: TensorFlow
    * `tableau`: Tableau
    * `layout`: Web App
    * `database`: Database
    * `function`: Cloud Function
    * `cloud-cog`: Cloud Settings
    * `settings`: Settings
    * `aws`: AWS
    * `google-cloud`: Google Cloud
    * `azure`: Azure
    * `google`: Google
    * `microsoft`: Microsoft
* `color`: Specifies the color of the node.
    * `red`: Red
    * `green`: Green
    * `blue`: Blue
    * `yellow`: Yellow
    * `purple`: Purple
    * `orange`: Orange
    * `grey`: Grey
    * `silver`: Silver
* `text`: Specifies the text displayed on the node.
* `style`: Specifies the style of the node.
    * `dashed`: Dashed
    * `dotted`: Dotted
    * `bold`: Bold
    * `italic`: Italic

### Subnodes

Subnodes represent elements nested within a node. The syntax to define subnodes is similar to that of nodes.

```yaml
# Node definition
NodeName [Attributes] {
  # Subnode definition
  SubNodeName [Attributes]
}
```

Subnodes can be nested across multiple levels.

### Groups

Groups are a feature used to cluster related nodes together. Groups are defined within `{}`. Nodes within a group can specify color with the `[color]` attribute.

```yaml
# Group definition
GroupName [color] {
  # Node definition within group
  NodeName [Attributes]
}
```

## Defining Relationships

Relationships represent connections between nodes. The definition of a relationship uses the syntax `Node1 > Node2`.

### Labels

Labels for relationships are specified after `:`. They are used to add descriptions or annotations to the relationship.

```yaml
# Relationship definition
Node1 > Node2: [Label]
```

### Types of Relationships

In Eraser, the following types of relationships can be used:

* `>`: Directed relationship (from Node1 to Node2)
* `<`: Directed relationship (from Node2 to Node1)
* `<>`: Bidirectional relationship (between Node1 and Node2)

## Examples

### Issue Triage Flow

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717593719913.png)

```yaml
# Nodes and Groups
Issue type? [shape: oval, icon: file-text]

BugPath [color: red] {
  Bug [icon: bug, color: red]
  Duplicate? [shape: diamond, icon: copy]
  Mark duplicate [shape: oval, icon: copy]
  Has repro? [shape: diamond, icon: repeat]
  Ask for repro [shape: oval, icon: repeat]
}

FeaturePath [color: green] {
  Feature [icon: zap, color: green]
  Well specced? [shape: diamond, icon: check-square]
  Can be package? [shape: diamond, icon: package]
  Define as package [shape: oval, icon: package]
}

Issue ready to claim [shape: oval, icon: send]

# Relationships
Issue type? > Bug
Bug > Duplicate?
Duplicate? > Mark duplicate: Yes
Duplicate? > Has repro?: No
Has repro? > Issue ready to claim: Yes
Has repro? > Ask for repro: No
Issue type? > Feature
Feature > Can be package?
Can be package? > Well specced?: No
Can be package? > Define as package: Yes
Well specced? > Issue ready to claim: Yes
```

### Price Lookup Flow

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717593739001.png)

```yaml
# Define nodes and relationships "A > B"
Start [shape: oval, icon: flag] > Read keywords from Excel [icon: excel]
Read keywords from Excel > Establish Amazon API connection [icon: amazon]
Establish Amazon API connection > Wait for user input [shape: diamond, icon: user]
Wait for user input > Search for keyword on Amazon[icon: search]: User selects keyword
Search for keyword on Amazon > Retrieve item price [icon: dollar-sign] 
Retrieve item price > Output result to Excel [icon: excel] 
Output result to Excel > End
Wait for user input > Close modal [icon: x]: User clicks cancel
Close modal > End [shape: oval, icon: check]

# Define group
For each keyword in the list [icon: repeat] {
  Search for keyword on Amazon
  Retrieve item price 
  Output result to Excel
}
```

## Summary

Eraser's notation is designed to create documents that are visually expressive. Its simple syntax, rich attributes, and various types of relationships allow for the easy creation of diverse diagrams. Use this guide to effectively utilize Eraser's notation to create more effective documents.

## Reference Site

https://docs.eraser.io/docs/what-is-eraser