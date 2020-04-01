# Copyright © 2018 Booz Allen Hamilton. All Rights Reserved.
# This software package is licensed under the Booz Allen Public License. The license can be found in the License file or at http://boozallen.github.io/licenses/bapl

FROM java:openjdk-8-jdk

# install node
RUN deb https://deb.nodesource.com/node_8.x/jessie/main && \
    curl --silent https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add - && \
    apt update && \
	install -y nodejs

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
