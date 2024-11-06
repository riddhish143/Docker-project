# Use OpenJDK 11 as the base image for the build stage
FROM openjdk:11 AS BUILD_IMAGE

# Install Maven in the build stage
RUN apt update && apt install -y maven

# Clone the vprofile project repository
RUN git clone https://github.com/devopshydclub/vprofile-project.git

# Change to the project directory, checkout to the docker branch, and build the project
RUN cd vprofile-project && git checkout docker && mvn install

# Use Tomcat 9 with JRE 11 as the base image for the runtime stage
FROM tomcat:9-jre11

# Remove any default webapps in the Tomcat webapps directory
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the WAR file from the build stage into the Tomcat webapps directory
COPY --from=BUILD_IMAGE /vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Expose port 8080 for the Tomcat server
EXPOSE 8080

# Start Tomcat when the container runs
CMD ["catalina.sh", "run"]
