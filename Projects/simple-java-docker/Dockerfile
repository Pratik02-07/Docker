# pull a base image 
FROM eclipse-temurin:17-jdk-alpine

# working directory - folder where the application code will be copied to and compiled
WORKDIR /app

# Copy source code from the local machine into the container
COPY src/Main.java /app/Main.java

# Compile the Java code
RUN javac Main.java

# Run the Java application when the container starts
CMD ["java", "Main"]
