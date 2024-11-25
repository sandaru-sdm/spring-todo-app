# ToDoApp

A simple ToDo application built using Spring Boot and Maven, designed to manage tasks efficiently. This project provides a REST API for creating, reading, updating, and deleting tasks.

## Features

- **Task Management**: Add, view, update, and delete tasks.
- **Database Integration**: MySQL is used as the backend database for persistent storage.
- **REST API**: Fully functional API endpoints for task operations.
- **Spring Boot**: Built with Spring Boot for rapid application development.
- **Cross-Platform**: Can be run on any platform with Java and Maven installed.

## Project Structure

```
ToDoApp/
├── src/                # Source code for the application
│   ├── main/
│   │   ├── java/      # Java source files
│   │   └── resources/ # Configuration and properties files
├── pom.xml            # Maven build configuration file
├── todo.sql           # SQL script to set up the MySQL database
├── HELP.md            # Reference documentation
└── README.md          # Project documentation (this file)
```

## Requirements

- **Java**: Version 17 or higher
- **Maven**: Version 3.6 or higher
- **MySQL**: Version 8.0 or higher

## Installation and Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd ToDoApp
```

### 2. Set Up the Database

Open your MySQL client and execute the SQL script provided in todo.sql to create the database:

```sql
CREATE DATABASE todo_app;
USE todo_app;
-- Execute the remaining SQL commands from todo.sql
```

### 3. Configure the Application

Update the database credentials in the `application.properties` file (located in the `src/main/resources/` directory):

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/todo_app
spring.datasource.username=your_username
spring.datasource.password=your_password
```

### 4. Build and Run the Application

Using Maven Wrapper:
```bash
./mvnw spring-boot:run
```

Or Using Maven Directly:
```bash
mvn spring-boot:run
```

The application will start on http://localhost:8080.

## API Documentation

### Base URL
http://localhost:8080

### Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/tasks` | GET | Retrieve all tasks |
| `/api/tasks/{id}` | GET | Retrieve a single task |
| `/api/tasks` | POST | Create a new task |
| `/api/tasks/{id}` | PUT | Update a task |
| `/api/tasks/{id}` | DELETE | Delete a task |

### Example API Usage

#### 1. Get All Tasks

Request:
```bash
GET /api/tasks
```

Response:
```json
[
  {
    "id": 1,
    "title": "Sample Task",
    "description": "This is a sample task.",
    "completed": false
  }
]
```

#### 2. Create a New Task

Request:
```bash
POST /api/tasks
```

Body:
```json
{
  "title": "New Task",
  "description": "Description of the new task"
}
```

Response:
```json
{
  "id": 2,
  "title": "New Task",
  "description": "Description of the new task",
  "completed": false
}
```

#### 3. Update a Task

Request:
```bash
PUT /api/tasks/1
```

Body:
```json
{
  "title": "Updated Task",
  "description": "Updated description",
  "completed": true
}
```

Response:
```json
{
  "id": 1,
  "title": "Updated Task",
  "description": "Updated description",
  "completed": true
}
```

#### 4. Delete a Task

Request:
```bash
DELETE /api/tasks/1
```

Response:
```json
{
  "message": "Task deleted successfully"
}
```

## Development

### Install Dependencies

Run the following command to install all dependencies:

```bash
mvn install
```

### Package the Application

To build the project as a standalone JAR file:

```bash
mvn clean package
```

The JAR file will be generated in the `target/` directory.

## Troubleshooting

### Common Issues:

- **Database connection errors**: Ensure your MySQL server is running and the `application.properties` file contains the correct credentials.

- **Port conflicts**: If 8080 is already in use, change the port in the `application.properties` file:
  ```properties
  server.port=8081
  ```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add your message"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/your-feature-name
   ```
5. Submit a pull request.

## Acknowledgments

- Spring Boot Documentation
- MySQL Documentation
- Maven Documentation

Thank you for using ToDoApp! Happy task managing! 😊
