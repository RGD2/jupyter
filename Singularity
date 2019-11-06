BootStrap: docker
From: continuumio/anaconda3

%runscript

     echo "Starting notebook..."
     echo "Open browser to localhost:8888"
     exec /opt/conda/bin/jupyter lab --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root

%post

     # Install jupyter notebook
     /opt/conda/bin/conda install jupyter -y --quiet
     /opt/conda/bin/conda install -c conda-forge jupyterlab -y --quiet 
     /opt/conda/bin/conda install -c conda-forge nodejs -y --quiet
     /opt/conda/bin/conda install -c conda-forge widgetsnbextension -y --quiet
     /opt/conda/bin/conda install -c conda-forge ipywidgets -y --quiet
     /opt/conda/bin/conda install ipympl -y --quiet
     /opt/conda/bin/jupyter nbextension enable --py widgetsnbextension
     mkdir /opt/notebooks
     apt-get autoremove -y
     apt-get clean
