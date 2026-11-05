# Day 3 – REST API Development (GET & POST)

## 1. What is an API?

API stands for **Application Programming Interface**.

It allows two software applications to communicate with each other.

In our Movie Ticket Booking project:
- The client sends a request to the backend.
- The backend processes the request.
- The backend sends a response to the client.

Example: When a user requests movie details, the frontend sends a request to the backend API.

## 2. What is a REST API?

REST stands for **Representational State Transfer**.

A REST API allows clients and servers to communicate over HTTP using methods such as GET, POST, PUT and DELETE.

We have practised two HTTP methods:

| Method | Purpose |
|---|---|
| GET | Retrieve data |
| POST | Send data to the server |

## 3. Creating a REST Controller

We created `HelloController.java` inside the `controller` package.

### @RestController

- It is a Spring annotation used to create REST controllers.
- It tells Spring that this class will handle HTTP requests.
- The return value of a method is sent directly in the HTTP response body.

Example:

```java
@RestController
public class HelloController {
}
```

## 4. GET API

GET is an HTTP method used to retrieve data from the server.

We created the following endpoint:

```java
@GetMapping("/hello")
public String sayHello() {
    return "Hello! Movie Ticket Booking API is working.";
}
```

**Explanation:**
- `@GetMapping` maps an HTTP GET request to a method.
- `/hello` is the endpoint URL.
- `sayHello()` is the method that handles the request.
- The returned String becomes the response.

Endpoint:

`GET http://localhost:8080/hello`

Response:

```text
Hello! Movie Ticket Booking API is working.
```

## 5. DTO (Data Transfer Object)

DTO stands for **Data Transfer Object**.

A DTO is used to transfer data between the client and the backend.

We created a separate `dto` package and added a class named `MovieRequest`.

```java
public class MovieRequest {

    private String title;

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }
}
```

**Explanation:**
- `private String title` stores the movie title.
- `getTitle()` retrieves the title.
- `setTitle()` sets the title.

## 6. POST API

POST is an HTTP method used to send data to the server.

We created the following endpoint:

```java
@PostMapping("/movies")
public String addMovie(@RequestBody MovieRequest movieRequest) {
    return "Movie added: " + movieRequest.getTitle();
}
```

### Important annotations

**@PostMapping**
- Maps an HTTP POST request to a controller method.
- Here, `/movies` is the endpoint.

**@RequestBody**
- Reads the incoming request body.
- Converts JSON data into a Java object.
- Spring uses this object to provide data to the controller method.

### Request JSON

```json
{
    "title": "Interstellar"
}
```

### Response

```text
Movie added: Interstellar
```

**Important:** At this stage, the movie is only received and used to generate a response. It is NOT saved in the MySQL database yet.

## 7. Testing APIs using Postman

Postman is a tool used to send HTTP requests and test APIs.

We tested our POST API using these steps:

1. Open Postman and create a new HTTP request.
2. Select the POST method.
3. Enter the URL:

   `http://localhost:8080/movies`

4. Open the Body tab.
5. Select raw and choose JSON.
6. Enter the JSON request body.
7. Click Send.
8. Check the response.

Expected response:

`Movie added: Interstellar`

## 8. Spring Security Configuration

We created `SecurityConfig.java` to configure access to our endpoints.

Important configuration:

```java
.requestMatchers("/hello", "/movies").permitAll()
.anyRequest().authenticated()
```

**Explanation:**
- `permitAll()` allows requests to the specified endpoints without authentication.
- `authenticated()` requires authentication for other endpoints.

We also enabled HTTP Basic authentication and temporarily disabled CSRF for API testing.

**Note:** This is a temporary learning configuration. We will revisit security when implementing JWT authentication.

## 9. Project Structure After Day 3

```text
com.bhumi.movie_ticket_booking
│
├── config
│   └── SecurityConfig.java
│
├── controller
│   └── HelloController.java
│
├── dto
│   └── MovieRequest.java
│
└── MovieTicketBookingApplication.java
```

## 10. Day 3 Practical Summary

- Created a DTO class named `MovieRequest`.
- Created a GET endpoint `/hello`.
- Created a POST endpoint `/movies`.
- Used `@RestController`, `@GetMapping`, `@PostMapping` and `@RequestBody`.
- Configured endpoint permissions using Spring Security.
- Tested the POST API using Postman.
- Successfully received the movie title in the API response.

### What is pending?

The POST API does not save movies permanently yet.

In the next session, we will learn:
- Entity classes
- Spring Data JPA
- Repository layer
- Saving movie data in MySQL
