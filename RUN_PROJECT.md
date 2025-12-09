# Running Sherzod Hakimov's Website with Docker

This guide provides all the commands you need to run, manage, and stop the Jekyll site using Docker.

## Prerequisites

- Docker Desktop installed and running
- Terminal/Command line access

## Quick Start

### 1. Set Permissions (First Time Only)

Before running Docker for the first time, set the correct permissions:

```bash
chmod -R 777 .
```

### 2. Build and Run the Project

Start the Jekyll site with Docker Compose:

```bash
docker compose up
```

This will:
- Build the Docker image (first time only)
- Install all Ruby dependencies
- Start the Jekyll server
- Watch for file changes and rebuild automatically

### 3. Access Your Website

Once you see output like:
```
Server address: http://0.0.0.0:4000
Server running... press ctrl-c to stop.
```

Open your browser and visit:
- **http://localhost:4000**

## Common Commands

### Run in Background (Detached Mode)

To run the container in the background and free up your terminal:

```bash
docker compose up -d
```

### View Logs

If running in detached mode, view the logs:

```bash
docker compose logs -f
```

Press `Ctrl+C` to stop viewing logs (container keeps running).

### Check Running Containers

See if your container is running:

```bash
docker compose ps
```

Or use Docker's native command:

```bash
docker ps
```

### Stop the Project

#### If running in foreground:
Press `Ctrl+C` in the terminal where it's running

#### If running in background (detached mode):
```bash
docker compose down
```

### Stop and Remove Everything (Clean Slate)

Stop containers and remove volumes:

```bash
docker compose down -v
```

### Rebuild After Changes

If you modify the Dockerfile or Gemfile:

```bash
docker compose up --build
```

Or rebuild without starting:

```bash
docker compose build
```

## Troubleshooting

### Port Already in Use

If port 4000 is already in use, you'll see an error. To find and kill the process:

**On macOS/Linux:**
```bash
lsof -ti:4000 | xargs kill -9
```

**Or change the port in docker-compose.yaml:**
```yaml
ports: [ 4001:4000 ]
```
Then access via http://localhost:4001

### Permission Issues

If you encounter permission errors:

```bash
chmod -R 777 .
```

### Container Won't Start

View detailed logs:

```bash
docker compose logs
```

### Start Fresh

Remove all containers, images, and rebuild:

```bash
docker compose down
docker compose build --no-cache
docker compose up
```

## Advanced Usage

### Execute Commands Inside Container

Run Jekyll commands inside the running container:

```bash
docker compose exec jekyll-site bundle exec jekyll --version
```

### Shell Access

Access the container shell:

```bash
docker compose exec jekyll-site /bin/bash
```

### Update Dependencies

Update Ruby gems inside the container:

```bash
docker compose exec jekyll-site bundle update
```

## File Watching

The Docker setup includes file watching. When you edit files:
- Markdown files (.md)
- HTML files
- Configuration files (_config.yml)

Jekyll will automatically regenerate the site. Just refresh your browser!

**Note:** Changes to `_config.yml` or `_config_docker.yml` require restarting:
```bash
docker compose restart
```

## Complete Workflow

### Starting Your Day
```bash
# Start the project
docker compose up -d

# Check it's running
docker compose ps

# View logs if needed
docker compose logs -f
```

### Ending Your Day
```bash
# Stop the project
docker compose down
```

### Making Changes
1. Edit your files normally in your IDE/editor
2. Save changes
3. Wait a few seconds for Jekyll to rebuild
4. Refresh browser (http://localhost:4000)

### Checking Website Status

While the container is running:
- **Website:** http://localhost:4000
- **Container status:** `docker compose ps`
- **Live logs:** `docker compose logs -f`

## Quick Reference

| Command | Purpose |
|---------|---------|
| `docker compose up` | Start in foreground |
| `docker compose up -d` | Start in background |
| `docker compose down` | Stop and remove containers |
| `docker compose ps` | Check running status |
| `docker compose logs -f` | View live logs |
| `docker compose restart` | Restart containers |
| `docker compose build` | Rebuild image |
| `docker compose up --build` | Rebuild and start |
| `Ctrl+C` | Stop foreground process |

## Verification Steps

After running `docker compose up`, verify everything works:

1. ✅ Container is running: `docker compose ps`
2. ✅ No errors in logs: `docker compose logs`
3. ✅ Website loads: Open http://localhost:4000
4. ✅ Make a test edit to a .md file and verify auto-rebuild

## Summary

**To start working:**
```bash
docker compose up -d
```

**To stop working:**
```bash
docker compose down
```

**To view your site:**
```
http://localhost:4000
```

That's it! You're ready to develop your personal website.
