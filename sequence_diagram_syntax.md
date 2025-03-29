Sequence Diagram Syntax
======

Each line in a sequence diagram consists of two **columns** (i.e. entities), an **arrow** (i.e. direction of flow), and a **message**. The two columns are separated by the `>` arrow and the message is prepended with the `:`.

Here is an example:

`Web App > DB: Start transaction`

![](https://files.readme.io/53183e1-image.png)

Here are the types of arrows:

|Syntax|Description|
|---|---|
|`>`|Left-to-right arrow|
|`<`|Right-to-left arrow|
|`<>`|Bi-directional arrow|
|`-`|Line|
|`--`|Dotted line|
|`-->`|Dotted arrow|

Each line is parsed in sequential order from top to bottom and rendered in the diagram the same way.

Column names are required to be unique. If a line refers to a column name that hasn't been used in prior lines, a new column will be created.

Properties
-----------------------------

Properties are key-value pairs enclosed in `[ ]` brackets that can be appended to column names. Properties are optional.

It is possible to set multiple properties like shown below:

`Web App [icon: monitor, color: blue] > DB [icon: database, color: green]: Start transaction` 

![](https://files.readme.io/0376a8a-image.png)

Here are the properties that are allowed on columns:

|Property|Description|Value|Default value|
|---|---|---|---|
|`icon`|Attached icons|Icon names (e.g. `aws-ec2`).|
|`color`|Stroke and fill color|Color name (e.g. `blue`) or hex code (e.g. `#000000`)|
|`label`|Text label|Any string. Enclose in double quotes (e.g. `"Main Server"`) if containing a space. Allows multiple columns to have the same `label`.|
|`colorMode`|Fill color lightness|`pastel`, `bold`, `outline`|`pastel`|
|`styleMode`|Embellishments|`shadow`, `plain`, `watercolor`|`shadow`|
|`typeface`|Text typeface|`rough`, `clean`, `mono`|`rough`|

Here are the lists of icon names:

*   AWS Icons
*   Google Cloud Icons
*   Azure Icons
*   Tech Logos
*   General Icons

The `label` property is useful if you want the column label and name to be distinct. By default, the `label` is set as the column name. But because column names are required to be distinct, you will need to use the `label` property if you have two column with the exact same label.

`// Names need to be distinct, but labels can overlap Server1 [label: server] Server2 [label: server]`

Here are the properties that are allowed on arrows (lines):

|Property|Description|Example|
|---|---|---|
|`color`|Line color|`Web App > DB: Start transaction [color: blue]`  `Web App > DB: [color: blue]`|

Refer to [Styling](/docs/styling) for more details and examples on the `colorMode`, `styleMode`, and `typeface` properties.

Blocks
---------------------

**Blocks** are groupings of messages that represent control flow. They can be used to express loops, if-else logic, parallel processing, and break execution.

Block definitions consist of a block type followed by `{ }`. It can have an optional `label` property. For example, the below `opt` (optional) block has a label `if complete`. The block contains a single message from `Server` to `Client`.

`opt [label: if complete] {  Server > Client: Success }`

![](https://files.readme.io/7e5f5e7-image.png)

There are 5 block types, each representing a type of control flow.

|Type|Description|
|---|---|
|`loop`|Loop|
|`alt` (`else`)|Alternative|
|`opt`|Optional|
|`par`(`and`)|Parallel|
|`break`|Break|

![](https://files.readme.io/2a72b9a-sequence_diagram_blocks.png)

It is possible to create connected blocks in the case of the `alt` (paired with `else`) and `par` (paired with `and`) blocks.

`alt [label: if complete] {  Server > Client: Success } else [label: if failed] {  Server > Client: Failure }`

![](https://files.readme.io/22bc493-image.png)

Here are all the block properties that are allowed:

|Property|Description|Value|
|---|---|---|
|`label`|Add a label to the block|Block label. Can be any string.|
|`icon`|Add an icon to the block label|Icon names (e.g. `aws-ec2`)|
|`color`|Specify a color for the block|Color name (e.g. `blue`) or hex code (e.g. `#000000`)|

Activations
-------------------------------

**Activations** represent the time during which a column (an actor or resource) is actively performing an action.

A pair of `activate` and `deactivate` statements define a single activation. The `activate` and `deactivate` keyword is followed by the column name.

`Client > Server: Data request activate Server Server > Client: Return data deactivate Server`

![](https://files.readme.io/b97e9bc-image.png)

Escape string
-----------------------------------

Certain characters are not allowed in node and group names because they are reserved. You can use these characters, you can wrap the entire node or group name in quotes `" "`.

`User > "https://localhost:8080": GET`
