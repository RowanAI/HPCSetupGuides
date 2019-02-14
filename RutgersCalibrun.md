ssh with your private key – no need for password

```
>>ssh username@caliburn.rdi2.rutgers.edu
```

Go to elf 
```
>>ssh elf 
```


Load python
```
>>module avail python
>>module load python/3.6.6
```

Load CUDA
```
module load cuda/9.0
```

Go to our project directory:

```
cd /gpfs/gpfs/project1/gr19002-001
```

Create your own working folder
```
mkdir mywork
```

Run interactive session of GPU
```
srun -N 1 --partition gpu --gres gpu:1 --qos gpu-award --pty bash
```
