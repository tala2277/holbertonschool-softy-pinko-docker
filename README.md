# Softy Pinko — Docker

My Docker project for Holberton School. I use Flask for the API and Nginx to serve the front-end, proxy requests and balance traffic between API containers.

## Tasks

| Folder | Description |
| --- | --- |
| `task0` | Build an Ubuntu image that prints `Hello, World!`. |
| `task1` | Run a Flask API on port 5252. |
| `task2` | Serve the Softy Pinko front-end with Nginx on port 9000. |
| `task3` | Connect the front-end to the API using AJAX and Flask-CORS. |
| `task4` | Run both services with Docker Compose. |
| `task5` | Route requests through an Nginx proxy on port 80. |
| `task6` | Run two API containers with round-robin load balancing. |

## Requirements

- Docker
- Docker Compose

The examples use `docker-compose` as in the task instructions. With the newer Compose plugin, use `docker compose` instead.

## Run the project

```sh
cd task6
docker-compose build
docker-compose up --scale back-end=2
```

Open [http://localhost](http://localhost). The page loads `Hello, World!` from `/api/hello` through the proxy.

To check requests reaching the two API containers:

```sh
docker-compose logs back-end
```

Stop the services:

```sh
docker-compose down
```

## Run earlier tasks

**Task 0**

```sh
cd task0
docker build -t softy-pinko:task0 .
docker run --rm softy-pinko:task0
```

**Task 1**

```sh
cd task1
docker build -t softy-pinko:task1 .
docker run --rm -p 5252:5252 softy-pinko:task1
```

Visit [http://localhost:5252/api/hello](http://localhost:5252/api/hello).

**Tasks 2 and 3**

From the task folder, build and run the back-end:

```sh
docker build -t softy-pinko-back-end ./back-end
docker run --rm -p 5252:5252 softy-pinko-back-end
```

In another terminal, from the same folder:

```sh
docker build -t softy-pinko-front-end ./front-end
docker run --rm -p 9000:9000 softy-pinko-front-end
```

Visit [http://localhost:9000](http://localhost:9000). Task 2 serves the static page; task 3 also loads the API message.

**Tasks 4 and 5**

From the task folder:

```sh
docker-compose up --build
```

Use port 9000 for task 4 and port 80 for task 5. In tasks 5 and 6, only the proxy publishes a host port.

Run one task at a time and stop its containers before starting another task that uses the same ports.

## Front-end source

The supplied [Softy Pinko front-end](https://github.com/atlas-school/softy-pinko-front-end) is included in each front-end folder. The template is by TemplateMo.

## Author

**Abeer Al-Saiari** — [@Abeerr0](https://github.com/Abeerr0)
