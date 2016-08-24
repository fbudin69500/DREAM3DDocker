FROM dream3d/sdk-ubuntu-16.04:latest
MAINTAINER DREAM3D Community

RUN mkdir /usr/src/DREAM3D
WORKDIR /usr/src/DREAM3D

ENV DREAM3D_VERSION 0cf7dd2dfe88c586d3ac43b3d36a11265ab94d5d
RUN git clone https://github.com/BlueQuartzSoftware/DREAM3D.git && \
  cd DREAM3D && \
  git checkout ${DREAM3D_VERSION}

ENV CMP_VERSION 5ec851ab3e9724c27fd4d3ad11c00e53d86c558b
RUN git clone https://github.com/BlueQuartzSoftware/CMP.git && \
  cd CMP && \
  git checkout ${CMP_VERSION}

ENV SIMPL_VERSION f8089037c6112bcb723198a293b02477632059de
RUN git clone https://github.com/BlueQuartzSoftware/SIMPL.git && \
  cd SIMPL && \
  git checkout ${SIMPL_VERSION}

ENV SIMPLView_VERSION 77f6009d5110f510bc47f7de89a63e2ca446819c
RUN git clone https://github.com/BlueQuartzSoftware/SIMPLView.git && \
  cd SIMPLView && \
  git checkout ${SIMPLView_VERSION}

ENV CXXFLAGS="-std=c++11 -Wall"
ENV CC="/usr/bin/clang"
ENV CXX="/usr/bin/clang++"

RUN mkdir DREAM3D-build-Release && \
  cd DREAM3D-build-Release && \
  cmake -C /usr/src/DREAM3D_SDK/DREAM3D_SDK.cmake \
    -G Ninja \
    -DCMAKE_BUILD_TYPE=Release \
    -DTBB_ARCH_PLATFORM:PATH=x86_64-linux-gnu \
    ../DREAM3D && \
  ninja

VOLUME /usr/src/DREAM3D

# The app to run in the x11vnc server
ENV APP /usr/src/DREAM3D/DREAM3D-build-Release/Bin/DREAM3D

