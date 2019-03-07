FROM rarsenal/ghtf-jpy-rbase-3.5

USER root

MAINTAINER Ivan Chang (iychang@uci.edu)

# libav-tools for R and matplotlib anim
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    openjdk-8-jre &&  apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir /usr/src/myapp

COPY install/* /usr/src/myapp/

RUN cd /usr/src/myapp && \
	wget http://software.broadinstitute.org/cancer/software/genepattern/download_installer/installers/gp-3.9.10-153/Linux/NoVM/GPserver.bin && \
	chmod +x GPserver.bin && \
	PATH=$PATH:/usr/src/myapp && \
	./GPserver.bin -f install-gp.properties && \
	rm GPserver.bin && \
	fix-permissions /opt/genepattern

COPY resources/* /opt/genepattern/resources/

RUN chown -R jovyan:users /opt/genepattern

USER $NB_USER

ENV PATH="${PATH}:/opt/genepattern"

#RUN pip install git+https://github.com/rarsenal/nbgpserverproxy.git

#RUN jupyter serverextension enable --sys-prefix --py nbgpserverproxy
#RUN jupyter nbextension install    --sys-prefix --py nbgpserverproxy
#RUN jupyter nbextension enable     --sys-prefix --py nbgpserverproxy

