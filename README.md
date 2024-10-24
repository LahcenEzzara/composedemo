# Docker Compose Flask & Redis App

This project demonstrates a simple Python web application built with Flask and Redis, using Docker Compose to set up a multi-container architecture.

## Project Structure

```
composedemo/
│
├── app.py                # Flask application
├── Dockerfile            # Dockerfile to build the web app
├── docker-compose.yml    # Docker Compose configuration
└── requirements.txt      # Python dependencies
```

## Prerequisites

- Docker installed on your machine.
- Docker Compose installed.

## Getting Started

Follow these steps to set up and run the project locally.

### 1. Clone the Repository
```bash
git clone https://github.com/LahcenEzzara/composedemo.git
cd composedemo
```

### 2. Define the Flask Application

The main Flask application logic is in `app.py`. It uses Redis to count the number of times the page has been accessed.

### 3. Define Dependencies

The `requirements.txt` file lists the necessary dependencies for the Flask app:
```
flask
redis
```

### 4. Build and Run the Containers

Use Docker Compose to build and run the application:
```bash
docker compose up
```

The application will be accessible at [http://localhost:8000](http://localhost:8000). Every time you refresh the page, the counter increments.

### 5. Stop the Application

To stop the running containers, use the following command:
```bash
docker compose down
```

## Updating the Application

The `docker-compose.yml` file includes a bind mount that allows live updates to the code. Any changes made to the `app.py` file will automatically apply to the running container without needing to rebuild the image.

If you modify the code, simply refresh the page to see the changes:
```python
return 'Hello from Docker! I was here {} times.\n'.format(count)
```

## File Descriptions

### `app.py`
A simple Flask application that connects to Redis to count the number of hits on the page.

### `Dockerfile`
Defines how to build the Docker image for the Flask application:
- Uses Python 3.7 Alpine.
- Installs necessary dependencies from `requirements.txt`.
- Exposes port 5000 for the Flask app to run.

### `docker-compose.yml`
Sets up two services:
- **web**: Runs the Flask application.
- **redis**: Uses the official Redis Alpine image.

### `requirements.txt`
Specifies the Python dependencies for the Flask app:
- `flask`
- `redis`

## Rebuild the Application

If you need to rebuild the application after making changes, you can do so with:
```bash
docker compose up --build
```

## License

This project is open source and available under the [MIT License](LICENSE).

---

Happy coding! 🎉