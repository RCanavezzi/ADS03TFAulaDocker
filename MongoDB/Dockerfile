FROM mongo:latest

# Set environment variables for MongoDB
ENV MONGO_INITDB_ROOT_USERNAME=admin
ENV MONGO_INITDB_ROOT_PASSWORD=adminpassword

# Expose the default MongoDB port
EXPOSE 27017

# Copy initialization scripts if needed (optional)
# COPY ./init-scripts /docker-entrypoint-initdb.d/