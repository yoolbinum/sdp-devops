# Copyright © 2018 Booz Allen Hamilton. All Rights Reserved.
# This software package is licensed under the Booz Allen Public License. The license can be found in the License file or at http://boozallen.github.io/licenses/bapl

FROM java:openjdk-8-jdk

# install node
if [ "x${DIST}" == "xprecise" ]; then
  RUN echo "Calling $0"
  RUN apt-get update
  RUN apt-get install -y clang-3.4
fi

if [ "x${DIST}" == "xwheezy" ]; then
  RUN echo "Calling $0"
  RUN apt-get update
  RUN apt-get -y install curl apt-transport-https ca-certificates
  RUN echo "deb https://deb.nodesource.com/clang-3.4 wheezy main" >> /etc/apt/sources.list
  RUN curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
  RUN apt-get update
  RUN apt-get install -y clang-3.4
fi

RUN npm install -g protractor gulp jasmine-spec-reporter && \
    webdriver-manager update && \
    apt-get update && \
    apt-get install -y xvfb wget && \
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && \
    dpkg --unpack google-chrome-stable_current_amd64.deb && \
    apt-get install -f -y && \
    apt-get clean && \
    rm google-chrome-stable_current_amd64.deb

# Install all npm packages from package.json
# RUN npm install

CMD /bin/bash
