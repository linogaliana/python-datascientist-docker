FROM inseefrlab/onyxia-python-minimal

USER root

RUN apt-get -y update && \
    apt-get -y install wget && \
    apt-get install -y git && \
    apt-get install build-essential -y && \
    rm -rf /var/lib/apt/lists/*
 
RUN apt-get -y update && \
    DEBIAN_FRONTEND=noninteractive apt install -y imagemagick

# Install graphviz
RUN apt-get -y update && \
    apt-get install -y graphviz

# Create the environment:
COPY environment.yml .

RUN mamba env update -n base -f environment.yml && \
    # Clean
    rm environment.yml && \ 
    mamba clean --all -f -y && \
    rm -rf /var/lib/apt/lists/*

# Installation quarto
#ENV QUARTO_VERSION="1.4.176"
#RUN wget "https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb" && \
#    apt install "./quarto-${QUARTO_VERSION}-linux-amd64.deb" && \
#    rm -f "./quarto-${QUARTO_VERSION}-linux-amd64.deb"

RUN conda info --envs

# Install chrome
# RUN apt install chromium-browser


RUN python -m spacy download en_core_web_sm
RUN python -m gensim.downloader --download glove-wiki-gigaword-200

EXPOSE 5000
CMD ["pip", "freeze"]
