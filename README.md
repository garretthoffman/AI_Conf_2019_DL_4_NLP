# AI_Conf_2019_DL_4_NLP
Slides and Code Tutorials for AIConf NY Tutorial on Deep Learning Methodologies for Natural Language Processing

## Notes

You can access the ULMFiT Notebook on [Google Colab](https://colab.research.google.com/drive/1Q5lUfTt3WIj4K9VNiMyEFk82gGerZk05)

For a code sample of RNNs with Attention check out [Taming Recurrent Neural Networks for Better Summarization](http://www.abigailsee.com/2017/04/16/taming-rnns-for-better-summarization.html) with links to the accompanying tensorflow implementation.

## Setup

### Download via Git

1. Go to your home directory by opening your terminal and entering `cd ~`

2. Clone the repository by entering

    ```
    git clone https://github.com/GarrettHoffman/AI_Conf_2019_DL_4_NLP
    ```

### Download Twitter GloVe Vectors

Download the pre-trained Twitter GloVe word vectors from [here](https://nlp.stanford.edu/projects/glove/) and place the file `glove.twitter.27B.50d.txt` in the `data` directory.

### Setup Virtual Environment
	
#### Option 1: Dockerfiles (Recommended)

3. After cloning the repo to your machine, enter

    ```
    docker build -t ai_conf_nlp_<image_type> -f ./dockerfiles/Dockerfile.<image_type> ./dockerfiles/
    ```

    where `<image_type>` is either `gpu` or `cpu`. (Note that, in order to run these files on your GPU, you'll need to have a compatible GPU, with drivers installed and configured properly [as described in TensorFlow's documentation](https://www.tensorflow.org/install/).)

4. Run the Docker image by entering

    ```
    docker run -it -p 8888:8888 -v <path to repo>:/root ai_conf_nlp_<image_type>
    ```

    where `<image_type>` is either `gpu` or `cpu`, depending on the image you built in the last step.

5. After building, starting, and attaching to the appropriate Docker container, run the provided Jupyter notebooks by entering

    ```
    jupyter notebook --ip 0.0.0.0 --allow-root
    ```

    and navigate to the specified URL `http://0.0.0.0:8888/?token=<JUPYTER NOTEBOOK ACCESS TOKEN>` in your browser.
    
6. Choose `0X_Notebook_Title.ipynb` to open the applicable Notebook.
	
###### Debugging docker
If you receive an error of the form:

```
WARNING: Error loading config file:/home/rp/.docker/config.json - stat /home/rp/.docker/config.json: permission denied
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.26/images/json: dial unix /var/run/docker.sock: connect: permission denied
```

It's most likely because you installed Docker using sudo permissions with a packet manager such as `brew` or `apt-get`. To solve this `permission denied` simply run docker with `sudo` (ie. run `docker` commands with `sudo docker <command and options>` instead of just `docker <command and options>`).

#### Option 2: Local setup using Miniconda

If you don't have or don't want to use Docker, you can follow these steps to setup the notebook.

3. Install miniconda using [one of the installers and the miniconda installation instructions](https://conda.io/miniconda.html). Use Python3.6.

4. After the installation, create a new virtual environment, using this command.
	```
	$ conda create -n strata_nlp
	$ source activate venv
	```
   
5. You are now in a virtual environment. Next up, [install TensorFlow by following the instructions](https://www.tensorflow.org/install/).

6. To install the rest of the dependenies, navigate into your repository and run 

	```
	$ pip install -r dockerfiles/requirements.txt
	```
   
7. Now you can run 

	```
	jupyter notebook
	```
	
	to finally start up the notebook. A browser should open automatically. If not, navigate to [http://127.0.0.1:8888](http://127.0.0.1:8888) in your browser. 
	
8. Choose `0X_Notebook_Title.ipynb` to open the applicable Notebook. to open the Notebook. Note: The ULMFiT Notebook will not run in the container, this must be run on Google Colab
