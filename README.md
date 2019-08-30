# beluga-how-to
Tutorial to use the Beluga comuting cloud. The compute canada team did an impressive job when documenting their server. The [doc](https://docs.computecanada.ca/wiki/Compute_Canada_Documentation) is very well written and complete, but can be intimidating when one wants to start a job for the first time. This README tries to summarize the information as brief as possible, but it is greatly recommended to follow the links and read more about the details of the servers.

### Preliminaries

**Modules**

More details [here](https://docs.computecanada.ca/wiki/Utiliser_des_modules/en)

- Beluga is a complex machinery, most programs are pre-installed by the server admins so that they are properly optimized for it. You should use these optimized programs over your manual installations.
- These pre-installed programs are called modules.
- The command line tool to interfere with the modules is called `module`.
- To load a module use `module load <program>`.
- To search a module use `module spider <prgram>`.
- To list all your loaded modules use `module list`.

**File systems**

More details [here](https://docs.computecanada.ca/wiki/B%C3%A9luga/en)

- `HOME`: small -> 50GB, 500K files per user. Backup daily. Suitable for code.
- `SCRATCH`: large -> 20TB, 1M files per user. Purge every 60 days!!! Suitable for temporary data.
- `PROJECT`: medium -> 1TB, 500K files  per *group*. Backup daily. Suitable for permanent data.

### Setting up the environment for PyTorch

More details [here](https://docs.computecanada.ca/wiki/PyTorch)

1. Make sure you are in your `HOME` by doing:
```bash
cd ~
```

2. Load the adequate modules:
```bash
module load python/3.7.0 # to have python, you can choose an other version
module load scipy-stack # to have python scientific libraries
module load cuda # to enable cuda for GPU computing
```
You should add these lines in your `.bashrc`to make sure they are loaded at every login:
```bash
echo \
"# Modules to load
module load python/3.7.0
module load scipy-stack
module load cuda" >> .bashrc
```

3. Create and activate a python virtual environment, more details [here](https://docs.computecanada.ca/wiki/Python#Creating_and_using_a_virtual_environment). In brief, this will encapsulate your pytorch installation from other possible libraries:
```bash
mkdir envs
virtualenv --no-download ~/envs/pytorch
source activate ~/envs/pytorch
```
To deactivate the environment you can at anytime execute:
```bash
deactivate
```

4. Update pip and install the beluga pytorch wheels (special optimized libraries):
```bash
pip install torch torchvision torchtext torchaudio --no-index
```









