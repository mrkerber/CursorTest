# Media Logging App

## Overview
This application will allow users to log their media consumption across multiple platforms (web and mobile). Users can log movies, books, and games, providing a rating from 1 to 10 for each entry.

## MVP Scope
- User authentication
- Media entry form for logging movies, books, and games
- Ability to rate entries from 1 to 10
- Simple dashboard displaying logged media

## Planned Features
- Filter and sort media by type and rating
- Wishlist functionality to track desired media
- Integration with social media for sharing logs
- User profiles with detailed statistics and insights on logged media

## High-Level Architecture
- **Frontend**: Built using React for web and React Native for mobile, ensuring consistency across platforms.
- **Backend**: RESTful API developed in Node.js, connected to a MongoDB database for storage.
- **Authentication**: Utilization of JWT for secure authentication across platforms.