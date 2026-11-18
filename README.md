
# WebDev Roadmap

WebDev Roadmap is a React-based educational website designed to help beginners explore web development.

The website introduces essential web development concepts, popular frameworks, and practical programming tips.

## Features

- Home page with an introduction to web development
- Basics page for fundamental web development concepts
- Framework page for exploring web frameworks
- Tips page for practical learning advice
- Navigation between different learning sections

## Tech Stack

- React
- JavaScript
- HTML5
- CSS3
- React Router
- Create React App

## Getting Started

### Prerequisites

- Node.js
- npm

### Installation

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd WebDev-Roadmap
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm start
```

Open http://localhost:3000 in your browser.

## Project Structure

- `src/` - React components and application pages
- `public/` - Static assets and HTML files
- `package.json` - Project dependencies and scripts


## Attribution

This project was initially created using Create React App.

Create React App:
https://github.com/facebook/create-react-app
```

## Docker Setup

This project uses a multi-stage Docker build:

- Node.js 22 Alpine builds the React application.
- Nginx Alpine serves the production files.

### Prerequisites

- Docker Desktop installed and running

### Build the Docker Image

Run the following command from the project directory:

```bash
docker build -t webdev-roadmap .
```

### Run the Container

```bash
docker run -d --name webdev-roadmap-app -p 8080:80 webdev-roadmap
```

### Access the Application

Open the following URL:

http://localhost:8080

Use the navigation menu to explore:
- Basics
- Framework
- Tips

### Check the Container Status

```bash
docker ps
```

### Stop the Container

```bash
docker stop webdev-roadmap-app
```

### Remove the Container

```bash
docker rm webdev-roadmap-app
```

### Configuration

- Host port: 8080
- Container port: 80
- Web server: Nginx
- Environment variables: None required

### Troubleshooting

If port 8080 is already in use, run the container
with a different host port, for example:

```bash
docker run -d --name webdev-roadmap-app -p 8081:80 webdev-roadmap
```

Then open http://localhost:8081.

If the container name already exists, stop and remove
the old container before creating another one.


## Docker Management Scripts

The project includes npm scripts to simplify Docker management.

### Build the Docker Image

```bash
npm run docker:build
```

### Start the Application

```bash
npm run docker:run
```

The application will be available at:

http://localhost:8081

### Check Container Status

```bash
npm run docker:status
```

### Stop the Application

```bash
npm run docker:stop
```

These scripts use Docker Compose and make the project easier
to run and manage on Windows, Linux, and macOS.

