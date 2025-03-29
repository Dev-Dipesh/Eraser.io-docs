# Entity Relationship Diagram - Syntax

Entities
-------------------------

Entities correspond to database tables or similar. Entities contain attributes.

Entity definitions consist of a name followed by `{ }`. For example, `users` is the name of the below entity and it contains attributes `id` and `displayName`.

`users { id string displayName string }`

![](https://files.readme.io/5f7c92b-image.png)  

It is possible for entities to contain nothing like the below.

`users { }`

![](https://files.readme.io/2f9153e-image.png)

Entity names are required to be unique.

Attributes
-----------------------------

Attributes correspond to database table columns or similar.

Attribute definitions occur within an entity definition. They consist of a `name`, `type` (optional), and `metadata` (optional) delimited by the space character. Here is an example:

`users { id string pk }`

![](https://files.readme.io/167bdc2-image.png)

Outside of a definition (e.g. in a relationship statement), attributes are referred to following the entity that they belong to, separated by a `.`. Here is an example:

`users.teamId > teams.id`

![](https://files.readme.io/63e0662-image.png)

It is possible to define an attribute and create a relationship in the same line by using a relationship statement directly inside the table definition. Here is an example:

`users { teamId < teams.id }`

![](https://files.readme.io/2950e6a-image.png)

Properties
-----------------------------

Properties are key-value pairs enclosed in `[ ]` brackets that can be appended to entity definitions. Properties are optional.

It is possible to set multiple properties like shown below:

`users [icon: user, color: blue] { teamId < teams.id }`

![](https://files.readme.io/8e957c8-image.png)  

Here are the properties that are allowed:

|Property|Description|Value|Default value|
|---|---|---|---|
|`icon`|Attached icons|Icon names (e.g. `aws-ec2`).||
|`color`|Stroke and fill color, when possible|Color name (e.g. `blue`) or hex code (e.g. `#000000`)|
|`colorMode`|Fill color lightness|`pastel`, `bold`, `outline`|`pastel`|
|`styleMode`|Embellishments|`shadow`, `plain`, `watercolor`|`shadow`|
|`typeface`|Text typeface|`rough`, `clean`, `mono`|`rough`|

Here are the lists of icon names:

*   General Icons
*   Tech Logos
*   AWS Icons
*   Google Cloud Icons
*   Azure Icons

Refer to [Styling](/docs/styling) for more details and examples on the `colorMode`, `styleMode`, and `typeface` properties.

Relationships

[](#relationships)
-----------------------------------

Relationships show the attribute-level relations between entities.

Here is an example:

`users.teamId > teams.id`

![](https://files.readme.io/4d44cf6-image.png)

It is possible to show omit the attribute-level and simply show entity-level relations like this:

`users > teams`

![](https://files.readme.io/107892f-image.png)

The type of connecting line represents the cardinality between the two entities. Here are the types:

| Syntax | Description |
|---|---|
|`<`|One-to-many|
|`>`|Many-to-one|
|`-`|One-to-one|
|`<>`|Many-to-many|

If a relationship statement contains a name that has not been previously defined as an entity or attribute, an entity or attribute with that name will be created.

Here are the properties that are allowed on relationships (lines):

| Property | Description | Example |
|---|---|---|
| `color` |Line color|`users.teamId > teams.id [color: green]`|

Escape string
-----------------------------------

Certain reserved characters are not allowed in entity or attribute names. However, you can still use these characters by wrapping the entire entity or attribute name in quotes `" "`.

`"CI/CD" [icon: gear] {     id string pk }`
