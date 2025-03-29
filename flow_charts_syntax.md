# Flow Charts - Syntax

Nodes
-------------------

A node is the most basic building block in a flow chart.

Node definitions consist of a name followed by an optional set of properties. For example, `Start` is the name of below node and it has an `shape` property which is set to `oval`.

`Start [shape: oval]`

![](https://files.readme.io/48546b3-image.png)

Node names are required to be unique.

Nodes support `shape`, `icon`, `color`, and `label` properties. More on properties below.

Groups
---------------------

A group is a container that can encapsulate nodes and groups.

Group definitions consist of a name followed by `{ }`. For example, `Loop` is the name of the below group and it contains `Issue1`, `Issue2`, and `Issue3` nodes.

`Loop {   Issue1, Issue2, Issue3 }`

![](https://files.readme.io/26a8a15-image.png)

Nodes (or groups) inside a group can be enumerated either with `,` or new lines as separators. Below results in the same but uses new lines to separate each node.

`Loop {   Issue1   Issue2   Issue3 }`

Group names are required to be unique.

Groups can be nested. In the below example, the `Outer Loop` group contains the `Inner Loop` group.

`Outer Loop { 	Inner Loop { 		Issue1 		Issue2     	} 	Issue3 }`

![](https://files.readme.io/110a93b-image.png)

Groups support `icon`, `color`, and `label` properties.

Properties
-----------------------------

Properties are key-value pairs enclosed in `[ ]` brackets that can be appended to definitions of nodes and groups. Properties are optional.

Here are the properties that are allowed:

|Property|Description|Value|Default Value|
|---|---|---|---|
|`shape`|Shape of node|Shape names (e.g. `diamond` or `oval`).|`rectangle`|
|`icon`|Icon|Icon names (e.g. `aws-ec2`).|
|`color`|Stroke and fill color|Color name (e.g. `blue`) or hex code (e.g. `"#000000"`\- note: must be wrapped in quotes)|
|`label`|Text label|Any string. Enclose in double quotes (e.g. `"Main Server"`) if containing a space. Allows multiple nodes and groups to have the same `label`.|Name of node or group|
|`colorMode`|Fill color lightness|`pastel`, `bold`, `outline`|`pastel`|
|`styleMode`|Embellishments|`shadow`, `plain`, `watercolor`|`shadow`|
|`typeface`|Text typeface|`rough`, `clean`, `mono`|`rough`|

Here is the list of shapes:

*   `rectangle` (default), `cylinder`, `diamond`, `document`, `ellipse`, `hexagon`, `oval`, `parallelogram`, `star`, `trapezoid`, `triangle`

Here are the lists of icon names:

*   AWS Icons
*   Google Cloud Icons
*   Azure Icons
*   Tech Logos
*   General Icons

The `label` property is useful if you want the node's (or group's) label and name to be distinct. By default, the `label` is set as the node name. But because node names are required to be distinct, you will need to use the `label` property if you have two nodes with the exact same label.

`// Names need to be distinct, but labels can overlap Start_A [label: start] Start_B [label: start]`

Refer to [Styling](/docs/styling) for more details and examples on the `colorMode`, `styleMode`, and `typeface` properties.

It is possible to set multiple properties by separating them using `,` like shown below:

`Start [shape: oval, icon: flag]`

Connections
-------------------------------

Connections represent relationships between nodes and groups. They can be created between nodes, between groups, and between nodes and groups.

Here is an example of a connection between two nodes:

`Issue > Bug`

![](https://files.readme.io/3eeeac3-image.png)

Here are the types of connectors:

| Syntax |Description|
|---|---|
|`>`|Left-to-right arrow|
|`<`|Right-to-left arrow|
|`<>`|Bi-directional arrow|
|`-`|Line|
|`--`|Dotted line|
|`-->`|Dotted arrow|

### 

Connection label

[](#connection-label)

It is possible to add a label to a connection. Here is an example:

`Issue > Bug: Triage`

![](https://files.readme.io/9a1104f-Relationship_labels.png)

### 

Branching connections

[](#branching-connections)

It is possible to create it is possible to create one-to-many connections in a single statement. Here is an example:

`Issue > Bug, Feature`

![](https://files.readme.io/0896972-image.png)

### 

Chained connections

[](#chained-connections)

It is also possible to "chain" a sequence of connection statements in a single statement

`Issue > Bug > Duplicate?`

![](https://files.readme.io/19d4eb8-image.png)

If a connection statement contains a name that has not been previously defined as a node or a group, a blank node with that name will be created.

### Connection properties

Here are the properties that are allowed on connections (lines):

|Property|Description|Example|
|---|---|---|
|`color`|Line color|`Issue > Bug: Triage [color: green]`  `Issue > Bug: [color: green]`|


Escape string
-----------------------------------

Certain characters are not allowed in node and group names because they are reserved. You can use these characters, you can wrap the entire node or group name in quotes `" "`.

`User > "https://localhost:8080": GET`

Direction
---------------------------

The direction of the flow chart can be changed using the `direction` statement. Allowed directions are:

*   `direction down` (default)
*   `direction up`
*   `direction right`
*   `direction left`

The direction statement can be placed anywhere in the code like this:

`direction right`

![`direction right` has been applied to the flow chart](https://files.readme.io/c324846c63b87f7837f0c62e8414d58325a849c840a7d04f136d84ebdaf8c794-diagram-export-11-4-2024-9_33_26-AM.png)
