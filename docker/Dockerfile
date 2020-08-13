# Use Java 8 as base image
FROM openjdk:8

# Create a directory & set it as working directory
WORKDIR /opt/ignite

# Set IGNITE Version
ENV IGNITE_VERSION 2.8.1

# Download IGNITE package of specified version
RUN wget https://mirrors.estointernet.in/apache//ignite/2.8.1/apache-ignite-${IGNITE_VERSION}-bin.zip

# Install "unzip" utility
RUN apt-get update && apt-get install -y unzip

# Unzip the package downloaded
RUN unzip apache-ignite-${IGNITE_VERSION}-bin.zip

# Remove zip file
RUN rm apache-ignite-${IGNITE_VERSION}-bin.zip

# Copy custom configuration XML to INGITE config location
COPY ./custom_conf.xml /opt/ignite/apache-ignite-${IGNITE_VERSION}-bin/config

# Set IGNITE directory
ENV IGNITE /opt/ignite/apache-ignite-${IGNITE_VERSION}-bin

# Start the IGNITE 
CMD $IGNITE/bin/ignite.sh $IGNITE/config/custom_conf.xml

# Expose IGNITE ports
# 47100: communication SPI port
# 45000: node discovery SPI port
# 8080: REST port
# 10800: SQL port
EXPOSE 47100 45000 8080 10800
