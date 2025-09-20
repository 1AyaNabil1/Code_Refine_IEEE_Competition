# The Core Entities
## Core Entities

1. Users
2. Movies
3. Genres
4. Cast_Members

## 1. Users Table
Stores the basic information about each user.

### Attributes:
- id (Primary Key) – Unique identifier for each user
- first_name – User's first name
- last_name – User's last name
- email – Contact email (unique)
- password – Hashed password for authentication
- role – User role (user, admin)
- profile_picture_url – URL to user's profile picture
- bio – User's bio/description
- created_at – Date of account creation
- updated_at – Last profile update

## 2. Movies Table
This table stores all information related to movies in the system.

### Attributes:
- id (Primary Key)
- title – Movie title
- description – Short description of the movie
- plot – Detailed plot summary
- movie_url – URL to the movie file or streaming link
- poster_url – URL to the movie poster
- trailer_url – URL to movie trailer
- release_date – Movie release date
- duration – Length of the movie (in minutes)
- language – Primary language
- country – Country of origin
- budget – Movie budget
- box_office – Box office earnings
- imdb_rating – IMDB rating
- avg_user_rating – Average rating from platform users
- num_ratings – Total number of user ratings
- num_favorites – Total number of times added to favorites
- num_views – Number of views
- created_at – Date added to platform
- updated_at – Last update

## 3. Genres Table
Stores movie genres for better categorization.

### Attributes:
- id (Primary Key)
- name – Genre name (Action, Comedy, Drama, etc.)
- description – Genre description

## 4. Movie_Genres Table
Junction table for many-to-many relationship between movies and genres.

### Attributes:
- movie_id (Foreign Key → Movies.id)
- genre_id (Foreign Key → Genres.id)
- Primary Key: (movie_id, genre_id)

## 5. Cast_Members Table
Stores information about actors, directors, and crew.

### Attributes:
- id (Primary Key)
- name – Full name
- birth_date – Date of birth
- nationality – Nationality
- biography – Brief biography
- profile_picture_url – URL to profile picture

## 6. Movie_Cast Table
Junction table linking movies with cast members and their roles.

### Attributes:
- id (Primary Key)
- movie_id (Foreign Key → Movies.id)
- cast_member_id (Foreign Key → Cast_Members.id)
- role_type – Type of role (actor, director, producer, writer)
- character_name – Character name (for actors)

## 7. User_Movie_Interactions Table
Tracks all user interactions with movies (replaces User Behavior).

### Attributes:
- id (Primary Key)
- user_id (Foreign Key → Users.id)
- movie_id (Foreign Key → Movies.id)
- interaction_type – Type of interaction (view, favorite, love, watchlist)
- rating – User's rating (1-10)
- created_at – When interaction occurred

## 8. Reviews Table
Stores detailed user reviews (separate from ratings).

### Attributes:
- id (Primary Key)
- user_id (Foreign Key → Users.id)
- movie_id (Foreign Key → Movies.id)
- title – Review title
- content – Review content
- rating – Review rating (1-10)
- likes_count – Number of likes on review
- created_at – Review creation date
- updated_at – Last update

## 9. Movie_Lists Table
User-created movie lists (e.g., "Top 10 Action Movies").

### Attributes:
- id (Primary Key)
- user_id (Foreign Key → Users.id)
- title – List title
- description – List description
- is_public – Whether list is public
- created_at – List creation date
- updated_at – Last update

## 10. Movie_List_Items Table
Items within each movie list.

### Attributes:
- id (Primary Key)
- list_id (Foreign Key → Movie_Lists.id)
- movie_id (Foreign Key → Movies.id)
- position – Order within the list
- notes – User notes about the movie in this list

## 11. User_Recommendations Table
Stores movie recommendations for users.

### Attributes:
- id (Primary Key)
- user_id (Foreign Key → Users.id)
- movie_id (Foreign Key → Movies.id)
- recommendation_score – Algorithm-generated score
- reason – Reason for recommendation
- is_seen – Whether user has seen the recommendation
- created_at – When recommendation was generated

## 12. Notifications Table
Stores user notifications.

### Attributes:
- id (Primary Key)
- user_id (Foreign Key → Users.id)
- type – Notification type (new_movie, recommendation, review_like)
- title – Notification title
- message – Notification content
- is_read – Whether notification has been read
- related_entity_type – Type of related entity (movie, review, etc.)
- related_entity_id – ID of related entity
- created_at – Notification creation time

## 13. User_Follows Table
Allows users to follow other users.

### Attributes:
- follower_id (Foreign Key → Users.id)
- following_id (Foreign Key → Users.id)
- created_at – When follow relationship started
- Primary Key: (follower_id, following_id)

## Key Relationships:
- Users can have many interactions with movies (favorites, ratings, reviews)
- Movies belong to multiple genres (many-to-many)
- Movies have multiple cast members in different roles (many-to-many)
- Users can create multiple movie lists with multiple movies
- Users can follow other users
- Users receive personalized recommendations and notifications
- Reviews can be liked by other users (through a separate likes table if needed)