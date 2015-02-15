FROM dockerfile/rabbitmq
MAINTAINER Kyle Prager kprager@attensity.com

# add RabbitMQ plugins
RUN rabbitmq-plugins enable rabbitmq_mqtt rabbitmq_stomp rabbitmq_management  rabbitmq_management_agent rabbitmq_management_visualiser rabbitmq_federation rabbitmq_federation_management sockjs

# add config file and set permissions
ADD rabbitmq.config /etc/rabbitmq/

RUN chmod u+rw /etc/rabbitmq/rabbitmq.config

# add cookie for cluster and set permissions and ownership
ADD erlang.cookie /var/lib/rabbitmq/.erlang.cookie

RUN chown rabbitmq:rabbitmq /var/lib/rabbitmq/.erlang.cookie

RUN chmod 400 /var/lib/rabbitmq/.erlang.cookie

# add start script and set permissions
RUN mkdir /opt/rabbit

ADD startrabbit.sh /opt/rabbit/

RUN chmod a+x /opt/rabbit/startrabbit.sh

# Expose all necessary ports
EXPOSE 5672
EXPOSE 15672
EXPOSE 25672
EXPOSE 4369
EXPOSE 9100
EXPOSE 9101
EXPOSE 9102
EXPOSE 9103
EXPOSE 9104
EXPOSE 9105

CMD /opt/rabbit/startrabbit.sh
