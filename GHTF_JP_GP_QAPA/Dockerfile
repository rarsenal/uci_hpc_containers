FROM rarsenal/ghtf-jpy-gp-rbulk-3.5

MAINTAINER iychang@uci.edu

USER root

RUN cd /tmp  && \
	wget https://github.com/arq5x/bedtools2/releases/download/v2.27.0/bedtools-2.27.0.tar.gz && \
	tar -zxvf bedtools-2.27.0.tar.gz && \
	cd bedtools2 && \
	make && \
	make install

RUN cd /tmp && \
	git clone https://github.com/morrislab/qapa.git && \
	cd qapa && \
	R -e 'install.packages(c("optparse", "dplyr", "data.table", "stringr"))' && \
	python setup.py install

USER $NB_USER
