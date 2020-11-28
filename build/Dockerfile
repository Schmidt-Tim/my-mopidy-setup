FROM balenalib/rpi-raspbian:buster-20201118

RUN apt-get update \
 && apt-get install -y wget \
                       gnupg2 \
 && wget -q -O - https://apt.mopidy.com/mopidy.gpg | apt-key add - \
 && wget -q -O /etc/apt/sources.list.d/mopidy.list https://apt.mopidy.com/buster.list

RUN apt-get update \
 && apt-get install -y libffi-dev \
                       libxml2-dev \
                       libxslt1-dev \
                       zlib1g-dev \
                       build-essential \
                       gstreamer1.0-alsa \
                       gstreamer1.0-plugins-bad \
                       gstreamer1.0-plugins-good \
                       gstreamer1.0-plugins-ugly \
                       python3-dbus \
                       python3-dev \
                       python3-gst-1.0 \
                       python3-lxml \
                       python3-pip \
                       python3-setuptools \
                       python3-wheel \
                       libasound2-dev \
                       libspotify-dev \
                       dleyna-server \
                       git \
 && rm -rf /var/lib/apt/lists/*

# pip install requirements
COPY requirements.txt requirements.txt

RUN pip3 install -r requirements.txt \
 && rm -rf ~/.cache/pip

# refresh certs
RUN update-ca-certificates --fresh


ENV TZ=Europe/Berlin

ENTRYPOINT ["mopidy"]
