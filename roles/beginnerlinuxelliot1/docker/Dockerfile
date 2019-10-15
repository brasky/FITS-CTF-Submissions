FROM ubuntu:18.04

RUN apt-get update && apt-get install -y openssh-server sudo
RUN mkdir /var/run/sshd
RUN useradd -m -d /home/myUser myUser
RUN echo 'myUser:myPassword123' | chpasswd
RUN usermod -s /bin/bash myUser

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

RUN touch /home/myUser/catme.txt
RUN echo "flag{beginnerlinuxelliot1}" >> /home/myUser/catme.txt
RUN chown root:root /home/myUser/catme.txt
RUN chmod 400 /home/myUser/catme.txt
RUN echo 'myUser ALL=NOPASSWD: /bin/cat, /usr/bin/whoami' >> /etc/sudoers