# Get nodejs image
FROM node:12

# Install git
RUN apt-get update && apt-get -qy install git && apt-get -y install ffmpeg
USER root
WORKDIR /root/

# Clone the bot
RUN git clone https://github.com/TRX-0/Tron.git
# Install npm packages
WORKDIR /root/Tron/
RUN npm install &&  npm install discord.js

# Get auth and config
ADD auth.json .
ADD config.json .

# Get entrypoint
ADD entrypoint.sh /
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]