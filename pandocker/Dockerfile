FROM debian:testing

# Install packages for pandoc and deploy
RUN apt-get update && apt-get install -y \
  texlive-full \
  pandoc \
  openssh-client \
  python3 \
  python3-pip \
  librsvg2-bin

# Configure ssh
RUN mkdir -p ~/.ssh && \
  eval $(ssh-agent -s) && \
  echo -e "Host *\n\tStrictHostKeyChecking no\n\n" > ~/.ssh/config

# Install pandocfilters via pip
RUN pip3 install pandocfilters

# Remove documentations
RUN apt-get --purge remove -y .\*-doc$

# remove unused stuff
RUN apt-get clean -y
