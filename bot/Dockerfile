# Get nodejs image
FROM node:12

# Install git
RUN apt-get update && apt-get -qy install git && apt-get -y install ffmpeg

# Add user tron
#RUN useradd -ms /sbin/nologin bot
#USER bot
USER root
#WORKDIR /home/bot/
WORKDIR /root/

# Clone the bot
RUN git clone https://github.com/TRX-0/Tron.git
# Install npm packages
#WORKDIR /home/bot/Tron/
WORKDIR /root/Tron/
RUN npm install &&  npm install discord.js

# Get auth and config
ADD auth.json .
ADD config.json .
#RUN chown bot:bot /home/bot/Tron/auth.json && chown bot:bot /home/bot/Tron/config.json

# Get entrypoint
COPY entrypoint.sh /
#RUN chown bot:bot /entrypoint.sh && 
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]