# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# NOTE: DO *NOT* EDIT THIS FILE.  IT IS GENERATED.
# PLEASE UPDATE Dockerfile.txt INSTEAD OF THIS FILE
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
FROM seleniarm/node-base:4.1.0-alpha-20211218
LABEL authors=SeleniumHQ,sj26,jamesmortensen

USER root

# Install Chromium Arm64
# RUN echo "deb http://http.us.debian.org/debian/ stable non-free contrib main" >> /etc/apt/sources.list \
RUN echo "deb http://ftp.hk.debian.org/debian/ sid main" >> /etc/apt/sources.list \
  && apt-get update -qqy \
  # && apt-get -qqy install chromium=89.0.4389.82-1 \
  # && apt-get -qqy install chromium=90.0.4430.212-1 \
  && apt-get -qqy install chromium=93.0.4577.82-1 \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

#=================================
# Chromium Launch Script Wrapper
#=================================
COPY wrap_chromium_binary /opt/bin/wrap_chromium_binary
RUN /opt/bin/wrap_chromium_binary

#============================================
# Chromium webdriver
#============================================
RUN apt-get update -qqy \
  && apt-get -qqy install chromium-driver \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

RUN echo "chromium" > /opt/selenium/browser_name

USER 1200

