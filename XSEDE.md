# Setup access to the XSEDE System

XSEDE allows us to access other HPC's out there in the world. These instructions are for accessing the **BRIDGES** cluster.

If you already have a BRIDGES account, you may be able to skip to step 4.

## Connecting to BRIDGES

### 1. Create an account at [XSEDE](https://portal.xsede.org/my-xsede#/guest)
![
](https://i.imgur.com/1PTjDpt.png)

### 2. Register XSEDE with Duo

Once logged in, [go to the portal](https://portal.xsede.org/mfa#enroll) and enroll with Duo.

Fantastic... you should be all set up.

### 3. Connect to XSEDE

In a terminal window, type the following command:

```
$ ssh [username]@login.xsede.org
Please login to this system using your XSEDE username and password:

password:
```
Type in your **XSEDE Password**, then you will be prompted with a Duo Mobile authentication:
```
Duo two-factor login for [username]
Enter a passcode or select one of the following options:
1. Duo Push to XXX-XXX-1234
2. Phone call to XXX-XXX-1234
Passcode or option (1-2): 1
```

### 4. Connect to BRIDGES
Once you are connected to XSEDE, you can type:

```
$ gsissh bridges
Last login: Thu Jan 24 15:07:34 2019 from 150.250.5.23

********************************* W A R N I N G ********************************

You have connected to br018.pvt.bridges.psc.edu
```
to connect to the BRIDGES interface.

### 5. Testing BRIDGES Connectivity
Once you are in the BRIDGES system, you can run a test model by executing the following:

```
$ git clone https://github.com/grasool/testing-bridges
$ cd testing-bridges
$ interact --gpu
$ module avail tensorflow
$ module load keras/2.2.0_tf1.7_py3_gpu
$ source activate
$ python tf_test.py
$ python test_mnist.py
```

What just happened? Let's explain. First you cloned a github repository called **testing-bridges**. `interact --gpu` then was used to interact with the GPU directly.

`module avail tensorflow` showed you a list of all tensorflow versions / configurations that are available. `module load keras/2.2.0_tf1.7_py3_gpu` loaded the `keras` module using TensorFlow 1.7 for Python3.

`source activate` activates a Python3 Virtual Environment. Then the 2 python files are run. `tf_test.py` does a basic TensorFlow matrix multiplication. `test_mnist.py` trains a convolutional neural network on the MNIST dataset.

# Running SLURM
In real life, when running large models, you'll want to use something like Slurm. The Slurm Workload Manager, or Slurm, is a free and open-source job scheduler for Linux and Unix-like kernels, used by many of the world's supercomputers and computer clusters.

Once you are connected to BRIDGES, and have the `testing-bridges` repository cloned, you can run:

```
$ sbatch test_slurm.sh
```

slurm*.out file is created when the job starts.

To see the current output of the queue, you can type:
```
$ squeue -u [username]
```


# Helpful Reading
## GPU
### Resources

[https://psc.edu/bridges/user-guide/running-jobs](https://psc.edu/bridges/user-guide/running-jobs)  (Go to the end and see code  for the GPUs)

[https://ondemand.bridges.psc.edu/pun/sys/dashboard](https://ondemand.bridges.psc.edu/pun/sys/dashboard) (Use dashboard)

### Jupyter

[https://ondemand.bridges.psc.edu/pun/sys/dashboard](https://ondemand.bridges.psc.edu/pun/sys/dashboard)

[https://psc.edu/bridges/user-guide/ondemand#jupyterhub](https://psc.edu/bridges/user-guide/ondemand#jupyterhub)

## Slurm
https://www.rc.fas.harvard.edu/resources/documentation/convenient-slurm-commands/#Information_on_jobs
