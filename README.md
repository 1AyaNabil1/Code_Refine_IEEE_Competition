# IEEEMDB

IEEEMDB is a smart online platform that helps movie lovers discover films, track what they’ve watched, and share their thoughts with friends. It combines a personal movie diary with social networking features

## Functional Requirements
- Administrators can add, update, and remove movies and metadata via an admin interface
- Users can register, log in, and manage a personal profile with watch history and preferences
- The system stores and retrieves information about millions of movies (title, description, cast, trailers)
- Users can search and filter movies by title, cast, genre, and other attributes
- Users can rate movies and write detailed reviews linked to their profiles
- Users can create and share custom movie lists (like, “Top 10 Action Movies”)
- The recommendation engine provides personalized suggestions based on watch history and lists
- The system sends notifications when new movies matching user interests are available

## Non-Functional Requirements
- Scalability: Support millions of users and movie records with efficient data storage and retrieval.
- Performance: Ensure low-latency search and page loads (<200ms) under high load.
- Availability: Maintain 99.9% uptime with redundancy and failover strategies.
- Security: Protect user data with authentication, authorization, and encrypted communications.


# Data Model

## 1. Users Table
Stores the basic information about each user.

### Attributes:
- id (Primary Key) – Unique identifier for each user  
- first_name – User’s first name  
- last_name – User’s last name  
- email – Contact email  
- password – Hashed password for authentication  
- created_at – Date of account creation  



## 2. User Behavior Table
This table tracks how users interact with the system. It helps in personalization and recommendations.

### Attributes:
- id (Primary Key)  
- user_id (Foreign Key → Users.id)  
- favourites – List of movies the user marked as favorite  
- loves – Movies the user has “loved”  
- history – Watched movies history  
- reviews – Movies reviewed by the user  



## 3. Movies Table  
This table stores all information related to movies in the system.  

### Attributes:
- id (Primary Key)  
- name – Movie title  
- description – Short description of the movie  
- movie_url – URL to the movie file or streaming link  
- poster_url – URL to the movie poster  
- num_loves – Total number of loves  
- rating – Average rating from users  
- num_favourites – Total number of times added to favorites  
- num_views – Number of views  
- duration – Length of the movie


## 4. Movie Comments Table
This table stores user-generated comments and reviews on each movie.  

### Attributes:
- id (Primary Key)  
- user_id (Foreign Key → Users.id)  
- movie_id (Foreign Key → Movies.id)  
- review_text – Content of the comment/review  
- created_at – Date and time of the comment


## Relationships
- A user can interact with many movies (via favorites, loves, history, and reviews).  
- A movie can have multiple comments linked to it.  
- The user behavior table acts as a bridge to track preferences and interactions for each user.  



# API Design

We have different parts in our system:

1. **Auth API**
   - **Input:** User info
   - **Output:** Allows the user to log in to our system

2. **Movies API (Add New)**
   - **Input:** Movie details (movie name, description, movie URL, genre)
   - **Output:** Response indicating whether the addition was successful or not

3. **Recommendation API**
   - **Input:** Initially suggests movies randomly, then based on user behavior
   - **Output:** JSON with movie details (movie id, title, description, rating) to suggest on the main page

4. **Movie Page API**
   - **Input:** JSON with movie id and title
   - **Output:** JSON with all movie info (title, description, movie URL, poster URL, rating, number of views, number of loves, comments, etc.)

5. **Actions APIs**
   - **Input:** JSON with id, action type (comment, rate, love), user id, movie id
   - **Output:** Adds the action to its table and returns success or failure

6. **Search API**
   - **Input:** Keyword to search for movies
   - **Output:** Measures similarity and suggests results from the database

---

This README describes the main APIs required for a movie platform, including authentication, movie management, recommendations, movie details, user actions, and search functionality.
