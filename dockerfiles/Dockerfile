FROM kalilinux/kali-rolling
LABEL org.opencontainers.image.authors="githubfoam"


#clean start
RUN apt-get update -y && apt-get upgrade -y && apt-get autoremove - && apt-get clean 

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections && \
    apt-get install -y kali-tools-forensics && \
    echo "########################### METAPACKAGE INFO ###########################" && \
    apt depends kali-tools-forensics  && \
    apt show kali-tools-forensics && \
    apt-cache show kali-tools-forensics | grep Depends && \
    echo "########################### METAPACKAGE INFO ###########################"


# custom packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    aircrack-ng \
    ncat  \
    tor  \    
    strace \
    ltrace \
    # https://github.com/danielmiessler/SecLists
    seclists \ 
    ansible \
    hping3

# custom git packages
# RUN apt-get update && \
#     #wa3f
#     apt-get install -y libssl-dev \
#     libxml2-dev \
#     libxslt1-dev \
#     zlib1g-dev \
#     python2-dev \
#     python2 \
#     python-dev-is-python3 \
#     # Package 'python-dev' has no installation candidate
#     # python-dev \
#     # Unable to locate package python-pybloomfiltermmap
#     # python-pybloomfiltermmap && \
#     git clone https://github.com/andresriancho/w3af.git /opt/w3af && \
#     /opt/w3af/w3af_console && \
#     bash /tmp/w3af_dependency_install.sh && \
#     echo 'export PATH=/opt/w3af:$PATH' >> /etc/profile

#testing
RUN hping3 -v

