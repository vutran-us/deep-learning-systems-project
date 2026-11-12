# CIFAR-10 CNN capstone

Udacity AI Mastery Capstone: Deep Learning Systems. The experiment compares two Adam learning rates for the same CIFAR-10 CNN over eight epochs.

| Metric | Baseline (0.001) | Experiment (0.0003) |
|---|---:|---:|
| Test accuracy | 70.40% | 63.18% |
| Test macro F1 | 0.7008 | 0.6303 |
| Final train minus validation accuracy | +5.06 pp | −0.05 pp |

## Set up the environment

The recorded run used Ubuntu 26.04 on Linux x86_64, Python 3.14.4, PyTorch 2.15.0 with CUDA 13.2, and an NVIDIA RTX A3000. Use Python 3.14 to install the frozen requirements. If you already have the project files, start at the virtual environment step from the project directory.

```bash
git clone https://github.com/vutran-us/deep-learning-systems-project.git && cd deep-learning-systems-project
python3.14 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

The frozen requirements include Linux CUDA wheels and will fail to install on macOS or Windows. On those platforms, create and activate a virtual environment, install a compatible build using the [PyTorch installation instructions](https://pytorch.org/get-started/locally/), then run `python -m pip install numpy matplotlib jupyterlab ipykernel`. The notebook can run on CPU.

## Download and extract CIFAR-10

The binary archive is about 162 MB. The Toronto server can be slow. One project download took about 21 minutes.

From the notebook directory, run the following on Linux. The checksum must report `OK` before extraction proceeds.

```bash
mkdir -p data &&
wget -O data/cifar-10-binary.tar.gz https://www.cs.toronto.edu/~kriz/cifar-10-binary.tar.gz &&
printf '%s\n' 'c32a1d4ab5d03f1284b67883e8d87530  data/cifar-10-binary.tar.gz' | md5sum -c - &&
tar -xzf data/cifar-10-binary.tar.gz -C data/ &&
test -f data/cifar-10-batches-bin/data_batch_1.bin
```

On macOS or Windows, you can also download the [binary archive](https://www.cs.toronto.edu/~kriz/cifar-10-binary.tar.gz) in your browser, verify its MD5 against the value above, and extract it into `data/`. The resulting path relative to the notebook must be `data/cifar-10-batches-bin/data_batch_1.bin`.

## Run the notebook

Launch JupyterLab from the activated environment with `python -m jupyter lab`. Open `deep_learning.ipynb`, select the project's Python kernel, and choose **Restart Kernel and Run All Cells**.

## Submission files

- `deep_learning.ipynb` contains the experiment, metrics, and plots.
- `module_summary.pdf` contains the capstone report.
- `requirements.txt` contains the frozen Linux dependencies.
- `data/` is downloaded separately and excluded from the submission. Keep it out of version control.
