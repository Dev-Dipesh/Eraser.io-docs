Cloud Architecture Syntax
======

Nodes
-------------------

A node is the most basic building block in a cloud architecture diagram.

Node definitions consist of a name followed by an optional set of properties. For example, `compute` is the name of below node and it has an `icon` property which is set to `aws-ec2`.

`compute [icon: aws-ec2]`

![](https://files.readme.io/2211d42-image.png)

Node names are required to be unique.

Nodes support `icon` and `color` properties.

Groups
---------------------

A group is a container that can encapsulate nodes and groups.

Group definitions consist of a name followed by `{ }`. For example, `Main Server` is the name of the below group and it contains `Server` and `Data` nodes.

  `Main Server {     Server [icon: aws-ec2]     Data [icon: aws-rds]   }`

![](https://files.readme.io/e4e565d-image.png)

Group names are required to be unique.

Groups can be nested. In the below example, `VPC Subnet` group contains `Main Server group`.

`VPC Subnet {   Main Server {     Server [icon: aws-ec2]     Data [icon: aws-rds]   } }`

![](https://files.readme.io/71f3972-image.png)

Groups support `icon` and `color` properties.

Properties
-----------------------------

Properties are key-value pairs enclosed in `[ ]` brackets that can be appended to definitions of nodes and groups. Properties are optional.

It is possible to set multiple properties like shown below:

  `Main Server [icon: aws-ec2, color: blue] {     Server [icon: aws-ec2]     Data [icon: aws-rds]   }`

![](https://files.readme.io/757ac9f-image.png)

Here are the properties that are allowed:

|Property|Description|Value|Default value|
|---|---|---|---|
|`icon`|Attached icons|Icon names (e.g. `aws-ec2`).|
|`color`|Stroke and fill color|Color name (e.g. `blue`) or hex code (e.g. `"#000000"`\- note the quote marks for hex codes)|
|`label`|Text label|Any string. Enclose in double quotes (e.g. `"Main Server"`) if containing a space. Allows multiple nodes and groups to have the same `label`.|Name of node or group|
|`colorMode`|Fill color lightness|`pastel`, `bold`, `outline`|`pastel`|
|`styleMode`|Embellishments|`shadow`, `plain`, `watercolor`|`shadow`|
|`typeface`|Text typeface|`rough`, `clean`, `mono`|`rough`|

Here are the lists of icon names:

*   AWS Icons
*   Google Cloud Icons
*   Azure Icons
*   Tech Logos
*   General Icons

The `label` property is useful if you want the node's (or group's) label and name to be distinct. By default, the `label` is set as the node name. But because node names are required to be distinct, you will need to use the `label` property if you have two nodes with the exact same label.

`// Names need to be distinct, but labels can overlap Server_A [label: server] Server_B [label: server]`

Refer to [Styling](/docs/styling) for more details and examples on the `colorMode`, `styleMode`, and `typeface` properties.

It is possible to set multiple properties by separating them using `,` like shown below:

`Server [icon: server, typeface: mono]`

Connections
-------------------------------

Connections represent relationships between nodes and groups. They can be created between nodes, between groups, and between nodes and groups.

Here is an example of a connection between two nodes:

`Compute > Storage`

![](https://files.readme.io/439a719-image.png)

Here are the types of connectors:

|Syntax|Description|
|---|---|
|`>`|Left-to-right arrow|
|`<`|Right-to-left arrow|
|`<>`|Bi-directional arrow|
|`-`|Line|
|`--`|Dotted line|
|`-->`|Dotted arrow|

It is possible to add a label to a connection. Here is an example:

`Storage > Server: Cache Hit`

![](https://files.readme.io/d547532-Connection_labels.png)

It is possible to create it is possible to create one-to-many connections in a single statement. This is instead of creating separate one-to-one connections. Here is an example:

`Server > Worker1, Worker2, Worker3`

![](https://files.readme.io/cb51434-image.png)

If a connection statement contains a name that has not been previously defined as a node or a group, a blank node with that name will be created.

Here are the properties that are allowed on connections (lines):

|Property|Description|Example|
|---|---|---|
|`color`|Line color|`Storage > Server: Cache Hit [color: green]` `Storage > Server: [color: green]`|

Escape string
-----------------------------------

Certain characters are not allowed in node and group names because they are reserved. You can use these characters, you can wrap the entire node or group name in quotes `" "`.

`User > "https://localhost:8080": GET`
