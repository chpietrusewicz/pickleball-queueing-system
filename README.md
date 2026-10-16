# 🏓 Pickleball Court Queueing System

A web app that manages the WPI Club Pickleball practice queue, court assignments, and player parties with persistent state and a live-updating interface.

**By Justin Fletcher, Josue Hernandez, Max Gambino, and Casey Pietrusewicz**

Built for WPI CS 4241 (Webware) Final Project in A Term 2026.

## Demo / Preview

🎥 **Video demonstration:** [Watch here](https://youtu.be/hR5E4vDZ-kA)

🌐 **Deployed website:** [Visit the application](https://pickleball-queueing-system-3e4e.onrender.com/)

## Overview

WPI Club Pickleball has weekly practices in the rec center. There is enough space for 4 courts and 4 people per court, so a total of 16 people. Because more than 16 people show up to the practices, a queue is needed to manage who is waiting to play and who is currently on a court.

To address this problem, we designed a web app to function as this queue system, complete with persistent state and a live-updating UI. We also have a party system so you can play with your friends.

## Key Features

- Queue management for players waiting to play.
- Court assignments for up to 4 courts with 4 people per court.
- Persistent state for practices and queue information.
- Live state updates across different browsers using WebSockets.
- Party system for playing with friends.
- Automatic grouping of smaller groups when a group of fewer than 4 players is at the top of the queue.
- Multiple themes.
- Cookies so users stay logged in when they refresh the page.
- Browser notifications when joining the queue.
- An End Practice button for administrators.

## Tech Stack

- React for front-end framework and components
- TypeScript as scripting language
- Tailwind CSS for styling
- Express for back-end server
- MongoDB for storing data
- WS for WebSockets, used for live communication between different instances of the website
- Postman for testing API endpoints

## Instructions

After going to the deployed URL, you can either create a new practice or join an existing one. We have one in the database using this code (`LNS12N`) with seeded data.

The admin account for this practice has the following credentials:

- **Username:** `admin`
- **Password:** `admin`

You can log into the seeded player accounts by using `player{number}` as the username and `pass{number}` as the password. You can also create your own account as long as it is not an existing username.

## Engineering Challenges & Learnings

One particularly difficult aspect of this project was the database design and endpoints. We went through several iterations designing endpoints and working with MongoDB. Our server file grew to be very large, but we were able to organize the functionality needed for the application.

We also found the WebSockets to be challenging but very rewarding. It was awesome to see live state updates happen in different browsers with no action from the user. The last challenge to this project was getting all of the different features to work together.

## Contributors

### 👨‍💻 Justin

- Worked on backend database schema and queue endpoints
- Connected front-end to backend by implementing handlers
- Implemented party system in client side and got it working with web sockets
- Performed QA and bug fixes
- Deployed website

### 👨‍💻 Josue

- Set up a Vite React TypeScript template
- Wrote the first version of the party endpoints
  - Create, leave, and enqueue parties
  - Sent requests to join, canceled, and responded to requests
- Started browser notifications when joining the queue

### 👨‍💻 Max

- **Frontend**
  - Created the pages
  - Used Tailwind CSS for styling
- **Queue system**
  - Would always try to get groups onto courts
  - Would group smaller groups together if a group of <4 is at the top of the queue
- Created a theme page with multiple themes
- Created cookies so users would stay logged in if they refreshed the page

### 👨‍💻 Casey

- Initialized connection to MongoDB during creation of the Express server
- Wrote the first version of the `createPractice` function
- Implemented WebSockets into the web app
  - Push state updates whenever a change occurs and broadcast to all current users/browsers
  - Wrote `useQueueSocket` to be able to display changes on React
  - Store practice code in localHost in case user gets disconnected
- Added an End Practice button to allow the admin to end the session
