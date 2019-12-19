FROM buildpack-deps:buster

ARG WINE_VERSION=winehq-stable

ENV DEBIAN_FRONTEND noninteractive

# wine settings
ENV WINEPREFIX /wine-prefix/
ENV WINEARCH   win32
ENV WINEDEBUG  fixme-all

# we need wine for this all to work, so we'll use the PPA
RUN set -x \
    && dpkg --add-architecture i386 \
    && apt-get update -qy \
    && apt-get install --no-install-recommends -qfy gpg-agent apt-transport-https software-properties-common wget \
    && wget -nv https://dl.winehq.org/wine-builds/winehq.key \
    && apt-key add winehq.key \
    && rm winehq.key \
    && add-apt-repository 'https://dl.winehq.org/wine-builds/debian/' \
    && apt-get update -qy \
    && apt-get install --no-install-recommends -qfy $WINE_VERSION xvfb xauth cabextract winbind fonts-wine ca-certificates \
    && apt-get clean \
    && wget -nv -O /usr/local/bin/winetricks 'https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks' \
    && chmod +x /usr/local/bin/winetricks \
    && wineboot -u
