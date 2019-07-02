Bootstrap: docker

From: continuumio/miniconda3


%files
    bw223.yml

%environment
    PATH=/opt/conda/envs/$(head -1  bw223.yml | cut -d' ' -f2)/bin:$PATH                # Change $PATH

%post
    echo "Creating a Singularity Container of my bw223 Conda Env"                # What I'm doing
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc                       # enable conda for the current
    echo "conda activate $(head -1  bw223.yml | cut -d' ' -f2)" >> ~/.bashrc            # will start "ngs3" conda env
    apt-get update && apt-get -y install nano tree htop wget build-essential            # Install
#   /opt/conda/bin/conda update -n base -c defaults conda                    # Update Conda
    /opt/conda/bin/conda env create -f bw223.yml                            # Conda create my env

%runscript
    exec "$@"

%labels
    Maintainer olivier.kirsh@u-paris.fr                                # Merci qui?
    Version v1.0 20190702
