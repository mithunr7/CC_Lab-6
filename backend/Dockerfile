FROM python:3.10-slim

WORKDIR /app

RUN echo 'import os\nfrom http.server import BaseHTTPRequestHandler, HTTPServer\n\nclass Handler(BaseHTTPRequestHandler):\n    def do_GET(self):\n        self.send_response(200)\n        self.send_header(\"Content-type\", \"text/plain\")\n        self.end_headers()\n        hostname = os.uname().nodename\n        self.wfile.write(f\"Served by backend: {hostname}\".encode())\n\nHTTPServer((\"0.0.0.0\", 80), Handler).serve_forever()' > server.py

CMD ["python", "server.py"]
