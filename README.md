# d16


Experiment 16: Creating Docker Images using Dockerfile
Tasks: Write Dockerfile, build and run image.
Outcome: Application containerization.


1. Simple Python App (app.py)
print("Hello from Docker Container!")


# Use official Python image
FROM python:3.10

# Set working directory inside container
WORKDIR /app

# Copy the Python file into the container
COPY app.py .

# Run the Python script
CMD ["python", "app.py"]


def greet(name):
    return "Hello " + name

print(greet("Docker"))


docker build -t my-python-app .
docker run my-python-app
