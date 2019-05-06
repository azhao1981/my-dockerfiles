FROM google/dart

WORKDIR /app

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV TZ=Asia/Shanghai

RUN set -x \
  && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime  \
  && echo "Asia/Shanghai" > /etc/timezone

ENV PUB_HOSTED_URL=https://pub.flutter-io.cn
ENV FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn

ADD pubspec.* /app/
RUN pub get
ADD . /app
RUN pub get --offline
EXPOSE 8080

CMD []
ENTRYPOINT ["/usr/bin/dart", "/app/bin/server.dart"]