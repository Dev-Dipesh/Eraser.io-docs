# Eraser Notation Guide②

## Entity-Relationship Diagram (ERD)

Eraser also provides notation for creating Entity-Relationship Diagrams (ERD). An ERD is a diagram used to visually represent the structure of a database.

### ERD Notation

ERD notation is similar to regular diagram notation, but uses some special attributes and relationship types to represent entities and relationships.

* **Entity**:
    * `[icon: user, color: blue]`: Specifies the icon and color of the entity.
    * `{ ... }`: Describes the attributes of the entity.
    * `id string pk`: Specifies the attribute which is the primary key.
* **Relationship**:
    * `>`: One-to-one relationship
    * `<>`: One-to-many relationship
    * `<>*`: Many-to-many relationship

### ERD Example

#### ERD of an RPG Game

<blockquote class="twitter-tweet" data-media-max-width="800"><p lang="ja" dir="ltr">Eraser Notation Guide② ~Entity-Relationship Diagram~<br>《ERD of an RPG Game》<br>Created with a fairly random prompt, but it might be quite good! (Created with Gemini 1.5 Flash) <a href="https://t.co/vHXlOwkY4B">https://t.co/vHXlOwkY4B</a> <a href="https://t.co/Y57LYjOohA">pic.twitter.com/Y57LYjOohA</a></p>&mdash; Maki@Sunwood AI Labs. (@hAru_mAki_ch) <a href="https://twitter.com/hAru_mAki_ch/status/1798352736771363239?ref_src=twsrc%5Etfw">June 5, 2024</a></blockquote>

```yaml
// 1. users: The heroes who adventure in this world!
users [icon: user, color: blue] {
  id string pk
  displayName string
  level int
  experience int
  gold int
  currentLocation string
}

// 2. teams: Companions that help heroes advance their adventures.
teams [icon: users, color: blue] {
  id string pk
  name string
  leaderId string
}

// 3. characters: Unique companions controlled by the heroes!
characters [icon: warrior, color: green] {
  id string pk
  name string
  level int
  stats json 
  skills json
  userId string
}

// 4. items: Tools and weapons helpful for the adventure!
items [icon: sword, color: orange] {
  id string pk
  name string
  type string
  rarity string
  stats json
}

// 5. quests: Trials imposed on the heroes!
quests [icon: quest, color: purple] {
  id string pk
  name string
  description string
  reward json 
  status string
}

// 6. enemies: Strong adversaries that hinder heroes' adventures!
enemies [icon: monster, color: red] {
  id string pk
  name string
  level int
  stats json
  skills json
  location string
}

// 7. locations: Fields and dungeons where heroes adventure.
locations [icon: map, color: grey] {
  id string pk
  name string
  description string
  enemies json
  items json
}

// Entity Relationships

users.teams <> teams.id // Heroes can belong to multiple teams, and a single team can have multiple heroes.
characters.userId > users.id // Characters are owned by heroes.
items.userId > users.id // Items are possessed by heroes.
quests.userId > users.id // Quests are undertaken by heroes.
enemies.location > locations.id // Enemies appear at specific locations.
```

#### ERD for a Dream Fulfillment! Event Reservation App

<blockquote class="twitter-tweet" data-media-max-width="800"><p lang="ja" dir="ltr">Eraser Notation Guide② ~Entity-Relationship Diagram~ <br>《Dream Fulfillment! Event Reservation App's ERD》 <br>This is just a regular calendar reservation app...<br>（Created with Gemini 1.5 Flash） <a href="https://t.co/JfnI8QxWAC">https://t.co/JfnI8QxWAC</a> <a href="https://t.co/KwGYyBfNzY">pic.twitter.com/KwGYyBfNzY</a></p>&mdash; Maki@Sunwood AI Labs. (@hAru_mAki_ch) <a href="https://twitter.com/hAru_mAki_ch/status/1798353579864101032?ref_src=twsrc%5Etfw">June 5, 2024</a></blockquote>

