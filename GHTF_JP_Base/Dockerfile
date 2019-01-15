FROM jupyter/r-notebook

USER root

RUN apt-get update && \
	apt-get install -y --no-install-recommends \
		libapparmor1 \
		libedit2 \
		lsb-release \ 
		libssl1.0.0 \
		psmisc \
		libcurl4-openssl-dev \
		;

# You can use rsession from rstudio's desktop package as well.
ENV RSTUDIO_PKG=rstudio-server-1.1.456-amd64.deb

RUN wget -q http://download2.rstudio.org/${RSTUDIO_PKG}
RUN dpkg -i ${RSTUDIO_PKG}
RUN rm ${RSTUDIO_PKG}

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

USER $NB_USER

RUN pip install git+https://github.com/jupyterhub/nbserverproxy.git
RUN jupyter serverextension enable --sys-prefix --py nbserverproxy

RUN pip install git+https://github.com/jupyterhub/nbrsessionproxy.git
RUN jupyter serverextension enable --sys-prefix --py nbrsessionproxy
RUN jupyter nbextension install    --sys-prefix --py nbrsessionproxy
RUN jupyter nbextension enable     --sys-prefix --py nbrsessionproxy

# The desktop package uses /usr/lib/rstudio/bin
ENV PATH="${PATH}:/usr/lib/rstudio-server/bin"
ENV LD_LIBRARY_PATH="/usr/lib/R/lib:/lib:/usr/lib/x86_64-linux-gnu:/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server:/opt/conda/lib/R/lib"

USER root

RUN apt-get update && \
    apt-get -y install --fix-missing libxml2-dev && \
    rm -rf /var/lib/apt/lists/*

USER $NB_USER

RUN conda install --yes \
	'libssh2' \
	'krb5' && \
	conda clean -tipsy

#install R packages
RUN Rscript -e "source('https://bioconductor.org/biocLite.R')" \
    -e "biocLite('biomaRt')" \
    -e "biocLite('SWATH2stats')"

RUN echo "r <- getOption('repos'); r['CRAN'] <- 'http://cran.us.r-project.org'; options(repos = r);" > ~/.Rprofile && \
    Rscript -e "install.packages('devtools')" \
    -e "install.packages('ggplot2', dependencies=TRUE)" \
    -e "install.packages('ggrepel', dependencies=TRUE)" \
    -e "install.packages('dplyr', dependencies=TRUE)" \
    -e "install.packages('stringr', dependencies=TRUE)" \
    -e "install.packages('qcc', dependencies=TRUE)" \
    -e "install.packages('data.table', dependencies=TRUE)" \
    -e "install.packages('reshape2', dependencies=TRUE)"

