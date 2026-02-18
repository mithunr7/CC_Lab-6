FROM ubuntu:22.04

RUN apt-get update && apt-get install -y python3

WORKDIR /app

RUN cat > server.py << 'EOF'
import os
from http.server import BaseHTTPRequestHandler, HTTPServer

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header("Content-type", "text/plain")
        self.end_headers()
        self.wfile.write(f"Served by backend: {os.uname().nodename}".encode())

HTTPServer(("0.0.0.0", 80), Handler).serve_forever()
EOF

CMD ["python3", "server.py"]
