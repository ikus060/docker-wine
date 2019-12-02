FROM buildpack-deps:stretch

ENV DEBIAN_FRONTEND noninteractive

# wine settings
ENV WINEPREFIX /wine-prefix/
ENV WINEARCH   win32
ENV WINEDEBUG  fixme-all

RUN set -x \
    && dpkg --add-architecture i386 && apt-get update && apt-get install -y --no-install-recommends wine wine32 xvfb xauth cabextract winbind fonts-wine ca-certificates \
    && apt-get clean \
    && wget -nv -O /usr/local/bin/winetricks 'https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks' \
    && chmod +x /usr/local/bin/winetricks \
    && wineboot -u
