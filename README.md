# IEEEMDB - IEEE Movie Database Platform

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
## Project Overview

**IEEEMDB** (IEEE Movie Database) is a comprehensive online platform designed for movie enthusiasts. It combines the functionality of a personal movie diary with social networking features, creating an intelligent system that helps users discover movies, track viewing history, and connect with fellow movie lovers.

---

## System Architecture

### High-Level Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Web Client    │    │  Mobile Client  │    │   Admin Panel   │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌────────────┴───────────┐
                    │       API Gateway      │
                    └─────────────┬──────────┘
                                  │
                    ┌─────────────┴──────────┐
                    │   Application Server   │
                    └────────────┬───────────┘
                                 │
                ┌────────────────┼────────────────┐
       ┌────────┴───────┐ ┌──────┴──────┐ ┌───────┴─────┐
       │    Database    │ │    Cache    │ │   Storage   │
       └────────────────┘ └─────────────┘ └─────────────┘
```
---

## Requirements

### Functional Requirements

1. **User Management**
   - User registration and authentication
   - Profile management and customization
   - Role-based access control (User/Admin)

2. **Movie Catalog**
   - Movie database with rich metadata
   - Movie search by title, genre, cast, and other attributes
   - Movie details with trailers, posters, and cast information

3. **User Interactions**
   - Rate and review movies
   - Add movies to favorites and watchlists
   - Track viewing history

4. **Movie Lists & Collections**
   - Create custom movie lists
   - Public and private list sharing
   - Collaborative list creation

5. **Recommendation System**
   - Personalized movie recommendations
   - Algorithm-based suggestions
   - Friend-based recommendations

6. **Notifications**
   - Real-time notifications for new movies
   - Social activity notifications
   - Recommendation alerts

### Non-Functional Requirements

1. **Performance**
   - Page load time < 2 seconds
   - API response time < 500ms
   - Support for 10,000+ concurrent users

2. **Scalability**
   - Horizontal scaling capability
   - Database optimization for large datasets
   - CDN integration for media delivery

3. **Security**
   - Secure authentication and authorization
   - Data encryption in transit and at rest
   - Input validation and SQL injection prevention

4. **Reliability**
   - 99.9% uptime availability
   - Automated backup and disaster recovery
   - Error handling and graceful degradation

5. **Usability**
   - Responsive design for all devices
   - Intuitive user interface
   - Accessibility compliance (WCAG 2.1)

---

## Database Design

### Entity Relationship Diagram

Our database follows a normalized design with the following core entities:

- **Users**: User accounts and profiles
- **Movies**: Movie catalog with metadata
- **Genres**: Movie categorization
- **Cast_Members**: Actor and crew information
- **Reviews**: User movie reviews
- **Movie_Lists**: User-created movie collections
- **User_Movie_Interactions**: User engagement tracking
- **Notifications**: System notifications
- **User_Follows**: Social connections

For detailed database schema, see: [Database Design Documentation](./DB_Design/Entities.md)

---

## API Design

### RESTful API Endpoints

Our API follows REST principles with clear, consistent endpoints:

#### Authentication

```
POST /auth/register     - User registration
POST /auth/login        - User login
```

#### Movies

```
GET  /movies           - Search and browse movies
GET  /movies/{id}      - Get movie details
POST /movies           - Add new movie (Admin)
```

#### User Interactions

```
POST /movies/{id}/rate      - Rate a movie
POST /movies/{id}/favorite  - Add to favorites
POST /movies/{id}/view      - Track movie view
```

#### Reviews

```
POST /movies/{id}/reviews   - Write a review
GET  /movies/{id}/reviews   - Get movie reviews
```

#### Movie Lists

```
POST /lists                 - Create movie list
POST /lists/{id}/movies     - Add movie to list
GET  /users/{id}/lists      - Get user's lists
```

For complete API documentation, see: [API Design](./api/api_design.json)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details