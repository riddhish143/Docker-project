FROM nginx
LABEL "Project"="Application"
LABEL "Author"="Riddhish"
# Remove the default nginx configuration file
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copy your custom nginx configuration file into the container
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf
