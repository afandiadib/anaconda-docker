# Anaconda Container

My personalized miniconda package. Softwares included are for biomolecular dynamics studies. I used jupyter notebook most of the time and used ipython for automation.

To run jupyter notebook, I create a bash script as follow:

    #!/bin/bash

    port=$1

    if [ -z $port ]; then port=8888; fi

    echo
    echo port - $port
    echo

    docker run --rm --user=$(id -u) \
               --workdir=\`pwd\` \
               --volume=/home/$USER:/home/$USER \
               --volume=/media:/media \
               --volume=/mnt:/mnt \
               --volume=/etc/group:/etc/group:ro \
               --volume=/etc/passwd:/etc/passwd:ro \
               --volume=/etc/shadow:/etc/shadow:ro \
               --volume=/etc/sudoers.d:/etc/sudoers.d:ro \
               --publish $port:$port \
               afandiadib/conda:nvidia jupyter notebook --port=$port --no-browser --ip=0.0.0.0

To run ipython, I create an alias in .bashrc file: -

    alias ipython=docker run --rm --workdir=\`pwd\` --volume=\`pwd\`:\`pwd\` afandiadib/conda:nvidia ipython
