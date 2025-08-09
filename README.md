Neural Laplace HTE
==============================


The project is built with following Python libraries:
1. [Pytorch-Lightning](https://pytorch-lightning.readthedocs.io/en/latest/) - deep learning models
2. [Hydra](https://hydra.cc/docs/intro/) - simplified command line arguments management
3. [MlFlow](https://mlflow.org/) - experiments tracking

### Installations
First one needs to make the virtual environment and install all the requirements:
```console
pip3 install virtualenv
python3 -m virtualenv -p python3 --always-copy venv
source venv/bin/activate
pip3 install -r requirements.txt
```

## MlFlow Setup / Connection
To start an experiments server, run: 

`mlflow server --port=5000`

To access MlFLow web UI with all the experiments, connect via ssh:

`ssh -N -f -L localhost:5000:localhost:5000 <username>@<server-link>`

Then, one can go to local browser http://localhost:5000.

## Experiments
To replicate neural Laplace experiments, use this command:
```console
PYTHONPATH=. CUDA_VISIBLE_DEVICES=<devices> 
python3 runnables/train_enc_dec.py -m +dataset=cancer_sim +backbone=crn +backbone/crn_hparams/cancer_sim_grad_reverse=\'0\',\'1\',\'2\' ,\'3\', \'4\' exp.seed=5,7,42
```
