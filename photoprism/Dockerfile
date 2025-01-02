# Start from the official PhotoPrism image
FROM photoprism/photoprism:latest

# Update the system and install necessary libraries
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ffmpeg \
    libheif1 \
    libheif-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Optional: Ensure the container can process HEIC files
RUN ffmpeg -codecs | grep heif || echo "HEIC codec missing"
