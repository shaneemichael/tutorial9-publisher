# Publisher Questions 
### Name: Shane Michael Tanata Tendy
### NPM: 2306259976
### Class: B

----

### How much data your publisher program will send to the message broker in one run? ####
The program will send 5 separate UserCreatedEventMessage objects to the message broker in one run.

Each message contains:
- `A user_id (String)`
- `A user_name (String)`

The 5 messages sent are:
- `{ user_id: "1", user_name: "129500004y-Amir" }`
- `{ user_id: "2", user_name: "129500004y-Budi" }`
- `{ user_id: "3", user_name: "129500004y-Cica" }`
- `{ user_id: "4", user_name: "129500004y-Dira" }`
- `{ user_id: "5", user_name: "129500004y-Emir" }`

Each message is serialized using Borsh (Binary Object Representation Serializer for Hashing) 
before being sent to the "user_created" queue in the message broker.

### The url of: "amqp://guest:guest@localhost:5672" is the same as in the subscriber program, what does it mean? ####
The identical URL "amqp://guest:guest@localhost:5672" in both the publisher and subscriber 
programs  means they're connecting to the same message broker instance. This is essential for the 
publisher-subscriber pattern to work correctly.

The URL in detail:
1. `amqp://` - The protocol specifier (Advanced Message Queuing Protocol)
2. `guest:guest@` - Authentication credentials:
    - First "guest" - Username
    - Second "guest" - Password
    - These are typically the default credentials for RabbitMQ message brokers
3. `localhost:5672` - Connection target:
    - `localhost` - The server address (in this case, running on the same machine)
    - `5672` - The default port for AMQP connections

By using the same connection parameters, the publisher can send messages to the 
"user_created" queue, and the subscriber can receive those messages from the same queue, 
enabling asynchronous communication between these components.

## RabbitMQ Images ##
![RabbitMQ Run Image](../publisher/rabbit1.jpg)
![Sending Image](../publisher/sending.jpeg)
![RabbitMQ Run2 Image](../publisher/rabbit2.jpeg)
![RabbitMQ Run3 Image](../publisher/rabbit3.jpeg)