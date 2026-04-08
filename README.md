
---

##  sample.py,d,app.py

```python
def greet(name):
    return "Hello " + name


from sample import greet

print("Hello from Docker Container!")
print(greet("Docker"))


# Use official Python image
FROM python:3.10

# Set working directory
WORKDIR /app

# Copy all files into container
COPY . .

# Run the application
CMD ["python", "app.py"]


docker build -t my-python-app .


docker run my-python-app
