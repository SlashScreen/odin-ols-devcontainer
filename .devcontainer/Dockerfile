FROM mcr.microsoft.com/devcontainers/base:alpine-3.20

# Build and install Odin
RUN sudo apk add llvm llvm-dev clang &&\
git clone --depth 1 https://github.com/odin-lang/Odin &&\
cd Odin &&\
git pull &&\
make release-native
ENV PATH="/Odin:${PATH}"

# Build and install OLS
# We have to build this because the prebuilt binary is linked against glibc and alpine uses musl
RUN cd / &&\
git clone --depth 1 https://github.com/DanielGavin/ols &&\
cd ols &&\
./build.sh &&\
./odinfmt.sh
ENV PATH="/ols:${PATH}"
