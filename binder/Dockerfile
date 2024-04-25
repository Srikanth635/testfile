# FROM intel4coro/base-notebook:20.04-noetic-full-xpra
FROM intel4coro/base-notebook:20.04-noetic

#------------------------------------------rasa38 Conda Env (Python 3.8) for rasa packages------------------------------------------

USER root

RUN conda create -n rasa38 python=3.8 && echo "conda activate rasa38" >> ~/.bashrc

SHELL ["conda", "run", "-n", "rasa38", "/bin/bash", "-c"]

RUN pip install rasa && pip install rasa[spacy] && pip install transformers && pip install nltk

RUN python -m spacy download en_core_web_sm && python -m nltk.downloader punkt && python -m nltk.downloader wordnet

# Initiate RASA workspace 
COPY --chown=${NB_USER}:users binder/rasa.sh /home/${NB_USER}/rasa.sh
RUN chmod +x /home/${NB_USER}/rasa.sh

ENV RASA_WS=/home/${NB_USER}/workspace/rasa
WORKDIR ${RASA_WS}/src
COPY --chown=${NB_USER}:users binder/rasa ${RASA_WS}/src/
RUN chmod -R a+rwx ${PWD}
# SHELL ["conda", "run", "-n", "rasa38", "/bin/bash", "-c"]

#------------------------------------------Switch to base Conda Env (Python 3.10)------------------------------------------



#---------------------------------------------------------------------------------------------------------------------

RUN pip install --upgrade \
  sidecar \
  Cython \
  openai \
  jupyterlab-git \
  jupyterlab-unfold \
  jupyter-archive \
  jupyterlab-search-replace \
  jupyter-offlinenotebook \
  jupyter-collaboration \
  jupyter-ai \
  jupyterlab-language-pack-de-DE  \
  jupyterlab_execute_time

RUN pip install --upgrade \
  jupyter-collaboration \
  openai \
  jupyter-ai

WORKDIR /home/${NB_USER}/bootstrapping_giskard/
