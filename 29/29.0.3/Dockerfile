FROM ghcr.io/inserteffect/android-build-tools:29.0.3

ENV ANDROID_PLATFORM_VERSION=29
ENV BUNDLER_VERSION=2.0.2
ENV RUBYGEMS_VERSION=3.0.6

# Ruby and Bundler for fastlane
RUN apt-get update && apt-get install -y --no-install-recommends \
            gcc \
            g++ \
            make \
            ruby-dev \
      && rm -rf /var/lib/apt/lists/*

RUN gem update --system "$RUBYGEMS_VERSION" \
    && gem install bundler --version "$BUNDLER_VERSION" --force \
    && rm -r /root/.gem/

# install things globally, for great justice
# and don't create ".bundle" in all our apps
ENV GEM_HOME /usr/local/bundle
ENV BUNDLE_PATH="$GEM_HOME" \
  BUNDLE_BIN="$GEM_HOME/bin" \
  BUNDLE_SILENCE_ROOT_WARNING=1 \
  BUNDLE_APP_CONFIG="$GEM_HOME"

ENV PATH $BUNDLE_BIN:$PATH

RUN mkdir -p "$GEM_HOME" "$BUNDLE_BIN" \
  && chmod 777 "$GEM_HOME" "$BUNDLE_BIN"

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
