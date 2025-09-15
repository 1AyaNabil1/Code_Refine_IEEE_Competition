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
