# React Vite Minimal Project

A minimal React application built with Vite and containerized with Docker.

## Features

- ⚡️ Vite for fast development and optimized builds
- ⚛️ React 18 with modern hooks and features
- 🐳 Docker multi-stage build for optimized production images
- 🚀 Nginx for efficient static file serving
- 📦 Docker Compose for easy deployment

## Prerequisites

- Node.js 18+ (for local development)
- Docker and Docker Compose (for containerized deployment)
- npm or yarn

## Getting Started

### Local Development

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Start development server**
   ```bash
   npm run dev
   ```

3. **Open your browser**
   Navigate to `http://localhost:5173`

### Building for Production

```bash
npm run build
```

The production build will be in the `dist` directory.

### Preview Production Build

```bash
npm run preview
```

## Docker Deployment

### Using Docker

1. **Build the Docker image**
   ```bash
   docker build -t react-vite-app .
   ```

2. **Run the container**
   ```bash
   docker run -p 3000:80 react-vite-app
   ```

3. **Access the application**
   Open `http://localhost:3000` in your browser

### Using Docker Compose

1. **Start the application**
   ```bash
   docker-compose up
   ```

2. **Build and start (if image doesn't exist)**
   ```bash
   docker-compose up --build
   ```

3. **Run in detached mode**
   ```bash
   docker-compose up -d
   ```

4. **Stop the application**
   ```bash
   docker-compose down
   ```

## Project Structure

```
.
├── src/
│   ├── App.jsx          # Main React component
│   ├── App.css          # Component styles
│   ├── main.jsx         # Application entry point
│   └── index.css        # Global styles
├── index.html           # HTML template
├── package.json         # Dependencies and scripts
├── vite.config.js       # Vite configuration
├── Dockerfile           # Docker build configuration
├── docker-compose.yml   # Docker Compose configuration
├── .dockerignore        # Files excluded from Docker build
├── .gitignore          # Git ignore patterns
├── README.md           # This file
└── approach.md         # Detailed approach documentation
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally

## Docker Details

### Multi-Stage Build

The Dockerfile uses a multi-stage build process:
1. **Build stage**: Installs dependencies and builds the application
2. **Production stage**: Uses Nginx to serve the built static files

### Ports

- **Development**: 5173 (Vite default)
- **Production (Docker)**: 3000 (host) → 80 (container)

### Nginx Configuration

The container is configured with Nginx to:
- Serve static files efficiently
- Support Single Page Application (SPA) routing
- Handle all routes by serving `index.html`

## Environment Variables

The application supports environment variables through Vite's environment variable system:
- Create `.env` file for local development
- Variables prefixed with `VITE_` are exposed to the client code

## Troubleshooting

### Port Already in Use

If port 3000 is already in use, modify `docker-compose.yml`:
```yaml
ports:
  - "8080:80"  # Change 3000 to your preferred port
```

### Docker Build Fails

1. Ensure Docker is running
2. Check available disk space
3. Try clearing Docker cache: `docker system prune -a`

### Application Not Loading in Browser

1. Check container logs: `docker-compose logs`
2. Verify container is running: `docker ps`
3. Ensure correct port mapping in docker-compose.yml

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

MIT

## Additional Resources

- [Vite Documentation](https://vitejs.dev/)
- [React Documentation](https://react.dev/)
- [Docker Documentation](https://docs.docker.com/)
- [Nginx Documentation](https://nginx.org/en/docs/)


