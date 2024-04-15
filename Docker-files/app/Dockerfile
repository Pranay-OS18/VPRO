FROM openjdk:11 AS BUILD_IMAGE
RUN apt-get update && apt-get install maven -y
RUN git clone https://github.com/Pranay-OS18/VPRO.git
RUN cd VPRO && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE VPRO/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
