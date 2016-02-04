FROM centos

RUN yum update -y
RUN groupadd vmail -g 2222
RUN useradd vmail -r -g 2222 -u 2222 -d /var/vmail -m -c "mail user"
RUN yum remove -y exim sendmail
RUN yum install postfix cronie -y
RUN yum install vim -y
RUN yum install dovecot -y
RUN yum install git -y
RUN git clone https://github.com/tomegathericon/Mail-Server.git
RUN rm -rf /etc/postfix
RUN rm -rf /etc/dovecot
RUN rsync -avhP Mail-Server/postfix /etc/
RUN rsync -avhP Mail-Server/dovecot /etc/
RUN chkconfig postfix on
RUN chkconfig dovecot on
RUN /usr/sbin/postfix start
RUN /usr/sbin/dovecot 
RUN rm -rf Mail-Server
EXPOSE 143 25 80

