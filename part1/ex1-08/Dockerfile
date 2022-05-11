FROM ubuntu:20.04

RUN apt-get update && apt-get install -y curl

# Use /usr/src/app as our workdir. The following instructions will be executed in this location.
WORKDIR /usr/src/app

COPY curler.sh .

RUN chmod +x curler.sh

CMD ./curler.sh