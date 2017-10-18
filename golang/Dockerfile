# This is golang
# VERSION 1
# Author: wendyeq

FROM golang

MAINTAINER wendyeq wendyeq@gmail.com

# install require software
RUN apt-get update && apt-get install -y unzip vim pkg-config libaio1

RUN mkdir -p /usr/lib/oracle/10.1/client64/

ENV LD_LIBRARY_PATH /usr/lib:/usr/local/lib:/usr/lib/oracle/10.1/client64/
ENV NLS_LANG AMERICAN_AMERICA.AL32UTF8

COPY basic-10.2.0.5.0-linux-x64.zip /tmp/
COPY sdk-10.2.0.5.0-linux-x64.zip /tmp/
COPY sqlplus-10.2.0.5.0-linux-x64.zip /tmp/

COPY main.go /go


RUN cd /tmp && unzip basic-10.2.0.5.0-linux-x64.zip 
#RUN cp /tmp/instantclient_10_2/* /usr/lib/oracle/10.1/client64/

RUN cd /tmp && unzip sdk-10.2.0.5.0-linux-x64.zip
#RUN cp -R /tmp/instantclient_10_2/sdk/ /usr/lib/oracle/10.1/client64/ 

RUN cd /tmp && unzip sqlplus-10.2.0.5.0-linux-x64.zip 
RUN cp -R /tmp/instantclient_10_2/* /usr/lib/oracle/10.1/client64/

RUN ln -s /usr/lib/oracle/10.1/client64/libclntsh.so.10.1 /usr/lib/oracle/10.1/client64/libclntsh.so
RUN ln -s /usr/lib/oracle/10.1/client64/libocci.so.10.1 /usr/lib/oracle/10.1/client64/libocci.so

#RUN cd /usr/lib/pkgconfig/ && curl -o oci8.pc https://raw.githubusercontent.com/wendyeq/go-oci8/master/oci8.pc  

COPY oci8.pc /usr/lib/pkgconfig/

#RUN go get github.com/wendyeq/go-oci8
RUN go get github.com/gin-gonic/gin
RUN go get github.com/mattn/go-oci8
RUN go get gopkg.in/gin-contrib/cors.v1

RUN rm -rf /tmp/*



