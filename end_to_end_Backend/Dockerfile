# Step 1: Use official Python image as a base image
FROM python:3.9-slim

# Step 2: Set the working directory in the container
WORKDIR /app

# Step 3: Copy the requirements.txt file to the container
COPY requirements.txt /app/

# Step 4: Install dependencies from the requirements.txt file
RUN pip install --no-cache-dir -r requirements.txt

# Step 5: Copy the rest of the application files into the container
COPY . /app/

# Step 6: Expose port 5000 (default Flask port)
EXPOSE 5000

# Step 7: Set the environment variable for Flask
ENV FLASK_APP=app.py

# Step 8: Start the Flask app when the container runs
CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]

