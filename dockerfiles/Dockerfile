FROM inseefrlab/onyxia-jupyter-python

USER root

RUN apt-get -y update && \
    apt-get -y install wget && \
    apt-get install -y git && \
    apt-get install build-essential -y && \
    rm -rf /var/lib/apt/lists/*
 
RUN apt-get -y update && \
    DEBIAN_FRONTEND=noninteractive apt install -y imagemagick

RUN which python

# Install graphviz
RUN wget https://raw.githubusercontent.com/linogaliana/python-datascientist/master/requirements.txt -O requirements.txt && \
    pip install -r requirements.txt && \
    wget https://raw.githubusercontent.com/linogaliana/python-datascientist/master/requirements.sh -O requirements.sh && \
    sudo apt-get update && \
    sudo apt install -y graphviz

RUN pip freeze 

RUN python -m spacy download en_core_web_sm
RUN python -m gensim.downloader --download glove-wiki-gigaword-200

EXPOSE 5000
CMD ["pip", "freeze"]
