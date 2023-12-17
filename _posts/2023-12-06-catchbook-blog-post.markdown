---
layout: post
title: "Catchbook English"
---
![alternative text](\pbl-blog\image\Banner.jpg)
## Introduction
Hello! My name is Ronald Hrovat, and I recently completed a 10-month Java programming course at everyone Codes. To practice our newly acquired skills in Java and Spring Boot, we had six weeks to work on a small project of our choice. As an enthusiastic angler, I decided to create a project related to fishing. The project involves recording all fishing catches, including fish species, bait used, location, time, and date.

## Planning and Project Structure
For the implementation of my project, I decided on the following classes:
* FishType (Predator or Non-Predator)
* FishSpecies (Types of fish)
* Bait (Type of bait used to catch the fish)
* Place (Location where the fish was caught)
* Catch (Record of all caught fish)

## Database
PostgreSQL is used for the database. The database is located in an LXC on my server, connected via VPN. The LXC was created using Proxmox. For testing purposes, the database was also created in a Docker container using Portainer. The database consists of five tables:

### Table Fish_type:

| id  | fish_type      |
| --- | ---------------|
| 1   | NON_PREDATOR   |
| 2   | PREDATOR       |

### Table Species:

| fish_type_id | id | name      |
| ------------ | -- | --------- |
| 1            | 1  | Karpf     |
| 1            | 2  | Schleie   |
| 2            | 3  | Hecht     |
| 2            | 4  | Zander    |

### Table Bait:

| fish_type_id | id | bait       |
| ------------ | -- | ---------- |
| 1            | 1  | Erdbeere   |
| 1            | 2  | Vanille    |
| 2            | 3  | Wobbler    |
| 1            | 4  | Pink Tuna  |

### Table Place:

| id | place              |
| -- | ------------------ |
| 1  | Klein Meiseldorf   |
| 2  | Geras              |
| 3  | Klein Finnland     |

### Table Catch:

| length | weight | bait_id | catch_time          | id | place_id | species_id |
| ------ | ------ | ------- | ------------------- | -- | -------- | ---------- |
| null   | 8.3    | 1       | 2022-11-19 15:50:00 | 1  | 1        | 1          |
| null   | 6.5    | 2       | 2022-11-19 16:40:00 | 2  | 1        | 1          |
| 85     | null   | 3       | 2022-11-19 18:30:00 | 3  | 1        | 3          |

## Functionality
The user can expand and modify their lists of bait, places, and fish species. Once customized, the user can record their fishing catches.