### Why?
I wanted to try out TensorFlow using a Jupyter Notebook, using the [standard Docker image](http://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-tensorflow-notebook), with an ephemeral container, but bind-mounting a work directory on my local machine so my work persists across runs.
These days, that means pulling a fresh token from the startup logs and dropping it into your browser, every run. [Lots of folks seem upset](https://github.com/jupyter/notebook/issues/2254) that this isn't easier to achieve.

_NOTE: this is for "quick start/test drive" purposes only and is NOT RECOMMENDED for other uses, as the maintainers repeatedly explain in the issue._

### How?
Here's the incantation that I'm using:
```bash
docker run --rm -p 8888:8888 -d \
  --name tensorflow_tokenless \
  -v $HOME/tensorflow/work:/home/jovyan/work \
  jupyter/tensorflow-notebook start-notebook.sh --NotebookApp.token=''
```

Which you can tear down (saving your work but not the container) like so:
```bash
docker stop tensorflow_tokenless
```
