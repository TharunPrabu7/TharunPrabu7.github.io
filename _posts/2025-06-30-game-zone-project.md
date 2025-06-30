---
permalink: "/game-zone-project"
description: "Full-stack CRUD app for game data using React and Spring Boot"
title: "Game Zone: A Full-Stack Game Management App"
date: "2025-06-30"
layout: post
---

## Preface

This project started out as a hands-on experiment to deepen my full-stack web development skills, especially around Java Spring Boot and modern frontend tools like React and TypeScript. What began as a simple login form quickly evolved into a full-fledged CRUD app where users can view, add, update, and delete video game records. I call it **Game Zone**.

Throughout this journey, I tackled user authentication, state management, dynamic routing, context sharing, and backend filtering—all while ensuring that users had a smooth experience whether they were logged in or just browsing.

## The Premise

The core idea of **Game Zone** is simple: allow users to manage a database of video games through a clean web interface. Anyone can view the list of games, but only authenticated users can perform actions like adding a new game, editing existing entries, or deleting them.

The game data includes:

- Name  
- Genre  
- Release Date  
- Copies Sold  
- Rating  
- Studio  
- Revenue  
- Game of the Year (Boolean)

## Frontend — React + TypeScript

The frontend was built with:

- **React** (with functional components)
- **TypeScript** for better type safety
- **React Router** for page navigation
- **Context API** to share global states like authentication and game data
- **CSS** for styling (with a sprinkle of Uiverse.io animations)

### Features:

- A beautiful **login/signup UI**
- Game listing table with clickable rows for detail views
- Conditional rendering of **Add**, **Edit**, and **Delete** buttons for logged-in users
- **Search bar** to filter games by name
- **Game detail pages** accessible via dynamic routing

```tsx
<Route path="/game/:name" element={<GameDetail />} />
```

## Backend — Java Spring Boot

The backend is built with:

- **Spring Boot**
- **Spring Security** (disabled default security and customized for CORS/auth)
- **Spring Data JPA**
- **PostgreSQL** as the database

### Highlights:

- RESTful endpoints for all CRUD operations (`/add`, `/edit`, `/delete`, `/login`)
- `@CrossOrigin` setup to communicate with React on localhost:5173
- Filtering logic on the backend with support for optional parameters
- Secure password handling using `BCryptPasswordEncoder`
- Global CORS configuration with `WebMvcConfigurer`

## Authentication

When a user signs up or logs in, the backend verifies credentials and returns a response object. While I didn’t implement JWT in this version, the system respects frontend logic for access control.

Logged-in users have access to the **admin panel** features like:

- `Add Game`
- `Edit Game`
- `Delete Game`

Unauthenticated users can still view the full game table, ensuring the app remains usable in read-only mode.

## Data Isolation

One key requirement was to ensure that user-added games don't affect the original dataset. This was handled by:

- Keeping all persistent changes in a separate table
- Making the game listing a **read-only view** unless authenticated
- Only showing "Add", "Edit", "Delete" when logged in

This way, the public-facing table remains pristine.

## Final Touches

To complete the user experience:

- A **Logout button** was added in the top-right corner
- User session is managed with Context API (lightweight, no external libraries)
- Input validation and friendly error messages were added

Here’s a sneak peek of the UI:

![Game Zone Screenshot](/assets/img/game-zone-preview.png)  
*Assuming you’ll add an image*

## Finishing Thoughts

This project was one of the most fun and practical full-stack builds I’ve done. It sharpened my skills in:

- Backend filtering logic
- Full-stack routing and state sharing
- React component design and styling
- Auth control and UI feedback loops

I plan to keep improving Game Zone—adding JWT-based authentication, user roles, and perhaps even game cover art with file uploads.

Check out the GitHub repo [here](https://github.com/TharunPrabu7) if you’d like to explore the code.

If you're a recruiter: yes, I do backend. But also… a little bit of everything else too. 😄
