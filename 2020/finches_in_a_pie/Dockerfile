FROM i386/ubuntu

RUN mkdir -p /srv/challenge
ADD . /srv/challenge/

RUN dpkg -i /srv/challenge/libssl1.1_1.1.0g-2ubuntu4_i386.deb
RUN dpkg -i /srv/challenge/libwrap0_7.6.q-27_i386.deb
RUN dpkg -i /srv/challenge/socat_1.7.3.2-2ubuntu2_i386.deb

RUN touch /srv/challenge/flag.txt
RUN echo "ractf{B4k1ng_4_p1E!}" > /srv/challenge/flag.txt

RUN chmod -R 755 /srv/challenge
RUN adduser --system --shell /bin/bash ractf

USER ractf
WORKDIR /srv/challenge


CMD ["socat", "-s", "tcp-l:5000,reuseaddr,fork", "exec:/srv/challenge/stolen_pie,stderr"]
