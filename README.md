
---

##  sample.py,d,app.py

mkdir docker-app
cd docker-app


sample.py
print("Hello from Docker container!")


2)app.py (webserver code)

from http.server import SimpleHTTPRequestHandler, HTTPServer
PORT = 5020
class MyHandler(SimpleHTTPRequestHandler):
def do_GET(self):
self.send_response(200)
self.send_header("Content-type", "text/html")
self.end_headers()
self.wfile.write(b"<h1>Hello from Docker Python Container</h1>")
server = HTTPServer(("0.0.0.0", PORT), MyHandler)
print(f"Server running on port {PORT}...")
server.serve_forever()


Dockerfile for sample.py
Task 2 — Write the Dockerfile
Create a file named:
1) Dockerfile for sample.py
Add:



FROM python:3.9-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]


Dockerfile for app.py
FROM python:3.9-slim
WORKDIR /app
COPY app.py .
EXPOSE 5020
CMD ["python", "app.py"]

docker build -t my-python-app .
docker images
my-python-app
docker run my-python-app






Expected output of sample.py:
Hello from Docker container!

docker run -p 5000:5000 my-python-app1
Expected output of app.py:
Hello from Docker Python Container in web browser


