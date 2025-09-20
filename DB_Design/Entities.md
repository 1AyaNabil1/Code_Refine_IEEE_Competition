# The Core Entities

## Core Entities

1. Users
2. Movies
3. Genres
4. Cast_Members

## 1. Users Table

Stores the basic information about each user.

### Attributes

- id (Primary Key)
- first_name – User's first name
- last_name – User's last name
- email – Contact email (unique)
- password – Hashed password for authentication
- role – User role (user, admin)

## 2. Movies Table

This table stores all information related to movies in the system.

### Attributes

- id (Primary Key)
- title – Movie title
- description – Short description of the movie
- release_date – Movie release date
- duration – Length of the movie (in minutes)
- language – Primary language
- imdb_rating – IMDB rating
- avg_user_rating – Average rating from platform users
- num_views – Number of views

## 3. Genres Table

Stores movie genres for better categorization.

### Attributes

- id (Primary Key)
- name – Genre name (Action, Comedy, Drama, etc.)
- description – Genre description

## 4. Movie_Genres Table

Junction table for many-to-many relationship between movies and genres.

### Attributes

- movie_id (Foreign Key → Movies.id)
- genre_id (Foreign Key → Genres.id)
- Primary Key: (movie_id, genre_id)

## 5. Cast_Members Table

Stores information about actors, directors, and crew.

### Attributes

- id (Primary Key)
- name – Full name
- birth_date – Date of birth
- nationality – Nationality
- biography – Brief biography

## 6. Movie_Cast Table

Junction table linking movies with cast members and their roles.

### Attributes

- id (Primary Key)
- movie_id (Foreign Key → Movies.id)
- cast_member_id (Foreign Key → Cast_Members.id)
- role_type – Type of role (actor, director, producer, writer)
- character_name – Character name (for actors)

## 7. User_Movie_Interactions Table

Tracks all user interactions with movies (replaces User Behavior).

### Attributes

- id (Primary Key)
- user_id (Foreign Key → Users.id)
- movie_id (Foreign Key → Movies.id)
- interaction_type – Type of interaction (view, favorite, love, watchlist)
- rating – User's rating (1-10)

## 8. Reviews Table

Stores detailed user reviews (separate from ratings).

### Attributes

- id (Primary Key)
- user_id (Foreign Key → Users.id)
- movie_id (Foreign Key → Movies.id)
- title – Review title
- content – Review content
- rating – Review rating (1-10)

## 9. Movie_Lists Table

User-created movie lists ("Top 10 Action Movies").

### Attributes

- id (Primary Key)
- user_id (Foreign Key → Users.id)
- title – List title
- description – List description
- is_public – Whether list is public

## 10. Notifications Table

Stores user notifications.

### Attributes

- id (Primary Key)
- user_id (Foreign Key → Users.id)
- type – Notification type (new_movie, recommendation, review_like)
- title – Notification title
- message – Notification content
- is_read – Whether notification has been read
- related_entity_type – Type of related entity (movie, review, etc.)
- related_entity_id – ID of related entity
- created_at – Notification creation time