FROM rockylinux:9

RUN dnf install -y wget epel-release && \
    dnf install -y sl

ENTRYPOINT ["sl","-l"]
CMD ["-F"]
