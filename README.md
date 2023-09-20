# Task 1: Java REST API Example

This project demonstrates the implementation of a Java-based REST API for managing "server" objects. It includes endpoints for searching, creating, updating, and deleting server objects. The server objects are stored in a MongoDB database.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Running the Application](#running-the-application)
- [Endpoints](#endpoints)
  - [GET /servers](#get-servers)
  - [GET /servers/{id}](#get-serversid)
  - [GET /servers/searchname](#get-serverssearchname)
  - [POST /servers/create](#post-serverscreate)
  - [PUT /servers/{id}](#put-serversid)
  - [DELETE /servers/{id}](#delete-serversid)
- [Environment Configuration](#environment-configuration)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

Before you begin, ensure you have met the following requirements:

- Java Development Kit (JDK) installed (Java 8 or later).
- Apache Maven for building the application.
- MongoDB installed and running locally or at a specified host.
- Postman, cURL, or any other HTTP client for testing the API endpoints.

## Getting Started

Follow these steps to set up and run the Java REST API application:

1. Clone this repository to your local machine:

   ```bash
   git clone gh repo clone sjarunvenkat/mongoserver-REST-API
   ```

2. Navigate to the project directory:

   ```bash
   cd mongoserver-REST-API
   ```

3. Build the project using Maven:

   ```bash
   mvn clean package
   ```

4. Run the application:

   ```bash
   java -jar target/mongoserver-REST-API.jar
   ```
![1](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/ef6b241c-0328-48d4-b641-a93e5a67f73a)

The application should now be running on `http://localhost:6039//servers`.

### Environment Configuration

To configure the MongoDB connection, set the following environment variables:

- `MONGODB_URI`: The MongoDB connection URI, e.g., `"mongodb://localhost:27017/mydb"`.
- `MONGODB_USERNAME` (optional): MongoDB username if authentication is enabled.
- `MONGODB_PASSWORD` (optional): MongoDB password if authentication is enabled.

## Endpoints

### GET /servers
![2](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/926fc14e-b585-43b7-8475-868c72727ccc)

- Description: Retrieve a list of all server objects.
- Request: None required.
- Response: A JSON array containing server objects.
- Example Response:

  ```json
  [
    {
      "id": "123",
      "name": "my centos",
      "language": "java",
      "framework": "django"
    },
    {
      "id": "456",
      "name": "my ubuntu",
      "language": "python",
      "framework": "flask"
    }
  ]
  ```

### GET /servers/{id}
![3](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/884da3c6-bd7f-4150-99c9-1fcc2a1a90e8)

- Description: Retrieve a single server object by its ID.
- Request: Path parameter `id` specifying the server ID.
- Response: A JSON object representing the server or a 404 response if not found.
- Example Request:

  ```
  GET /servers/123
  ```

- Example Response:

  ```json
  {
    "id": "123",
    "name": "my centos",
    "language": "java",
    "framework": "django"
  }
  ```

### GET /servers/searchname
![4](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/89918d6c-4557-464a-a7aa-ade4d7f104f5)

- Description: Search for server objects by name.
- Request: Query parameter `name` specifying the name to search for.
- Response: A JSON array containing matching server objects or a 404 response if none found.
- Example Request:

  ```
  GET /servers/searchname?name=centos
  ```

- Example Response:

  ```json
  [
    {
      "id": "123",
      "name": "my centos",
      "language": "java",
      "framework": "django"
    }
  ]
  ```

### POST /servers/create
![6](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/3f2e0a54-a5fb-489e-8690-f2f100a9efcb)

- Description: Create a new server object.
- Request: JSON-encoded server object in the request body.
- Response: A success message with the created server's name.
- Example Request:

  ```json
  {
    "name": "my ubuntu",
    "language": "python",
    "framework": "flask"
  }
  ```

- Example Response:

  ```
  Server created: my ubuntu
  ```

### PUT /servers/{id}
![5](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/569368ff-2a36-4dde-9f87-dd65609d6ec0)

- Description: Update an existing server object by its ID.
- Request: Path parameter `id` specifying the server ID, and a JSON-encoded server object in the request body.
- Response: The updated server object or a 404 response if the server with the given ID is not found.
- Example Request:

  ```json
  PUT /servers/123
  ```

  ```json
  {
    "name": "my updated centos",
    "language": "java",
    "framework": "spring"
  }
  ```

- Example Response:

  ```json
  {
    "id": "123",
    "name": "my updated centos",
    "language": "java",
    "framework": "spring"
  }
  ```

### DELETE /servers/{id}
![7](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/949dfdb1-98d5-4a95-97f1-9794e0825861)

- Description: Delete a server object by its ID.
- Request: Path parameter `id` specifying the server ID.
- Response: No content (204) if the server is successfully deleted, or a 404 response if the server with the given ID is not found.
- Example Request:

  ```
  DELETE /servers/123
  ```

## Testing

You can use tools like Postman, cURL, or any other HTTP client to test the API endpoints described above.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
