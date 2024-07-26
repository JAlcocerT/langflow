# Base Image
FROM python:3.10-slim

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    git \
    make && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Create a non-root user
RUN useradd -m -u 1000 user

# Set environment variables
ENV HOME=/home/user
ENV PATH=$HOME/.local/bin:$PATH

# Set the working directory
WORKDIR $HOME/app

# Copy application files
COPY . $HOME/app/
RUN chown -R user:user $HOME/app

# Install langflow
USER user
RUN pip install --user langflow==1.0.12 
#>=0.5.0

# Run the application
CMD ["python", "-m", "langflow", "--host", "0.0.0.0", "--port", "7860"]


#docker build -t langflow .
#podman build -t langflow .