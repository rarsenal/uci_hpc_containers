FROM rarsenal/ghtf-jpy-gp-rbase-3.5

MAINTAINER iychang@uci.edu

RUN Rscript -e 'if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")'
RUN Rscript -e 'BiocManager::install("DESeq2", version = "3.8")'
RUN Rscript -e 'BiocManager::install("edgeR", version = "3.8")'
RUN Rscript -e 'BiocManager::install("limma", version = "3.8")'
RUN Rscript -e 'BiocManager::install("DEXSeq", version = "3.8")'
