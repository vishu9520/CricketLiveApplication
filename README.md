# 🏏 Cricket Live Application

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.4-brightgreen.svg?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-17-orange.svg?logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![React](https://img.shields.io/badge/React-19.2-blue.svg?logo=react&logoColor=white)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-7.2-646CFF.svg?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4.1-38B2AC.svg?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1.svg?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED.svg?logo=docker&logoColor=white)](https://www.docker.com/)

A modern, full-stack **Cricket Live Score Application** delivering real-time match scores, tournament schedules, team rankings, player career statistics, and cricket news. Built with a high-performance **Spring Boot 3** REST API backend and an interactive **React 19 + Vite** single-page frontend styled with **Tailwind CSS** and **shadcn/ui**.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Architecture & Tech Stack](#-architecture--tech-stack)
- [Repository Structure](#-repository-structure)
- [API Reference](#-api-reference)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Database Setup](#1-database-setup)
  - [Backend Setup](#2-backend-setup)
  - [Frontend Setup](#3-frontend-setup)
- [Docker Deployment](#-docker-deployment)
- [Configuration](#-configuration)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 Overview

The **Cricket Live Application** gives cricket fans an all-in-one platform for following international and domestic cricket:
- **Live Match Center**: Instant updates on live matches, scorecards, current batsmen, bowler economy, and match status.
- **Series & Tournaments**: Follow ongoing tournaments, upcoming fixtures, and historical results.
- **ICC Team Rankings**: Real-time team rankings and rating points categorized across **Test**, **ODI**, and **T20** formats.
- **Player Hub**: Deep-dive player profiles with career runs, batting averages, centuries, wickets, and country filters.
- **Cricket Newsroom**: Curated news articles categorized by topics, with spotlight highlights and author tracking.

---

## ✨ Key Features

- 🔴 **Real-Time Scoreboard**: Dynamic polling for live cricket matches with current run-rates and active batsmen stats.
- 📅 **Fixtures & Results**: Filter matches by format (`TEST`, `ODI`, `T20`), participating team, or tournament series.
- 🏆 **Rankings Dashboard**: Comprehensive ICC standings for all three formats with win/loss/draw records.
- 👤 **Player Spotlight & Leaderboards**: Showcase top-run scorers, highest averages, and century makers with full profile cards.
- 📰 **News & Editorial**: Categorized news feeds, featured headlines, and author archives.
- 🌓 **Dark & Light Mode**: Built-in responsive theme switcher powered by Tailwind CSS.
- 📖 **OpenAPI / Swagger UI**: Interactive API documentation for seamless testing and third-party integration.
- 🐳 **Containerized**: Pre-configured `Dockerfile` for seamless deployment.

---

## 🛠️ Architecture & Tech Stack

```
┌────────────────────────────────┐         REST / JSON          ┌──────────────────────────────────┐
│        Frontend Client         │ <══════════════════════════> │          Backend Server          │
│   • React 19 + Vite 7          │     (HTTP / CORS Allowed)    │   • Spring Boot 3.4.4 (Java 17)  │
│   • Tailwind CSS 4 + shadcn/ui │                              │   • Spring Data JPA (Hibernate)  │
│   • Lucide Icons + Radix UI    │                              │   • SpringDoc OpenAPI / Swagger  │
└────────────────────────────────┘                              └─────────────────┬────────────────┘
                                                                                  │ JDBC
                                                                                  ▼
                                                                ┌──────────────────────────────────┐
                                                                │             Database             │
                                                                │         • MySQL 8.0+             │
                                                                │   (cricket_db schema & seeds)    │
                                                                └──────────────────────────────────┘
```

### Backend
- **Language**: Java 17
- **Framework**: Spring Boot 3.4.4
- **ORM / Persistence**: Spring Data JPA & Hibernate
- **Database Driver**: MySQL Connector/J
- **API Documentation**: Springdoc OpenAPI Starter WebMVC UI (Swagger)
- **Utilities**: Project Lombok, Hibernate Validator

### Frontend
- **Framework**: React 19 (JavaScript SPA)
- **Bundler & Tooling**: Vite 7
- **Routing**: React Router v7
- **Styling**: Tailwind CSS v4, PostCSS, Radix UI Primitives, Lucide Icons

### Database & DevOps
- **Database**: MySQL 8.0+
- **Containerization**: Docker (Eclipse Temurin 17 JDK)

---

## 📂 Repository Structure

```text
Cricket-Application/
├── backend/
│   └── demo/
│       ├── src/main/java/com/example/demo/
│       │   ├── controller/          # REST Controllers (Match, Player, Team, Tournament, News)
│       │   ├── entity/              # JPA Entities (Match, Player, Team, Tournament, NewsArticle)
│       │   ├── repository/          # Spring Data JPA Repositories
│       │   ├── service/             # Business Logic Layer
│       │   └── CricketPracticeBackendApplication.java
│       ├── src/main/resources/
│       │   └── application.properties # Server port & Datasource settings
│       ├── pom.xml                  # Maven dependencies & build plugins
│       └── mvnw, mvnw.cmd           # Maven Wrapper scripts
├── Frontend/
│   ├── src/
│   │   ├── components/              # Navigation, Header, Theme toggles & shadcn UI components
│   │   ├── pages/                   # Home, LiveScores, MatchCenter, News, Players, Rankings, Series
│   │   ├── lib/                     # UI utilities (clsx, tailwind-merge)
│   │   ├── App.jsx                  # Main routing configuration
│   │   └── main.jsx                 # Entry point
│   ├── package.json                 # Node dependencies and scripts
│   ├── vite.config.js               # Vite configuration
│   └── .env                         # Frontend environment variables
├── database/
│   └── SQL.txt                      # Complete MySQL schema creation & sample seed data
├── Dockerfile                       # Multi-stage Docker container specification
└── README.md                        # Documentation
```

---

## 🔌 API Reference

The backend exposes RESTful endpoints under `/api`. When running locally, explore the interactive documentation via **Swagger UI** at:
`http://localhost:8080/swagger-ui/index.html`

### 1. Matches (`/api/matches`)
| Method | Endpoint | Description |
|:-------|:---------|:------------|
| `GET` | `/api/matches` | Get all matches |
| `GET` | `/api/matches/live` | Retrieve live in-progress matches |
| `GET` | `/api/matches/{id}` | Get match details by ID |
| `GET` | `/api/matches/recent` | Get recently concluded matches |
| `GET` | `/api/matches/upcoming` | Get upcoming scheduled fixtures |
| `GET` | `/api/matches/team/{teamName}` | Filter matches by team name |
| `GET` | `/api/matches/series/{seriesName}` | Filter matches by series or tournament |
| `GET` | `/api/matches/format/{format}` | Filter by format (`TEST`, `ODI`, `T20`) |

### 2. Teams & Rankings (`/api/teams`)
| Method | Endpoint | Description |
|:-------|:---------|:------------|
| `GET` | `/api/teams` | List all teams |
| `GET` | `/api/teams/{id}` | Get team details by ID |
| `GET` | `/api/teams/rankings?format=TEST` | Get rankings for `TEST`, `ODI`, or `T20` |
| `GET` | `/api/teams/format/{format}` | Get teams matching a specific format |
| `GET` | `/api/teams/name/{name}` | Look up a team by name |
| `GET` | `/api/teams/formats` | List all available formats |
| `GET` | `/api/teams/test` | Get Test rankings |
| `GET` | `/api/teams/odi` | Get ODI rankings |
| `GET` | `/api/teams/t20` | Get T20 rankings |

### 3. Players (`/api/players`)
| Method | Endpoint | Description |
|:-------|:---------|:------------|
| `GET` | `/api/players` | List all players |
| `GET` | `/api/players/{id}` | Get player by ID |
| `GET` | `/api/players/spotlight` | Get featured spotlight players |
| `GET` | `/api/players/top/runs` | Leaderboard: Top run scorers |
| `GET` | `/api/players/top/average` | Leaderboard: Highest batting averages |
| `GET` | `/api/players/top/centuries` | Leaderboard: Most centuries scored |
| `GET` | `/api/players/country/{country}` | Filter players by country |
| `GET` | `/api/players/position/{position}` | Filter by role (`Batsman`, `Bowler`, `All-Rounder`) |

### 4. Tournaments (`/api/tournaments`)
| Method | Endpoint | Description |
|:-------|:---------|:------------|
| `GET` | `/api/tournaments` | List all tournaments |
| `GET` | `/api/tournaments/{id}` | Get tournament details by ID |
| `GET` | `/api/tournaments/live` | Ongoing tournaments |
| `GET` | `/api/tournaments/upcoming` | Upcoming tournaments |
| `GET` | `/api/tournaments/completed` | Concluded tournaments |
| `GET` | `/api/tournaments/location/{location}` | Filter by host location |

### 5. News Articles (`/api/news`)
| Method | Endpoint | Description |
|:-------|:---------|:------------|
| `GET` | `/api/news` | List all news articles |
| `GET` | `/api/news/{id}` | Get article by ID |
| `GET` | `/api/news/featured` | Get featured news stories |
| `GET` | `/api/news/category/{category}` | Filter news by category |
| `GET` | `/api/news/author/{author}` | Filter news by author name |
| `GET` | `/api/news/categories` | List unique news categories |
| `GET` | `/api/news/authors` | List unique authors |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have installed:
- **Java Development Kit (JDK) 17+**
- **Node.js 18+ & npm**
- **MySQL Server 8.0+**
- **Git**

---

### 1. Database Setup

1. Start your local MySQL server.
2. Log into MySQL and run the seed script provided in [`database/SQL.txt`](database/SQL.txt):

```bash
mysql -u root -p < database/SQL.txt
```

This will automatically create the `cricket_db` database, initialize tables (`teams`, `players`, `matches`, `match_current_batsmen`, `tournaments`, `news_articles`), and seed sample cricket records.

---

### 2. Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend/demo
   ```

2. Configure your MySQL credentials. You can either export environment variables or update `src/main/resources/application.properties`:

   **Using Environment Variables (Recommended):**
   ```bash
   # Windows (PowerShell)
   $env:SPRING_DATASOURCE_URL="jdbc:mysql://localhost:3306/cricket_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC"
   $env:SPRING_DATASOURCE_USERNAME="your_mysql_username"
   $env:SPRING_DATASOURCE_PASSWORD="your_mysql_password"

   # Linux / macOS
   export SPRING_DATASOURCE_URL="jdbc:mysql://localhost:3306/cricket_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC"
   export SPRING_DATASOURCE_USERNAME="your_mysql_username"
   export SPRING_DATASOURCE_PASSWORD="your_mysql_password"
   ```

3. Build and launch the Spring Boot server:
   ```bash
   # Windows
   ./mvnw.cmd spring-boot:run

   # Linux / macOS
   chmod +x ./mvnw
   ./mvnw spring-boot:run
   ```

   The backend will start at: `http://localhost:8080` (or the configured port).

---

### 3. Frontend Setup

1. In a separate terminal, navigate to the frontend directory:
   ```bash
   cd Frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Verify or edit the backend API base URL in `Frontend/.env`:
   ```env
   VITE_API_BASE_URL=http://localhost:8080/api
   ```
   *(Ensure the port matches your backend server's active port).*

4. Start the Vite development server:
   ```bash
   npm run dev
   ```

5. Open your browser and navigate to:
   ```
   http://localhost:5173
   ```

---

## 🐳 Docker Deployment

To build and run the backend inside a Docker container:

1. **Build the Docker Image**:
   ```bash
   docker build -t cricket-backend .
   ```

2. **Run the Container**:
   ```bash
   docker run -p 8080:8080 \
     -e SPRING_DATASOURCE_URL="jdbc:mysql://host.docker.internal:3306/cricket_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC" \
     -e SPRING_DATASOURCE_USERNAME="root" \
     -e SPRING_DATASOURCE_PASSWORD="your_password" \
     cricket-backend
   ```

---

## ⚙️ Configuration

### Backend (`application.properties`)
| Property | Description | Default |
|:---------|:------------|:--------|
| `server.port` | Backend port | `8080` |
| `spring.datasource.url` | Database JDBC URL | Environment variable |
| `spring.datasource.username` | Database user | Environment variable |
| `spring.datasource.password` | Database password | Environment variable |
| `spring.jpa.hibernate.ddl-auto` | Hibernate schema action | `update` |
| `spring.jpa.show-sql` | Output SQL queries in logs | `true` |

### Frontend (`.env`)
| Variable | Description | Default |
|:---------|:------------|:--------|
| `VITE_API_BASE_URL` | Base endpoint for API requests | `http://localhost:8080/api` |

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/NewFeature`).
3. Commit your changes (`git commit -m "Add new feature"`).
4. Push to your branch (`git push origin feature/NewFeature`).
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
