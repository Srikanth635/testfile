# FROM intel4coro/base-notebook:20.04-noetic-full-xpra
FROM intel4coro/base-notebook:20.04-noetic

#------------------------------------------rasa38 Conda Env (Python 3.8) for rasa packages------------------------------------------

COPY --chown=${NB_USER}:users binder/rasa.sh /home/${NB_USER}/rasa.sh
RUN chmod +x /home/${NB_USER}/rasa.sh
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
