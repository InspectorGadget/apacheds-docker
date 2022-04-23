#
# ApacheDS (Directory Service) for LDAP
# Default DN: uid=admin,ou=system
# Default Password: secret
#
# Maintainer: InspectorGadget <igadget28@gmail.com>
#

FROM openjdk:17-alpine

LABEL maintainer="InspectorGadget <igadget28@gmail.com>"
LABEL description="ApacheDS (Directory Service) for LDAP"
LABEL version="1.0"

# Add packages using 'apk'
RUN apk add --no-cache bash dcron openssl unzip wget

# Set command line utilities and install from Apache Distribution with AM25 version of the Package (Stable one)
RUN set -x && \
    wget -qO /apacheds.zip https://archive.apache.org/dist/directory/apacheds/dist/2.0.0.AM25/apacheds-2.0.0.AM25.zip && \
    mkdir -p /opt/apacheds && \
    unzip /apacheds.zip -d /opt/apacheds && \
    mv /opt/apacheds/apacheds-*/* /opt/apacheds/ && \
    rmdir /opt/apacheds/apacheds-*/ && \
    rm /apacheds.zip

WORKDIR /opt/apacheds

# Copy commands to directory
COPY /stop-container.sh /stop-container.sh
RUN chmod 744 /stop-container.sh

COPY /docker-cmd.sh /docker-cmd.sh
RUN chmod 744 /docker-cmd.sh

# Expose TCP Ports
EXPOSE 10389/tcp 10636/tcp

# Run CMD for server to startup. Script includes `tail` to keep container running
CMD ["/docker-cmd.sh"]