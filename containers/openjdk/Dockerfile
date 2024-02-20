ARG ALPINE_VERSION
FROM docker.io/alpine:${ALPINE_VERSION}
ARG JAVA_VERSION
RUN apk -U --no-progress upgrade \
 && apk --no-progress add bash openjdk${JAVA_VERSION}-jre-base
