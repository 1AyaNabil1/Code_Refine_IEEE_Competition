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
