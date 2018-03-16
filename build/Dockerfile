
FROM debian:stretch-slim

RUN apt-get update \
    && apt-get install --assume-yes --quiet --no-install-recommends \
      curl ca-certificates clang

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    APP_HOME=/app \
    APP_USER=rustuser \
    PATH=/usr/local/cargo/bin:$PATH

WORKDIR $APP_HOME

RUN useradd -s /bin/bash -d $APP_HOME -M $APP_USER \
    && chown -R $APP_USER $APP_HOME \
    && curl https://sh.rustup.rs > /tmp/rustinit.sh \
    && bash /tmp/rustinit.sh -y --no-modify-path \
    && rm /tmp/rustinit.sh

USER $APP_USER

CMD ["/bin/bash"]

