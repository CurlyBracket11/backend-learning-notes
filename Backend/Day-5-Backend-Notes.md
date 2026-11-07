**What is a GET API?**
GET is an HTTP method used to retrieve data from a server.

For example, imagine a user opens our Movie Ticket Booking application.
The frontend needs to display all available movies. It sends a GET request to our backend.
Our backend fetches the movies from MySQL and returns them as JSON.


*What is @PathVariable?*
@PathVariable is used to extract a value from the URL and pass it into a Java method.

*findAll() – Saari Movies Fetch Karna*
JpaRepository mein already findAll() method available hota hai.
Is method ko use karke hum database ki saari movies retrieve kar sakte hain.
Humein khud SQL query likhne ki zarurat nahi padti.
Ye multiple movies return karta hai, isliye iska return type List<Movie> hota hai.


*getAllMovies() humara Service method hai.*
*findAll() repository ka built-in method hai.*

List<Movie> ka matlab multiple Movie objects ki list.

2. **GET /movies API**
Postman se GET request aati hai.
Controller request receive karta hai.
Controller Service ko call karta hai.
Service Repository ko call karta hai.
Repository database se saari movies fetch karta hai.
Movies JSON format mein Postman ko return hoti hain.

*Important: GET request ka use data retrieve karne ke liye hota hai. Ismein hum Body mein movie details bhejne ki zarurat nahi hoti.*


3. **findById() – Particular Movie Fetch Karna**
findById() JpaRepository ka built-in method hai.
Iska use kisi particular ID wali movie ko database se find karne ke liye hota hai.
Example: findById(3) ka matlab ID 3 wali movie search karna.
Iska return type Optional<Movie> hota hai.


4. **Optional<Movie> Kya Hai?**
Optional ka simple meaning hai ki requested movie mil bhi sakti hai aur nahi bhi.
Example:
findById(3) → Agar ID 3 exist karti hai toh movie milegi.
findById(999) → Agar ID 999 exist nahi karti toh movie nahi milegi.
Repository ko dono possibilities handle karni hoti hain, isliye woh directly Movie return nahi karta.


5.**orElseThrow() – Movie Nahi Mili Toh?**
Humne Service mein ye code likha:
Ismein:
findById(id) → Database mein movie search karta hai.
orElseThrow() → Agar movie nahi mili toh exception throw karta hai.
HttpStatus.NOT_FOUND → HTTP 404 status deta hai.
Matlab agar user /movies/999 request karta hai aur ID exist nahi karti, toh server 404 Not Found return karega.

6. **GET Movie By ID API**
Controller mein humne ye endpoint banaya:
GET http://localhost:8080/movies/3
Yahan:
{id} URL ka dynamic part hai.
@PathVariable URL se ID extract karta hai.
Controller us ID ko Service ke paas bhejta hai.
Service Repository ke through database mein movie search karwata hai.
Yaad rakhna: @PathVariable khud database mein search nahi karta. Ye sirf URL se value nikalta hai.


7. **HTTP 404 Not Found**
404 ka matlab hai ki server tak request pahunch gayi, lekin requested resource nahi mili.
Humare project mein:
/movies/3 → Movie exist karti hai toh 200 OK ke saath response.
/movies/999 → Movie exist nahi karti toh 404 Not Found.


8. **SecurityConfig Mein /movies/**
Pehle humare SecurityConfig mein ye tha:
.requestMatchers("/hello", "/movies").permitAll()
Isse /movies accessible tha, lekin /movies/3 par 401 Unauthorized aa raha tha.
Humne update karke ye kiya:
.requestMatchers("/hello", "/movies", "/movies/**").permitAll()
/movies/** ka matlab hai /movies/ ke andar aane wale nested paths ko bhi allow karna, jaise:

/movies/1

/movies/2

/movies/3

Isliye ab GET by ID API bhi bina authentication ke access ho sakti hai.


9. **Dono GET APIs Mein Difference**
GET /movies
Database ki saari movies fetch karega

GET /movies/3
Sirf ID 3 wali movie fetch karega


