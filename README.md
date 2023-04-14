# Assignment 1 - Part 2: Model Evaluation

In this assignment, you will **evaluate NLP models with CheckList**.

Hopefully the assignment will help you:

- Get familiar with the basic programming environment setup for playing with NLP models locally.
- Get familiar with HuggingFace (retrieve models, datasets, call models).
- Get familiar with the concept of model evaluation (using CheckList).

## Steps for completing the assignment.

1. **Envoirnment setup.** Setup the virual Python environment so you can use the same version of Python. We recommend using [Conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html#before-you-start) :

   ```sh
   # create an environment named eval_env, under the version of python 3.7
   conda create --name eval_env python=3.7
   # start the environment.
   conda activate eval_env
   ```

2. **Install necessary packages.** You can also directly do `pip install -r requirements.txt`; we provide a step-by-step tour to show you the important packages (links are to their installation pages respectively): [HuggingFace Transformers](https://github.com/huggingface/transformers/blob/main/README.md#installation), [Pytorch](https://pytorch.org/get-started/locally/#start-locally), [Jupyter Notebook](https://jupyter.org/install), [CheckList](https://github.com/marcotcr/checklist), [SpaCy](https://spacy.io/).

   ```sh
   # You should make sure you are in the environment when installing packages.
   conda activate eval_env

   # Install Transformers from huggingface
   pip install transformers
   # also install datasets so you can use their data
   pip install datasets
   # Install Pytorch - the underlying deep learning infrustructure
   pip install torch

   # Install Juypyter Notebook, so you run different blocks of code interactively.
   # !! Make sure to use notebook, not juypterlab, as it may not be compatible with CheckList.
   pip install notebook

   # Finally, CheckList
   pip install checklist
   # use the right ipywidgets version
   pip install ipywidgets==7.5

   # These two lines help you use CheckList in Jupyter Notebook. You should still run them if you did `pip install -r requirements.txt`.

   jupyter nbextension install --py --sys-prefix checklist.viewer
   jupyter nbextension enable --py --sys-prefix checklist.viewer

   # make sure you can use SpaCy models.
   python -m spacy download en_core_web_sm
   ```

3. **Start the programming environment**

   ```sh
   # Make sure you are in the right environment
   conda activate eval_env
   # Assuming you have cloned this git repo:
   # git clone $GIT_REPO_URL
   # Make sure you are in the right folder
   cd $PATH_TO_YOUR_LOCAL_REPO
   # start the jupyter notebook
   jupyter notebook
   ```

4. **Start to complete the task in the notebook.** Visit `http://localhost:8888/notebooks/A1-Notebook.ipynb` so you can see your notebook. Follow its steps. Some tips:

   - Read the HuggingFace tutorial: [Quicktour](https://github.com/huggingface/notebooks/blob/main/transformers_doc/en/quicktour.ipynb) to get familiar with model and dataset loading.
   - Read the CheckList [readme and tutotirals](https://github.com/marcotcr/checklist) to understand how to use the package.
      - In particular, [this tutorial](https://github.com/marcotcr/checklist/blob/master/notebooks/tutorials/4.%20The%20CheckList%20process.ipynb) shows you how to run the Test Suite using Transformer pipelines, which is what you will be doing in your assignment.
   - _Task_: To build on the previous part of the assignment, we will use hate speech classification as the task.
   - _Model_: Select a popular and well-documented model for the task of hate speech classification on Hugging Face. Try their online inference API before downloading them (e.g. [this](https://huggingface.co/bert-base-cased)). If you do not have access to GPUs, try to select _small_ models on Huggingface -- check the size of `pytorch_model.bin` (e.g. [here](https://huggingface.co/distilbert-base-uncased-finetuned-sst-2-english/tree/main)). Smaller models are generally less accurate but will more efficient.

5. **Write a quick summary of your observations.** Fill in [A1-Summary.md](./A1-Summary.md).

## Deliverables

1. Make sure you have finished all of the steps, and have got the `.pkl` file that summarizes your evaluation results.
2. Rename `A1-Summary.md` to `A1-Summary-[firstlast].md` (e.g. `A1-Summary-janedoe.pkl`)
3. Similarly, rename `A1-Suite.pkl` to `A1-Suite-[firstlast].pkl` (e.g. `A1-Suite-janedoe.pkl`)
4. Create a zip file: `A1-[firstlast].zip`, that contains both `A1-Summary-[AndrewID].md` and `A1-Test-Suite-[AndrewID].pkl`.
5. Go back to Canvas, and submit `A1-[AndrewID].zip`.

## Grading:

- **0 point** if no submission.
- **60 points if you attemped the assignment without coding**. In this case, you will fill in the summary in Fill in [A1-Summary-No-Coding.md](./A1-Summary-No-Coding.md) by writing text descriptions of ten tests you'd want to run, rename the file to `A1-Summary-No-Coding-[firstlast].md`, and submit.
- **75 points if you wrote less than 10 tests.
- **90 points if you wrote at least 10 tests for a novel NLP task** (tasks that's not already included in the CheckList repo).

**The remaining 10 points will be based on the efficacy of your tests.

- We will rate each of your tests on a 1-5 scale: 1) not a bug, 2) minor bug, 3) bug worth investigating and fixing, 4) severe bug, model may not be fit for production, and 5) no model with this bug should be in production.
- You will receive 3 points if your total score is at least 15, 5 points if it is at least 21, 7 points if at least 27, and 10 points if at least 33.

## Acknowledgements.

This assignment is directly based on [the analogous course assignment for Sherry Wu's Human-Centered NLP course at CMU](https://www.cs.cmu.edu/~sherryw/courses/2023s-hcnlp.html). 
