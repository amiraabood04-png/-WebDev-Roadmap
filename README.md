# WebDev Roadmap

WebDev Roadmap is a React-based educational website that introduces beginners to web development fundamentals, popular frameworks, and practical programming tips.

## Features

- Home page introducing web development
- Basics page covering fundamental concepts
- Framework page introducing web development frameworks
- Tips page with practical learning advice
- Navigation between sections using React Router

## Tech Stack

- React 18
- JavaScript, HTML5, and CSS3
- React Router
- Create React App
- Node.js 22 Alpine (build stage)
- Nginx Alpine (production web server)
- Docker and Docker Compose
- Git and GitHub Actions

## Project Structure

```text
src/                    React components and pages
public/                 Static assets
Dockerfile              Multi-stage Docker build
.dockerignore           Files excluded from Docker build context
.gitignore              Files excluded from Git tracking
docker-compose.yml      Docker Compose configuration
.github/workflows/      Automated Docker build workflow
docs/notes.md           Technical lessons and challenges
docs/screenshots/       Assignment evidence screenshots
package.json            Dependencies and convenience scripts
```

## Prerequisites

For local development, install Node.js and npm.

For containerized deployment, install Docker Desktop (or Docker Engine with Docker Compose) and make sure it is running.

## Clone the Repository

```bash
git clone https://github.com/amiraabood04-png/-WebDev-Roadmap.git
cd -WebDev-Roadmap
```

## Run Locally (Without Docker)

```bash
npm install
npm start
```

Open http://localhost:3000 in your browser.

## Run with Docker

The Dockerfile uses a multi-stage build: Node.js installs dependencies and builds the React production files; Nginx serves the resulting static application.

### 1. Build the Image

```bash
docker build -t webdev-roadmap .
```

### 2. Start the Container

```bash
docker run -d --name webdev-roadmap-app -p 8080:80 webdev-roadmap
```

### 3. Verify the Application

Open http://localhost:8080 and check the Home, Basics, Framework, and Tips pages.

To inspect running containers:

```bash
docker ps
```

The container includes an HTTP healthcheck. After startup, `docker ps` can report `(healthy)` once the check passes.

### 4. Stop and Remove the Container

```bash
docker stop webdev-roadmap-app
docker rm webdev-roadmap-app
```

## Run with Docker Compose (Bonus A)

```bash
docker compose config
docker compose up -d --build
docker compose ps
```

Open http://localhost:8081. To stop and remove the Compose-managed container and network:

```bash
docker compose down
```

The Compose configuration uses host port **8081** mapped to container port **80**, so it can coexist with a manually started container on host port 8080.

## Docker Management Scripts (Bonus E)

The following npm scripts wrap Docker Compose:

| Command | Purpose |
|---|---|
| `npm run docker:build` | Build the Docker image |
| `npm run docker:run` | Start the Compose service |
| `npm run docker:status` | Show Compose container status |
| `npm run docker:stop` | Stop and remove the Compose service |

After modifying application code, rebuild the image before restarting the Compose service:

```bash
npm run docker:build
npm run docker:run
```

## Configuration

| Setting | Value |
|---|---|
| Production web server | Nginx |
| Container port | 80 |
| Docker host port | 8080 |
| Docker Compose host port | 8081 |
| Required application environment variables | None |

If a host port is already in use, stop the conflicting container or choose a different free host port.

## GitHub Actions CI (Bonus B)

The workflow in `.github/workflows/docker-build.yml` automatically builds the Docker image for pushes to `main` and pull requests targeting `main`. The workflow verifies the image build and does not publish it to a container registry.

## Additional Bonus Features

- **Multi-stage build (Bonus C):** Uses Node.js for building and Nginx for serving production output.
- **Healthcheck (Bonus D):** Checks the HTTP response of the running Nginx container.
- **Pull Request workflow (Bonus G):** A documentation feature branch was merged into `main` through Pull Request #1.

## Troubleshooting

- **`npm ci` lockfile error:** Ensure `package.json` and `package-lock.json` are synchronized. The technical notes describe the dependency issue encountered in this assignment.
- **Container name already exists:** Stop and remove the existing container before running another one with the same name.
- **Port already allocated:** Stop the container using the port or map a different available host port.
- **Docker cannot download images:** Check Docker Desktop connectivity and DNS configuration.

## Documentation and Evidence

- Technical notes: [`docs/notes.md`](docs/notes.md)
- Screenshots: [`docs/screenshots/`](docs/screenshots/)

## Attribution

This project was originally bootstrapped using [Create React App](https://github.com/facebook/create-react-app). Its educational site content and Docker workflow were developed as part of the OS Lab assignment.
