FROM bioconductor/release_base2

MAINTAINER iychang@uci.edu

#setup R configs
#install libs needed for biomaRt 
RUN apt-get update && \
    apt-get -y install --fix-missing libxml2-dev && \
    rm -rf /var/lib/apt/lists/*


#install R packages
RUN Rscript -e "source('https://bioconductor.org/biocLite.R')" && \
    Rscript -e "biocLite('biomaRt')" && \
    Rscript -e "biocLite('SWATH2stats')" && \
    echo "r <- getOption('repos'); r['CRAN'] <- 'http://cran.us.r-project.org'; options(repos = r);" > ~/.Rprofile && \
    Rscript -e "install.packages('devtools')" && \
    Rscript -e "install.packages('ggplot2', dependencies=TRUE)" && \
    Rscript -e "install.packages('ggrepel', dependencies=TRUE)" && \
    Rscript -e "install.packages('dplyr', dependencies=TRUE)" && \
    Rscript -e "install.packages('stringr', dependencies=TRUE)" && \
    Rscript -e "install.packages('qcc', dependencies=TRUE)" && \
    Rscript -e "install.packages('data.table', dependencies=TRUE)" && \
    Rscript -e "install.packages('reshape2', dependencies=TRUE)"
