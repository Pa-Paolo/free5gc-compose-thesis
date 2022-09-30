FROM ubuntu:20.04

LABEL description="Device simulation module" 

# Install all necessary software
RUN apt update \
    && apt install -y git python3-pip \
    && cd / \
    && git clone https://github.com/Pa-Paolo/Thesis_code \
    && cd /Thesis_code/forecasting \
    && pip install -r requirements.txt

# Set working dir
WORKDIR /Thesis_code/forecasting
