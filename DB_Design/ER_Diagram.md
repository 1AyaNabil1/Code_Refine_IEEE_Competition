# IEEEMDB Entity-Relationship Diagram

## Visual ER Diagram

```mermaid
erDiagram
    USERS {
        int id PK
        string first_name
        string last_name
        string email UK
        string password
        string role
        string profile_picture_url
        text bio
        datetime created_at
        datetime updated_at
    }
    
    MOVIES {
        int id PK
        string title
        text description
        text plot
        string movie_url
        string poster_url
        string trailer_url
        date release_date
        int duration
        string language
        string country
        decimal budget
        decimal box_office
        float imdb_rating
        float avg_user_rating
        int num_ratings
        int num_favorites
        int num_views
        datetime created_at
        datetime updated_at
    }
    
    GENRES {
        int id PK
        string name
        text description
    }
    
    CAST_MEMBERS {
        int id PK
        string name
        date birth_date
        string nationality
        text biography
        string profile_picture_url
    }
    
    REVIEWS {
        int id PK
        int user_id FK
        int movie_id FK
        string title
        text content
        int rating
        int likes_count
        datetime created_at
        datetime updated_at
    }
    
    MOVIE_LISTS {
        int id PK
        int user_id FK
        string title
        text description
        boolean is_public
        datetime created_at
        datetime updated_at
    }
    
    USER_RECOMMENDATIONS {
        int id PK
        int user_id FK
        int movie_id FK
        float recommendation_score
        text reason
        boolean is_seen
        datetime created_at
    }
    
    NOTIFICATIONS {
        int id PK
        int user_id FK
        string type
        string title
        text message
        boolean is_read
        string related_entity_type
        int related_entity_id
        datetime created_at
    }
    
    MOVIE_GENRES {
        int movie_id PK,FK
        int genre_id PK,FK
    }
    
    MOVIE_CAST {
        int id PK
        int movie_id FK
        int cast_member_id FK
        string role_type
        string character_name
    }
    
    USER_MOVIE_INTERACTIONS {
        int id PK
        int user_id FK
        int movie_id FK
        string interaction_type
        int rating
        datetime created_at
    }
    
    MOVIE_LIST_ITEMS {
        int id PK
        int list_id FK
        int movie_id FK
        int position
        text notes
    }
    
    USER_FOLLOWS {
        int follower_id PK,FK
        int following_id PK,FK
        datetime created_at
    }

    %% Relationships
    USERS ||--o{ REVIEWS : writes
    MOVIES ||--o{ REVIEWS : receives
    
    USERS ||--o{ USER_MOVIE_INTERACTIONS : performs
    MOVIES ||--o{ USER_MOVIE_INTERACTIONS : receives
    
    MOVIES ||--o{ MOVIE_GENRES : belongs_to
    GENRES ||--o{ MOVIE_GENRES : categorizes
    
    MOVIES ||--o{ MOVIE_CAST : features
    CAST_MEMBERS ||--o{ MOVIE_CAST : appears_in
    
    USERS ||--o{ MOVIE_LISTS : creates
    MOVIE_LISTS ||--o{ MOVIE_LIST_ITEMS : contains
    MOVIES ||--o{ MOVIE_LIST_ITEMS : listed_in
    
    USERS ||--o{ USER_RECOMMENDATIONS : receives
    MOVIES ||--o{ USER_RECOMMENDATIONS : recommended
    
    USERS ||--o{ NOTIFICATIONS : receives
    
    USERS ||--o{ USER_FOLLOWS : follows
    USERS ||--o{ USER_FOLLOWS : followed_by
```

## Entity Descriptions

### Core Entities

#### Users
- **Purpose**: Store user account information and profiles
- **Key Features**: Authentication, profiles, role-based access
- **Relationships**: Central entity connecting to all user activities

#### Movies
- **Purpose**: Complete movie catalog with metadata
- **Key Features**: Rich metadata, ratings, statistics
- **Relationships**: Core content entity linked to all interactions

#### Genres
- **Purpose**: Movie categorization system
- **Key Features**: Hierarchical categorization, search optimization
- **Relationships**: Many-to-many with movies

#### Cast_Members
- **Purpose**: Actor, director, and crew information
- **Key Features**: Biography, filmography tracking
- **Relationships**: Many-to-many with movies through roles

### Interaction Entities

#### Reviews
- **Purpose**: Detailed user feedback on movies
- **Key Features**: Ratings, text reviews, social engagement
- **Relationships**: Links users to movies with detailed feedback

#### User_Movie_Interactions
- **Purpose**: Track all user engagement with movies
- **Key Features**: Views, favorites, watchlist, quick ratings
- **Relationships**: Flexible interaction tracking system

#### Movie_Lists
- **Purpose**: User-curated movie collections
- **Key Features**: Custom lists, public/private sharing
- **Relationships**: Users create lists containing multiple movies

### System Entities

#### User_Recommendations
- **Purpose**: Personalized movie suggestions
- **Key Features**: Algorithm-driven recommendations, tracking
- **Relationships**: System-generated user-movie connections

#### Notifications
- **Purpose**: User engagement and updates
- **Key Features**: Multiple notification types, read status
- **Relationships**: User-centric communication system

#### User_Follows
- **Purpose**: Social networking features
- **Key Features**: Follow relationships, social discovery
- **Relationships**: Self-referencing user connections

## Key Relationship Patterns

### 1. User-Centric Design
- All major entities connect back to users
- Supports personalization and user experience tracking
- Enables comprehensive user profiles

### 2. Content Organization
- Movies as central content entity
- Multiple categorization methods (genres, cast, lists)
- Rich metadata for search and discovery

### 3. Interaction Tracking
- Multiple interaction types supported
- Historical tracking for recommendations
- Social features for community building

### 4. Scalability Considerations
- Junction tables for many-to-many relationships
- Denormalized statistics for performance
- Modular design for feature expansion

## Database Implementation Notes

### Indexes
```sql
-- Performance-critical indexes
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_movies_title ON movies(title);
CREATE INDEX idx_movies_rating ON movies(avg_user_rating DESC);
CREATE INDEX idx_reviews_user_movie ON reviews(user_id, movie_id);
CREATE INDEX idx_interactions_user ON user_movie_interactions(user_id);
CREATE INDEX idx_notifications_user_unread ON notifications(user_id, is_read);
```

### Constraints
```sql
-- Business logic constraints
ALTER TABLE reviews ADD CONSTRAINT chk_rating CHECK (rating BETWEEN 1 AND 10);
ALTER TABLE user_movie_interactions ADD CONSTRAINT chk_interaction_rating CHECK (rating IS NULL OR rating BETWEEN 1 AND 10);
ALTER TABLE movies ADD CONSTRAINT chk_duration CHECK (duration > 0);
ALTER TABLE user_follows ADD CONSTRAINT chk_no_self_follow CHECK (follower_id != following_id);
```