# Use official base image with Python 3.11 and uv preinstalled
FROM ghcr.io/astral-sh/uv:python3.11-bookworm-slim

# Set working directory
WORKDIR /app

# Copy project files
COPY . .

# Optional: compile bytecode for performance
ENV UV_COMPILE_BYTECODE=1

# Install dependencies using uv (Flask is needed)
RUN uv pip install flask --system

# Expose the port your app runs on
EXPOSE 8002

# Run the app using uv utility
CMD ["uv", "run", "app.py"]
