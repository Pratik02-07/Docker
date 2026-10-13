# Base image (OS)
FROM python:3.14-slim

# Working directory
WORKDIR /app

# 1. Copy only the requirements first
COPY requirements.txt .

# 2. Install dependencies (Docker will cache this layer!)
RUN pip install -r requirements.txt

# 3. Copy the rest of your source code
COPY . .

# expose port 80``
EXPOSE 80

# serve the app / run the app (keep it running)

CMD ["python","run.py"]