```yaml
// 1. Users: People who book events to fulfill their dreams
User [icon: user] {
  id Int pk
  username String
  email String
  avatar String
  createdDate DateTime
  favoriteEventType Int
}

// 2. Bookings: Event reservations to fulfill dreams
Booking [icon: clock] {
  id Int pk
  userId Int
  title String
  startTime DateTime
  endTime DateTime
  location String
  eventTypeId Int
  destinationCalendarId Int
  status String // Booking status (pending, confirmed, canceled)
  notes String
}

// 3. EventTypes: Various events to fulfill dreams
EventType [icon: list] {
  id Int pk
  name String
  description String
  duration Int
  defaultLocation String // Default venue
  price Decimal // Price
  imageUrl String // Event image URL
  userId Int // Event creator
}

// 4. ApiKeys: Keys for system integration
ApiKey [icon: key] {
  id String pk
  userId Int
  appId String
  hashedKey String
}

// 5. Apps: Applications for system integration
App [icon: grid] {
  slug String
  dirName String
  keys Json
  createdAt DateTime
}

// 6. Webhooks: Magical messages for system integration
Webhook [icon: link] {
  id String pk
  userId Int
  appId String
  active Boolean
  eventTrigger String // Trigger events (booking_created, booking_updated, etc.)
  url String // Notification URL
}

// 7. DestinationCalendars: Calendars fulfilling dreams
DestinationCalender [icon: calendar] {
  id Int pk
  userId Int
  integration String // Integration service (Google Calendar, Outlook Calendar, etc.)
  eventTypeId Int 
}

// Entity Relationships

Booking.eventtType < EventType.id // Bookings are linked to event types.
Webhook.appId > App.slug // Webhooks are linked to apps.
Webhook.userId > User.id // Webhooks are created by users.
App.slug > ApiKey.appId // Apps have API keys.
User.id < Booking.userId // Bookings are made by users.
EventType.userId <> User.id // Event types are created by users.
User.id > ApiKey.userId // Users possess API keys.
DestinationCalender.id > Booking.destinationCalendarId // Bookings are registered with destination calendars.
DestinationCalender.userId < User.id // Destination calendars are set by users.
DestinationCalender.eventTypeId < EventType.id // Destination calendars are linked to event types.
```

## Sequence Diagram

A sequence diagram is a type of diagram for visually representing the behavior of systems or software over a timeline. Eraser provides notation for creating sequence diagrams as well.

### Sequence Diagram Notation

Sequence diagram notation is similar to regular diagram notation, but uses some special attributes and relationship types to represent objects and messages.

* **Object**:
    * `[icon: layout]`: Specifies the icon of the object.
* **Message**:
    * `>`: Message from one object to another
    * `activate`: Activates an object
    * `deactivate`: Deactivates an object
    * `alt [label]:`: Conditional branch
    * `else [label]:`: The else part of a conditional branch
    * `loop [label]:`: Loop

### Sequence Diagram Example

```yaml
Web App [icon: layout] > DB [icon: database]: Start transaction
Web App > Cloud Fx [icon: function]: Call function
Cloud Fx > API [icon: cloud-cog]: Create session
API > Cloud Fx: Session info
Cloud Fx > DB: Create tx record
Cloud Fx > API: Request access token
API > Cloud Fx: Access token
Cloud Fx > Web App: Token and transaction info
Web App > API: Complete transaction
alt [label: If successful]{
  API > Web App: Transaction confirmation
}
else [label: If failed]{
  API > Web App: Transaction cancellation
}
Web App > DB: Create tx record
Web App > API: Subscribe to transaction changes
activate API 
API > API: Ongoing events
API > Web App: Push events
deactivate API
```

## Conclusion

Eraser's notation allows for the creation of various types of diagrams by combining simple syntax with a rich set of attributes and relationship types. Use the ERD and sequence diagram notations introduced in this guide to create more effective documentation.

## Reference Sites

https://docs.eraser.io/docs/examples-1

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>