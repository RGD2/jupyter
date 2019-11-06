BootStrap: docker
From: continuumio/anaconda3

%runscript

     echo "Starting notebook..."
     echo "Open browser to localhost:8888"
     exec /opt/conda/bin/jupyter lab --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root

%post

     apt-get update
     apt-get install -y apt-utils curl software-properties-common tmux python3-pip git vim-nox

     # install node
     curl -sL https://deb.nodesource.com/setup_12.x  | bash -
     apt-get -y install nodejs

     # install yarn
     curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
     apt update && apt install -y yarn
     yarn --version
     node --version
     npm --version

     # Install jupyter notebook
     python3 -m pip install --upgrade pip
     python3 -m pip install jupyter_contrib_nbextensions
     python3 -m pip install jupyterlab
     python3 -m pip install jupyterlab-git
     python3 -m pip install ipywidgets
     python3 -m pip install ipympl 
     python3 -m pip install matplotlib
     python3 -m pip install pandas

     # jupyterlab extenstions
     jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build
     jupyter labextension install @jupyterlab/toc --no-build
     jupyter labextension install @krassowski/jupyterlab_go_to_definition --no-build
     jupyter labextension install jupyterlab-drawio --no-build
     jupyter labextension install @ryantam626/jupyterlab_sublime --no-build
     jupyter labextension install @lckr/jupyterlab_variableinspector --no-build
     jupyter labextension install @jupyterlab/git --no-build
     jupyter labextension install jupyter-matplotlib --no-build
     jupyter lab clean
     jupyter lab build --minimize=False

     mkdir /opt/notebooks
     apt-get autoremove -y
     apt-get clean
