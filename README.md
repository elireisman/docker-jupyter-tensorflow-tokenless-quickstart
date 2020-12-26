### Why?
Try out TensorFlow using a Jupyter Notebook using the [standard Docker image](http://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-tensorflow-notebook) with an ephemeral container, bind-mounting in a work directory.

_NOTE: this isn't a good idea, just handy for a quick test drive


### How?
Here's the setup:
```bash
docker pull jupyter/tensorflow-notebook

mkdir -p $HOME/tensorflow/work
```

Create the container
```bash
docker run --rm -p 8888:8888 -d \
  --name tensorflow_tokenless \
  -v $HOME/tensorflow/work:/home/jovyan/work \
  jupyter/tensorflow-notebook start-notebook.sh --NotebookApp.token=''
```

Kill & delete the container
```bash
docker stop tensorflow_tokenless
```
