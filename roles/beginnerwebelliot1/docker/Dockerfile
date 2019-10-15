FROM ubuntu:18.04
ENV TZ=America/Los_Angeles
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update -q -y && apt-get install -q -y --no-install-recommends apache2 php openssh-server
RUN mkdir /var/run/sshd

EXPOSE 8002
RUN useradd -m -d /home/webserver webserver
COPY --chown=webserver:webserver entrypoint.sh /root/entrypoint.sh
COPY --chown=webserver:webserver 000-default.conf /etc/apache2/sites-available/000-default.conf
COPY --chown=webserver:webserver ports.conf /etc/apache2/ports.conf
ADD --chown=webserver:webserver web_content /var/www/html/
RUN chown -R www-data:www-data /var/www/html
RUN chmod -R 700 /var/www/html
RUN rm /var/www/html/index.html
ENTRYPOINT ["bash", "-c", "/root/entrypoint.sh"]
