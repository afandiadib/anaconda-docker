FROM nvidia/cudagl:9.0-devel-ubuntu16.04
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
    conda install -y -c anaconda scipy && \
    conda install -y -c anaconda jupyter && \
    conda install -y -c conda-forge matplotlib && \
    conda install -y -c openbabel openbabel && \
    conda install -y -c rdkit -c mordred-descriptor mordred && \
    conda install -y -c ambermd pytraj && \
    
    #NGLView
    apt-get -y install --no-install-recommends git && \
    git clone https://github.com/arose/nglview && \
    cd nglview && \
    python setup.py install && \
   
    #pymol
    apt-get -y install libglew-dev freeglut3-dev libpng-dev libfreetype6-dev libxml2-dev libmsgpack-dev libglm-dev && \
    conda install -y -c conda-forge pmw && \
    conda install -y -c anaconda pyqt && \
    git clone https://github.com/schrodinger/pymol-open-source.git && \
    cd pymol-open-source && \
    python setup.py install --prefix=/opt/conda && \
    
    apt-get -y purge git wget && \
    apt-get -y autoremove && apt-get -y clean && rm -rf /var/lib/apt/lists/* && \
    conda update -y --all && conda clean -p -y && \
    
    rm -rf /pymol-open-source && \
    chmod -R 777 /opt
    
    
ENV PATH="/opt/conda/bin:$PATH"
