FROM	node:latest

WORKDIR /usr/app

COPY    ./init_server.sh /usr/app/

RUN		apt-get update \
		&& apt-get install -y dumb-init \
		&& npm install -g npm \
        && chmod 777 init_server.sh

ENTRYPOINT	["/usr/bin/dumb-init", "--"]

CMD		["sh", "init_server.sh"]