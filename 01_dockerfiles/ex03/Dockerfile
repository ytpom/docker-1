FROM debian:9
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y curl openssh-server ca-certificates postfix tzdata
RUN curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash 
RUN apt-get install -y gitlab-ce
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout gitlab.example.com.key \
	-out gitlab.example.com.crt \
	-subj "/C=RU/ST=Moscow/L=Moscow/O=42 School/OU=21 School/CN=jphilip-"
RUN mkdir -p /etc/gitlab/ssl && \
	chmod 700 /etc/gitlab/ssl && \
	mv gitlab.example.com.key gitlab.example.com.crt /etc/gitlab/ssl/
RUN sed -i "/external_url /s/'http\:\/\/gitlab.example.com'/'https\:\/\/gitlab.example.com'/" /etc/gitlab/gitlab.rb && \
	echo letsencrypt[\'enable\'] = false >> /etc/gitlab/gitlab.rb && \
	echo nginx[\'ssl_certificate\'] = \"/etc/gitlab/ssl/gitlab.example.com.crt\" >> /etc/gitlab/gitlab.rb && \
	echo nginx[\'ssl_certificate_key\'] = \"/etc/gitlab/ssl/gitlab.example.com.key\" >> /etc/gitlab/gitlab.rb
EXPOSE 80
EXPOSE 22
EXPOSE 443
ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && service ssh restart && tail -f /dev/null
