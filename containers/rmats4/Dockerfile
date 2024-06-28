# continuumio/miniconda3:24.5.0-0
FROM continuumio/miniconda3:24.5.0-0

LABEL authors="phil@lifebit.ai laura.urbanski@jax.org mike.lloyd@jax.org" \
	description="Docker image containing rMATS v4.3.0"

RUN conda install -c conda-forge mamba -y

COPY environment.yml /
RUN apt-get update && apt-get install -y procps && \
	mamba env create -f /environment.yml && conda clean -a

# Make RUN commands use the new environment:
RUN echo "conda activate rmats4" >> ~/.bashrc
SHELL ["/bin/bash", "--login", "-c"]

ENV PATH /opt/conda/envs/rmats4/bin:$PATH
