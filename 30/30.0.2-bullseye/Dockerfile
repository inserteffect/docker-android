FROM inserteffect/android-build-tools:30.0.2-bullseye

ENV ANDROID_PLATFORM_VERSION=30

# Ruby and Bundler for fastlane
RUN apt-get update && apt-get install -y --no-install-recommends \
            gcc \
            g++ \
            make \
            git \
      && rm -rf /var/lib/apt/lists/*

RUN yes | sdkmanager "platforms;android-$ANDROID_PLATFORM_VERSION"

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
