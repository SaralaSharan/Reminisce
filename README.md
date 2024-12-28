## Live Demo

Experience Reminisce live on https://reminisce-w5gd.vercel.app/

## TEAM PRESENTATION

https://northeastern-my.sharepoint.com/:v:/r/personal/sharanappakanakagi_s_northeastern_edu/Documents/Recordings/Web%20Design%20Project%20Team-20241207_213729-Meeting%20Recording.mp4?csf=1&web=1&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=hCncDq

(reach out to us for any access issue - scroll down for contact details)


# Reminisce

Reminisce is a full-stack social media application designed to capture and share life's most memorable moments. Built on the MERN stack, this platform allows users from around the world to create and explore albums of memories, showcasing notable places visited and adventures experienced.

## Features

### Authentication
- Secure user registration and login system
- JWT (JSON Web Token) implementation for enhanced security

### Memory Management
- Create, read, update, and delete memories
- Rich text editor for detailed memory descriptions
- Image upload functionality for visual storytelling

### Search and Filtering
- Advanced search capabilities to find memories by tags (e.g., "Europe")
- Title-based search functionality
- search memories based on various criteria

### Internationalization
- Multi-language support enabling users to interact with the application in their preferred language
- Currently supported languages: English, Kannada(easily extendable to other languages)

### Accessibility & Fugu Features
- Read Aloud: A built-in text-to-speech feature that reads post title aloud for enhanced accessibility.
- Share Link of Post: Generate a sharable link for individual posts to easily share post with others.
- Download Post: Save a memory as a downloadable file (e.g., PDF format) for offline viewing and safekeeping

### Dark/Light Mode
- Switch between light and dark themes for a personalized browsing experience.
- Theme preferences persist across sessions for convenience.

### Pagination
- Efficient loading of memories through pagination
- Optimized performance by fetching a limited number of memories at a time

### Memory Details
- Dedicated pages for individual memories with expanded information
- Recommended memories section for related content discovery

### Comments
- Interactive comment system on memory posts
- Engage with other users' experiences and stories

### Client-Side Routing
- Smooth navigation between different sections of the application
- Enhanced user experience with fast page transitions

## Technology Stack

- **Frontend**: React.js
- **Backend**: Node.js with Express.js
- **Database**: MongoDB
- **Authentication**: JWT and Google OAuth
- **State Management**: Redux, Context API
- **Styling**: Styled-components, Tailwind CSS
- **Accessibility Features**: Text-to-speech, responsive design
- **Internationalization**: React-i18next integration

## Domain Model


```mermaid
---
title: Reminisce - Updated Domain Model with Enhanced Features
---
classDiagram
    class User {
      +String id
      +String username
      +String email
      +String password
      +String profilePicture
      +String bio
      +List~Post~ posts
      +List~Like~ likes
      +List~Notification~ notifications
    }

    class Post {
      +String id
      +String title
      +String content
      +DateTime createdAt
      +DateTime updatedAt
      +User author
      +List~Tag~ tags
      +List~Comment~ comments
      +int likeCount
    }

    class Tag {
      +String id
      +String name
    }

    class Comment {
      +String id
      +String text
      +DateTime createdAt
      +User author
      +Post post
    }

    class Like {
      +String id
      +User user
      +Post post
      +DateTime likedAt
    }

    class Notification {
      +String id
      +String type
      +String message
      +User recipient
      +DateTime createdAt
      +Boolean read
    }

    class Auth {
      +String token
      +DateTime expiresAt
    }

    User "1" --* "many" Post : "creates"
    Post "1" --> "1" User : "belongs to"
    Post "*" -- "*" Tag : "categorized by"
    Post "*" -- "*" Comment : "includes"
    Comment "1" --> "1" User : "authored by"
    Comment "1" --> "1" Post : "attached to"
    User "1" -- "*" Like : "likes"
    Post "1" -- "*" Like : "liked by"
    User "1" --> "*" Notification : "receives"
    User "1" --> "1" Auth : "authenticated by"
```

## API Endpoints
### Base URL: http://localhost:5002
### Authentication
- POST /auth/signup: Register a new user
- POST /auth/signin: User login
### Reminisce
- GET /posts: Get all memories with pagination
- GET /posts/search: Search for memories by title or tags
- GET /posts/:id: Get a specific memory by ID
- POST /posts: Create a new memory (authenticated)
- PATCH /posts/:id: Update an existing memory (authenticated)
- DELETE /posts/:id: Delete a memory (authenticated)
### Likes
- PATCH /posts/:id/likePost: Like or unlike a memory post (authenticated)
### Comments
- POST /posts/:id/commentPost: Add a comment to a memory post (authenticated)
### Fugu Features
- POST /posts/:id/readAloud: Generate an audio narration for a memory
- GET /posts/:id/share: Get a shareable link for a memory
- POST /posts/:id/download: Download a memory post in PDF format



## Run Instructions
Prerequisites
Ensure the following are installed:

Node.js
MongoDB (running locally or a connection string for a cloud database like MongoDB Atlas)
Setup Instructions
Clone the repository:


```bash
git clone https://github.com/info-6150-fall-2024/final-project-syncspace/reminisce.git
cd reminisce
```
Install dependencies:


```bash
cd server
npm install
```
Set up environment variables:

In the server directory, create a .env file with the following:
env
```
PORT=<APPLICATION_PORT>
MONGO_URI=<your_mongo_connection_string>
```

Start the application:

Start the server:

```
cd server
npm install
npm start
```

Start the Client:

```
cd client
npm install --legacy-peer-deps 
npm start
```

browse http://localhost:<APPLICATION_PORT>

OR

Checkout at: https://reminisce-w5gd.vercel.app/


## Team Members

| Name | Email |
|------|-------|
| Sarala Sharanappa Kanakagiri | sharanappakanakagi.s@northeastern.edu |
| Suhas Shetty | shetty.suh@northeastern.edu |
| Ullas Puttaiah | puttaiah.u@northeastern.edu |
| Ayush Patil | patil.ay@northeastern.edu |



## Contact

For general inquiries, please contact our team at sharanappakanakagi.s@northeastern.edu

---

Reminisce: Capturing moments, connecting worlds.
