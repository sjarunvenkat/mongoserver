# Task 2: Generating a Java REST API with Swagger Codegen

This project demonstrates the generation of a Java-based REST API using Swagger Codegen and Spring Boot. The API provides endpoints for managing "server" objects, including searching, creating, updating, and deleting server objects. The server objects are stored in a MongoDB database.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Running the Generated Application](#running-the-generated-application)
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
- Ensure the following dependency is added to your project's `pom.xml` file to enable Swagger documentation:

```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.2.0</version>
</dependency>
```


## Getting Started

Follow these steps to set up and run the generated Java REST API application:

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
![1](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/e490f04f-eea4-4199-89cb-72148ffc0ed9)

The application should now be running on `http://localhost:6039/swagger-ui/index.html#/`.
![2 2](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/6fe27c74-ba9d-4b03-acb9-9115d8e30e01)

### Environment Configuration

To configure the MongoDB connection, set the following environment variables:

- `MONGODB_URI`: The MongoDB connection URI, e.g., `"mongodb://localhost:27017/mydb"`.
- `MONGODB_USERNAME` (optional): MongoDB username if authentication is enabled.
- `MONGODB_PASSWORD` (optional): MongoDB password if authentication is enabled.

## Endpoints

### GET /servers
![2 3](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/3e396461-d47d-4cbe-a12b-a4f58989fddb)

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
![2 4](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/39ea6a0a-19d8-4e89-b326-09dbaa0d8647)

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
![2 5 (1)](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/29a3b449-cecf-4343-8009-59b59ca3d1a4)

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
![2 6](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/9b7dc15a-b4ca-4511-8132-0c9f99dce93b)

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
![2 7](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/6a0c8960-f068-4c8c-8bfd-abb5b0e6ce6c)

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
![2 8](https://github.com/sjarunvenkat/mongoserver-REST-API/assets/73863663/94ad7c0f-be46-4afe-a1aa-3b85007cf781)

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

---

Feel free to adapt and expand this README file as needed for your specific project. Include detailed instructions, dependencies, and any other information that helps users understand and use your Java REST API application generated with Swagger Codegen effectively.
