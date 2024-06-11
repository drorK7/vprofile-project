FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cy vprofile-project && git checkout docker && mvn install
LABEL "Project" = "Vprofile"
LABEL "Author" = "Davek"
FROM tomat:9-jre11
RUN rm -rf /user/local/tomecat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomecat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]