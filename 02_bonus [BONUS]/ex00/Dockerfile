FROM debian
RUN apt-get update &&  apt-get install -y curl gnupg2 nodejs vim git
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo \"deb https://dl.yarnpkg.com/debian/ stable main\" | tee /etc/apt/sources.list.d/yarn.
RUN apt-get update &&  apt-get install -y yarn
