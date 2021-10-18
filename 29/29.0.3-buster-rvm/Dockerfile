FROM inserteffect/android-build-tools:29.0.3-buster

ENV ANDROID_PLATFORM_VERSION=29
ENV DEFAULT_RUBY_VERSION=2.7.2

# Ruby and Bundler for fastlane
RUN apt-get update && apt-get install -y --no-install-recommends \
            gcc \
            g++ \
            make \
            git \
            curl \
            openssl \
            procps \
      && rm -rf /var/lib/apt/lists/*

RUN yes | sdkmanager "platforms;android-$ANDROID_PLATFORM_VERSION"

RUN curl -L https://get.rvm.io | bash -s stable
ENV RVM_HOME /usr/local/rvm
RUN echo "source $RVM_HOME/scripts/rvm" >> /etc/bash.bashrc

RUN bash -l -c "rvm requirements \
                && rvm install $DEFAULT_RUBY_VERSION \
                && rvm --default use $DEFAULT_RUBY_VERSION"

ARG VERSION
ARG BUILD_DATE
ARG VCS_REF

LABEL org.label-schema.version=$VERSION
LABEL org.label-schema.build-date=$BUILD_DATE
LABEL org.label-schema.vcs-ref=$VCS_REF
LABEL org.label-schema.vcs-url="https://github.com/inserteffect/docker-android.git"
LABEL org.label-schema.name="Android Build"
LABEL org.label-schema.vendor="InsertEFFECT"
LABEL org.label-schema.schema-version="1.0"
LABEL org.opencontainers.image.authors="insertEFFECT <philip.graf@insfx.com>"
