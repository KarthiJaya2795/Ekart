# Use a base image
FROM openjdk:8u151-jdk-alpine3.7

# Create a non-root user and group
RUN addgroup -S myuser && adduser -S myuser -G myuser

# Set the working directory
ENV APP_HOME /usr/src/app

# Expose the port
EXPOSE 8070

# Copy the application JAR file into the container
COPY target/shopping-cart-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar

# Set the working directory for the container
WORKDIR $APP_HOME

# Change ownership of the app files to the non-root user
RUN chown -R myuser:myuser $APP_HOME

# Switch to the non-root user
USER myuser

# Set the entrypoint to run the Java application as the non-root user
ENTRYPOINT exec java -jar app.jar
