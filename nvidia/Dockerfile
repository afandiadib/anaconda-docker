FROM nvidia/cudagl:9.2-devel-ubuntu18.04
MAINTAINER "Adib Afandi bin Abdullah <fendy90.oscura@gmail.com>"

RUN apt-get -y update && \
    apt-get -y install wget bzip2 libx11-6 libgl1-mesa-glx libglu1-mesa libxmu6 libxi6 libxcursor1 libgl1-mesa-dev && \
    wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    chmod +x Miniconda3-latest-Linux-x86_64.sh && \
    bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda && \
    
    #opencl from nvidia/opencl
    apt-get install -y --no-install-recommends ocl-icd-libopencl1 clinfo && \
    mkdir -p /etc/OpenCL/vendors && \
    echo "libnvidia-opencl.so.1" > /etc/OpenCL/vendors/nvidia.icd && \

    export PATH="/opt/conda/bin:$PATH" && \
    conda update -n base -c defaults conda && \
    conda install -y -c omnia openmm && \ 
    conda install -y -c omnia/label/betacuda92 openmm && \
    conda install -y -c anaconda scipy && \
    conda install -y -c anaconda jupyter && \
    conda install -y -c conda-forge matplotlib && \
    conda install -y -c openbabel openbabel && \
    conda install -y -c rdkit -c mordred-descriptor mordred && \
    conda update -y --all && conda clean -p -y && \

    apt-get -y purge wget bzip2 && \
    apt-get -y autoremove && apt-get -y clean && rm -rf /var/lib/apt/lists/* && \
    
    chmod -R 777 /opt

ENV PATH="/opt/conda/bin:$PATH"
