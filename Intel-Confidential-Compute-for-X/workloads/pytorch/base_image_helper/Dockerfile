# SPDX-License-Identifier: LGPL-3.0-or-later
# Copyright (C) 2022 Intel Corporation

FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime
COPY input.jpg ./
COPY classes.txt ./
COPY alexnet-pretrained.pt ./
COPY pytorchexample.py ./
USER root
CMD [" "]
RUN echo "deb [signed-by=/etc/apt/keyrings/intel-sgx-keyring.asc arch=amd64] https://download.01.org/intel-sgx/sgx_repo/ubuntu jammy main" | sudo tee -a /etc/apt/sources.list.d/intel-sgx.list \
 && curl -fsSLO https://download.01.org/intel-sgx/sgx_repo/ubuntu/intel-sgx-deb.key \ 
 && sudo mv intel-sgx-deb.key /etc/apt/keyrings/intel-sgx-keyring.asc \
 && sudo apt-get install libsgx-enclave-common-dev \
    libsgx-dcap-ql-dev \
    libsgx-dcap-default-qpl-dev \
    tee-appraisal-tool

ENTRYPOINT ["python3", "pytorchexample.py"]
