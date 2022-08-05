FROM ubuntu:20.04

RUN apt-get -y update && \
    apt-get -y install wget && \
    apt-get install -y git && \
    apt-get install build-essential -y && \
    rm -rf /var/lib/apt/lists/*
 
RUN apt-get -y update && \
    DEBIAN_FRONTEND=noninteractive apt install -y imagemagick

# Install recent go version
ENV GO_VERSION="1.18.4"
RUN wget https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz && \
    rm -rf /usr/local/go && \
    tar -C /usr/local -xzf go${GO_VERSION}.linux-amd64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

# Install hugo
ENV HUGO_VERSION="0.97.3" 
RUN wget https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.deb && \
    apt install "./hugo_extended_${HUGO_VERSION}_Linux-64bit.deb" && \
    rm -f hugo_extended_${HUGO_VERSION}_Linux-64bit.deb

# Install Miniconda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    bash Miniconda3-latest-Linux-x86_64.sh -b -p /miniconda && \
    rm -f Miniconda3-latest-Linux-x86_64.sh

# Make conda command available
ENV PATH="/miniconda/bin:${PATH}"

# Create the environment:
COPY environment.yml .

RUN conda install mamba -n base -c conda-forge && \
    mamba env create --force -q -n python-ENSAE --file environment.yml

# Installation quarto
ENV QUARTO_VERSION="1.0.37"
RUN wget "https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb" && \
    apt install "./quarto-${QUARTO_VERSION}-linux-amd64.deb" && \
    rm -f "./quarto-${QUARTO_VERSION}-linux-amd64.deb"

RUN conda info --envs

# Make Python interpreter from "monenv" available
ENV PATH="/miniconda/envs/python-ENSAE/bin:${PATH}"

# Install chrome
RUN apt-get install -y wget
RUN wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN apt-get install ./google-chrome-stable_current_amd64.deb


RUN python -m spacy download en_core_web_sm
RUN python -m gensim.downloader --download glove-wiki-gigaword-200

EXPOSE 5000
CMD ["pip", "freeze"]
