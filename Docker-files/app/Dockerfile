FROM maven:3.9.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE 
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install 

FROM tomcat:10-jdk21
LABEL "project"="Vprofile"
LABEL "Author"="Pacifique"
RUN rm -rf /usr/local/tomcat/webapps/* 
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE  8080
CMD [ "catarina.sh","run"]