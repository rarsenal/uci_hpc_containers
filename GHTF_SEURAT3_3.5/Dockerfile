FROM rocker/rstudio:3.5.1


MAINTAINER iychang@uci.edu

#setup R configs
#install libs needed for png 
RUN apt-get update && \
    apt-get -y install --fix-missing libhdf5-dev libtiff5-dev libgmp-dev libpng-dev texinfo texlive texlive-fonts-extra && \
    rm -rf /var/lib/apt/lists/*

#install R packages 1/3

#install R packages 2/3

#install R packages 3/3
RUN apt-get update
RUN apt-get install -y libcurl4-openssl-dev
RUN apt-get install -y libssl-dev
RUN R -e "install.packages('devtools')"

RUN Rscript -e "devtools::install_github(repo = 'satijalab/seurat', ref = 'release/3.0')"

# download conda
RUN ["/bin/bash", "-c", "wget http://repo.continuum.io/miniconda/Miniconda-latest-Linux-x86_64.sh -O $HOME/miniconda.sh"]
RUN chmod 0755 $HOME/miniconda.sh
RUN apt-get update && \
    apt-get -y install --fix-missing bzip2
RUN ["/bin/bash", "-c", "$HOME/miniconda.sh -b -p $HOME/conda"]
ENV PATH="$HOME/conda/bin:$PATH"
RUN rm $HOME/miniconda.sh

# update conda
RUN conda update conda
RUN conda install conda-build
