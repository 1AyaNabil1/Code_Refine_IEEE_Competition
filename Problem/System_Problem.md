You're a lead developer creating a new online platform called **IEEEMDB**. Your mission is to build a smart system that helps people discover movies, track what they've watched, and share their thoughts with friends. Think of it as a personal movie diary and social network all in one.

This contest is about two main things:

1. **System Design:** Your plan for building the system.
2. **Implementation:** The actual code you write for a key part of it.

Your goal is to design a powerful, scalable system and implement a small demo to prove your design works.

### **The Challenge: IEEEMDB**

Your system needs to handle the entire user experience of a movie lover, from finding a new movie to sharing their review. This includes:

- **Admin Tools:** A simple way for administrators to add new movies and manage content.
- **User Profiles:** Creating a personal page for each user to track their watch history, reviews, and more features of your choice.
- **Movie Lists:** The ability to store and manage information about millions of movies, including titles, descriptions, video trailers, cast members, and other properties of your choice.
- **Search & Discovery:** A way for users to find movies by title, actor, genre, or other parameters.
- **Ratings & Reviews:** The ability for users to rate movies they've seen and write detailed reviews.
- **Lists & Collections:** Allowing users to create and share their own movie lists (e.g., "Top 10 Action Movies") and those lists appear in their personal profile page.
- **Movie Suggestions:** Based on their movie lists and watch history, the system recommends similar movies to the user. Note that no AI details is required here, just consider the recommendation algorithm as a black box that takes some user’s data and return back a list of recommendations.
- **Notifications:** The system sends push notifications to users whenever there’s a new movie the user might like based on some criteria like the movie tags for example.

---

### **Judging Criteria**

Your final work will be judged on these key parts:

- **Functional & Non-Functional Requirements (8%)**: How well you list what the system needs to do as well as the qualities of the system. In a typical system design interview, you are expected to list at least 4 functional and 3 non-functional requirements. Of course adding more is a plus, but up to a limit. You are fine as long as you cover all the use cases for the functional requirements and the whole user experience for the non-functional requirements.
- **Data Model (15%)**: How you organize and structure all the data related to the system. Note that you don’t need to create the whole database schema, just an overview of the data model covering all your requirements.
- **API Design (15%)**: How the different parts of the system will talk to each other. Also you don’t need to create all the API endpoints here, just enough to cover the core functionality of the system. For each one, you should specify the endpoint/function name (what identifies it), the request body/function arguments (what it takes), and the response body/function return (what it gives).
- **High-level Architecture (21%)**: Your main plan for all the different pieces of the system and how they work together. You are expected to draw a high-level diagram describing your system in separated components, each component is responsible for handling a single domain in your system. This component can be a separate microservice in a microservices architecture, or a separate module in a modular monolithic architecture. You are also expected to demonstrate how these components interact with one another, for example if some component needs to call another component for some reason, you should show this interaction in the diagram. Also, it’s CRUCIAL that you use consistent shapes for each component, if you use the circle shape to represent a database for example, ALL databases in your diagram should be circles too. Also you should label each shape with what it represents, don’t just draw the shape and assume we know what it represents, if it represents a database for example, type this explicitly on the shape or next to it. Feel free to use whatever shape to represent whatever component as long as you use it consistently and label it.
- **Deep Dives (21%)**: This is the most important part in a typical system design interview where you go deep in each critical component in your high-level architecture and start specifying the problems you will face at high scale, and based on those problems, you start specifying the trade-offs you are going to take to optimize the performance at high scales. For example, here you specify what kind of database you will use, whether it makes sense to perform caching in a certain component or not, whether to use a message broker, and so on. This section of the interview heavily tests your seniority level and how deep you understand the system problems.
- **Implementation (20%)**: The quality of your code. We will check that it's clean, easy to manage, and follows good coding practices. Note that you are not expected to implement the whole system, just implement its core features and other features of your choice. Feel free to use whatever framework/technology, or just implement it as a simple console application, it’s up to you and what you are most comfortable with.
- **Back-Of-The-Envelope-Estimation (Bonus)**: Your estimation of the system capacity or performance requirements. For example, how many daily active users (DAU) your system is expecting, or how many queries per second (QPS) your system supports, and so on.

Your final submission must be a **GitHub repository** that includes your code and a detailed README file. The README should clearly document your system. For the functional & non-functional requirements, the data model, the API design, and the high-level architecture, you are required to use **Excalidraw** and include the exported file in your repository. For the deep dives, you are required to state them in a `txt` or an `md` file and mention it in your README documentation. If you decided to do the back-of-the-envelope-estimation, feel free to add them in **Excalidraw** or a separated file, but also mention this in the [README](http://README.md) documentation.

Good luck. We look forward to seeing your ideas.