FROM python:3.10-slim

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libffi-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements.txt before modifying it
COPY requirements.txt .

# Ensure thriftpy is removed from requirements.txt
RUN sed -i '/thriftpy/d' requirements.txt

# Explicitly install thriftpy2 first
RUN pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir thriftpy2 \
    && pip install --no-cache-dir -r requirements.txt --no-deps

COPY . .

CMD ["python", "processor.py"]
