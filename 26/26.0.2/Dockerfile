FROM inserteffect/android-build-tools:26.0.2
MAINTAINER Philip Graf <philip.graf@insfx.com>

ENV ANDROID_PLATFORM_VERSION=26

# Ruby for fastlane
RUN apt-get update && apt-get install -y --no-install-recommends \
            ruby \
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
