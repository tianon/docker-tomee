FROM java:6-jre

ENV PATH /usr/local/tomee/bin:$PATH
RUN mkdir -p /usr/local/tomee

WORKDIR /usr/local/tomee

RUN curl -SL http://www.apache.org/dist/tomee/KEYS -o KEYS \
	&& gpg --import KEYS

RUN curl -SL https://dist.apache.org/repos/dist/release/tomee/tomee-1.7.2/apache-tomee-1.7.2-jaxrs.tar.gz.asc -o tomee.tar.gz.asc

RUN curl -SL http://apache.rediris.es/tomee/tomee-1.7.2/apache-tomee-1.7.2-jaxrs.tar.gz -o tomee.tar.gz \
	&& tar -zxvf tomee.tar.gz  \
	&& gpg --verify tomee.tar.gz.asc tomee.tar.gz \
	&& mv apache-tomee-jaxrs-1.7.2/* /usr/local/tomee \
	&& rm -Rf apache-tomee-jaxrs-1.7.2 \
	&& rm bin/*.bat \
	&& rm tomee.tar.gz*


EXPOSE 8080
CMD ["catalina.sh", "run"]
