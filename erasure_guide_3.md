# EraserAI Code Explanation - Practical Use Cases

EraserAI is a very handy tool that generates visual diagrams from natural language or code snippets! In this explanation, we'll walk through how to create easy-to-understand diagrams using EraserAI, in a way that's easy for beginners to grasp.

## Cloud Architecture (AWS Visualization)

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717869470895.png)

```eraser
// Let's represent a simple data pipeline in AWS
// [icon: aws-s3] specifies an icon representing AWS S3 service
Data Source [icon: aws-s3] > Data Processing [icon: aws-emr] > Data Destination [icon: aws-redshift] 

// Visually represent the flow from data source to data processing to data destination
// ">" is an arrow indicating how data moves
```

* **Explanation:** We depicted a simple data pipeline where data is processed with EMR after coming from S3 and is finally loaded into Redshift.
* **Points:**
    * By using the `icon` attribute to attach icons representing AWS services, the diagram becomes easier to understand.
    * By using connectors (`>`), you can visually demonstrate how the data moves.

## Sequence Diagram (Viewing API Request Movement Step by Step)

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717869530345.png)

```eraser
// Let's visualize the sequence of API requests from client to server
Client [icon: user] > Server [icon: server]: Send API request
// "activate Server" indicates that the server is active
activate Server
// The server sends a query to the database
Server > Database [icon: database]: Database query
// The database returns query results to the server
Database > Server: Query results
// The server sends a response to the client
Server > Client [icon: user]: Send response
// "deactivate Server" indicates that the server has finished processing
deactivate Server
```

* **Explanation:** We depicted the flow where the client sends an API request to the server, the server retrieves data from the database, and returns the result to the client.
* **Points:**
    * By using `activate` / `deactivate` keywords, it's easy to indicate when the server is active.
    * By detailing explicit messages (`:`) at each step, you can easily track the flow of processing.

## ERD (Drawing a Database Design Diagram)

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717869622938.png)

```eraser
// Let's represent an ERD that shows the relationship between users and teams
users [icon: user] {
    // id is the primary key, and its type is string
    id string pk
    // name is the user's name, also a string
    name string
    // email is the user's email address, also a string
    email string
}

// Define the team entity
teams [icon: users] {
    // id is the primary key, and its type is string
    id string pk
    // name is the team's name, also a string
    name string
}

// There is a one-to-many relationship between users and teams
// A user belongs to one team and a team can have multiple users
users.teamId > teams.id
```

* **Explanation:** We represented the entities of users and teams and their relationship.
* **Points:**
    * The `pk` attribute indicates a primary key.
    * A connector (`>`) indicates a one-to-many relationship.

## Flowchart (Visualizing Process Flow)

![file](https://hamaruki.com/wp-content/uploads/2024/06/image-1717869683456.png)

```eraser
// A flowchart that takes user input, processes data, and outputs results
Start [shape: oval] > Get User Input [shape: diamond]
// A diamond indicates a conditional branch
Get User Input > Process Data [shape: rectangle]: Yes
// A rectangle indicates a process
Process Data > Output Result [shape: rectangle]
Get User Input > Exit [shape: oval]: No
```

* **Explanation:** We created a simple flowchart that takes user input, processes it, and outputs the results.
* **Points:**
    * By using the `shape` attribute, you can specify the shapes (oval, diamond, rectangle) representing each step.
    * By using connectors (`>`), you can effectively represent the flow of processing.

### FLowchart - Issue Triage Flow Example

```eraser
// Nodes and groups
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

// Relationships
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

![file](https://files.readme.io/2ec2d41-image.png)

### Flowchart - Price Lookup Flow Example

```eraser
// Define nodes and relationships "A > B"
Start [shape: oval, icon: flag] > Read keywords from Excel [icon: excel]
Read keywords from Excel > Establish Amazon API connection [icon: amazon]
Establish Amazon API connection > Wait for user input [shape: diamond, icon: user]
Wait for user input > Search for keyword on Amazon[icon: search]: User selects keyword
Search for keyword on Amazon > Retrieve item price [icon: dollar-sign] 
Retrieve item price > Output result to Excel [icon: excel] 
Output result to Excel > End
Wait for user input > Close modal [icon: x]: User clicks cancel
Close modal > End [shape: oval, icon: check]

// Define Groups
For each keyword in the list [icon: repeat] {
  Search for keyword on Amazon
  Retrieve item price 
  Output result to Excel
}
```

![file](https://files.readme.io/0ef5e94-image.png)

## Conclusion

By simplifying the generation and sharing of diagrams, EraserAI aids in smooth communication and collaboration within teams. Try applying these code examples in various scenarios to work more efficiently with EraserAI.

**For more detailed information, please refer to the official EraserAI documentation.**

https://docs.eraser.io/docs/what-is-eraser

**Good luck!**