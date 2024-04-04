# Chatroom App

This is a simple chatroom app where users can sign up using a username and password, log in, post messages in the chatroom, and interact with messages by liking or disliking them.

## Requirements
- Python 3.10 or higher
- Docker
- Node.js

## Database Setup

1. Create a Docker Volume:
    ```docker volume create mongodb_data_volume```

2. Deploy MongoDB Docker container:
    ```docker run -d -p 27017:27017 -v mongodb_data_volume:/data/db --name mongodb mongo```

## Server Setup

1. Navigate to the server folder:
    ```cd server```

2. Install requirements from requirements.txt:
    ```pip install -r requirements.txt```

3. Run the server code:
    ```gunicorn -w 1 -b 0.0.0.0:8080 wsgi:app```

## Client Setup

1. Navigate to the client folder:
    ```cd client```

2. Run the client code:
    ```npm start```

3. Access the app at [http://localhost:3000](http://localhost:3000)

### Docker Deployment

1. Create Docker Volume if not already created:
    ```docker volume create mongodb_data_volume```

2. Run the docker compose command:
    ```docker-compose up --build```

3. Access the app at [http://localhost:3000](http://localhost:3000)

### Kubernetes Deployment

1. Start Minikube:
    ```minikube start```

2. Configure Minikube to use local Docker images:
    ```eval $(minikube docker-env)```

3. Build the Docker images:
    ```docker-compose build```

4. Deploy server, client, and database:
    ```kubectl apply -f Kubernetes```

5. Forward the client port:
    ```kubectl port-forward deployment/client-deployment 3000 8080```

6. Access the app at [http://localhost:3000](http://localhost:3000)
