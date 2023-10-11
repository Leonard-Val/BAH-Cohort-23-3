FROM tomcat:latest
# RUN apt-get update
##PATH MAY BE CHANGED TO SOMETHING LIKE target/*war IF NECESSARY FOR GITACTIONS
COPY ./hohtrainingapp.war /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]
