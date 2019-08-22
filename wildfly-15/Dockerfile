FROM jboss/wildfly

RUN mkdir -p /opt/jboss/wildfly/modules/com/tramada/lib/main
COPY picasso-lib.zip /opt/jboss/wildfly/modules/com/tramada/lib/main/
RUN unzip /opt/jboss/wildfly/modules/com/tramada/lib/main/picasso-lib.zip
RUN rm /opt/jboss/wildfly/modules/com/tramada/lib/main/picasso-lib.zip

ADD standalone.conf /opt/jboss/wildfly/bin/
ADD standalone.xml /opt/jboss/wildfly/standalone/configuration/
ADD Tramada.war /opt/jboss/wildfly/standalone/deployments/

USER jboss

RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#70365 --silent
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0", "-c", "standalone.xml", "--debug", "*:8787"]