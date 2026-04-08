
---

##  sample.py,d,app.py



from http.server import SimpleHTTPRequestHandler, HTTPServer

PORT = 5000

class MyHandler(SimpleHTTPRequestHandler):

    def do_GET(self):
        self.send_response(200)
        self.send_header("Content-type", "text/html")
        self.end_headers()

        message = "<h1>Hello from Docker Python App!</h1>"
        self.wfile.write(message.encode())

# Start server
server = HTTPServer(("", PORT), MyHandler)

print(f"Server running on port {PORT}")
server.serve_forever()









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



# Use Python base image
FROM python:3.10

# Set working directory
WORKDIR /app

# Copy all files
COPY . .

# Expose port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]


docker build -t my-python-web-app .
docker run -p 5000:5000 my-python-web-app



