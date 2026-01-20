# SPDX-License-Identifier: LGPL-3.0-or-later
# Copyright (C) 2022 Intel Corporation

FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime
COPY input.jpg ./
COPY classes.txt ./
COPY alexnet-pretrained.pt ./
COPY pytorchexample.py ./
USER root
CMD [" "]
RUN apt-get update -y \ 
 && apt-get install -y curl
RUN mkdir -p /etc/apt/keyrings
RUN curl -fsSL https://download.01.org/intel-sgx/sgx_repo/ubuntu/intel-sgx-deb.key \
    -o /etc/apt/keyrings/intel-sgx-keyring.gpg
RUN echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/intel-sgx-keyring.gpg] https://download.01.org/intel-sgx/sgx_repo/ubuntu jammy main" \
    > /etc/apt/sources.list.d/intel-sgx.list

RUN apt-get update && apt-get install -y \
    libsgx-enclave-common-dev \
    libsgx-dcap-ql-dev \
    libsgx-dcap-default-qpl-dev \
    tee-appraisal-tool


ENTRYPOINT ["python3", "pytorchexample.py"]
