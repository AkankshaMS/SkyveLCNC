# Creates the minimum environment to package and run this Skyve application.
# Note that this uses an in-memory database and is only useful for demonstration/development.
FROM bizhubaustralia/skyve-wildfly-mysql

ENV LANG en_US.UTF-8

USER root
RUN mkdir /content
RUN chown jboss:jboss /content

USER jboss
ADD LCNC.war /opt/jboss/wildfly/standalone/deployments/LCNC.war
ADD LCNC.json /opt/jboss/wildfly/standalone/deployments
ADD LCNC-ds.xml /opt/jboss/wildfly/standalone/deployments
RUN touch /opt/jboss/wildfly/standalone/deployments/LCNC.war.dodeploy

ENV SKYVE_CONTENT='/content/' \
    SKYVE_DATASTORE_DIALECT='org.skyve.impl.persistence.hibernate.dialect.MySQL56InnoDBSpatialDialect' \
    DATABASE_URL='LCNC_db' \
    SKYVE_SECURITY_DOMAIN_NAME='LCNC' \
    SKYVE_JNDI_NAME='LCNCDB'

ENTRYPOINT [ "entrypoint.sh" ]