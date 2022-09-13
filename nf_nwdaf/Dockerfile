FROM golang

LABEL description="Nwdaf module"

# Install all necessary software
RUN apt update \
    && apt install -y git make gcc g++ libsctp-dev libsctp-dev lksctp-tools iproute2 wget \
    && cd / \
    && apt update \
    && apt install git \
    && git clone https://gitlab.com/Paolort/nwdaf \
    && cd nf_nwdaf/ \
    && go mod download github.com/antonfisher/nested-logrus-formatter \
    && go mod tidy \
    && go build -o ./build/nwdaf ./cmd/

# Set working dir
WORKDIR /nwdaf
