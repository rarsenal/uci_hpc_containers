FROM rarsenal/ghtf-jp-bulk-gp

MAINTAINER iychang@uci.edu

USER root

WORKDIR /bin
# Download TopHat2
RUN wget http://ccb.jhu.edu/software/tophat/downloads/tophat-2.0.14.Linux_x86_64.tar.gz
# Download Bowtie2
RUN wget --default-page=bowtie2-2.2.3-linux-x86_64.zip http://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.3/bowtie2-2.2.3-linux-x86_64.zip/
# Unzip the archive
RUN tar zxvf tophat-2.0.14.Linux_x86_64.tar.gz
# Remove the archive
RUN rm tophat-2.0.14.Linux_x86_64.tar.gz
# Unzip the archive
RUN unzip bowtie2-2.2.3-linux-x86_64.zip
# Remove the archive
RUN rm bowtie2-2.2.3-linux-x86_64.zip
# Working directory in Bowtie2
WORKDIR /bin/bowtie2-2.2.3
# Symbolic link from "bowtie" to "bowtie2"
RUN ln -s bowtie2 bowtie
# Change in PATH
ENV PATH $PATH:/bin/tophat-2.0.14.Linux_x86_64
ENV PATH $PATH:/bin/bowtie2-2.2.3
# Remove wget and unzip
#RUN apt-get purge --yes wget unzip

RUN conda create -n py27 python=2.7 anaconda

#RUN Rscript -e 'install.packages("dplyr")'

RUN Rscript -e 'install.packages("gplots")'

#RUN Rscript -e 'library(devtools)' \
#	-e 'install_github("cran/gplots")'

RUN conda install -c bioconda -c r samtools --override-channels

WORKDIR /bin
RUN wget http://cole-trapnell-lab.github.io/cufflinks/assets/downloads/cufflinks-2.2.1.Linux_x86_64.tar.gz
RUN tar -zxvf cufflinks-2.2.1.Linux_x86_64.tar.gz

# add cufflinks to path
ENV PATH /bin/cufflinks-2.2.1.Linux_x86_64:$PATH

# Cleanup
RUN rm -rf cufflinks-2.2.1.Linux_x86_64.tar.gz
RUN apt-get clean

RUN conda install --quiet --yes -c conda-forge jupyter_contrib_nbextensions && \
	conda clean -tipsy

RUN yes | pip install genepattern-notebook && \
    jupyter nbextension enable --py widgetsnbextension --sys-prefix && \
    jupyter nbextension install --py genepattern --sys-prefix && \
    jupyter nbextension enable --py genepattern --sys-prefix && \
    jupyter serverextension enable --py genepattern --sys-prefix && \
    jupyter nbextension install --py nbtools --sys-prefix && \
    jupyter nbextension enable --py nbtools --sys-prefix && \
    jupyter serverextension enable --py nbtools --sys-prefix

RUN pip install igv

RUN rm -rf /home/$NB_USER/.cache/yarn && \
    rm -rf /home/$NB_USER/.node-gyp && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

RUN jupyter nbextension install --py igv && \
    jupyter nbextension enable --py igv

USER $NB_USER

WORKDIR /home/$NB_USER
