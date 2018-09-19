# Yachay
Here are some steps for quick use yachay:

1. Firstly, you can using your WUSTL Key ssh directly to yachay.seas.wustl.edu when on SEAS network or connected to the VPN.

2. The scheduler is SLURM; there's a short overview and link to more docs here: https://sites.wustl.edu/eitrc/home/seas-compute-cluster/
   
3. You can write a script like:
``` 
#!/bin/bash
#SBATCH -p SEAS-Lab-Yeoh
#SBATCH -J your_job_name
#SBATCH --gres=gpu:GF1080TI:2
 
echo I see GPUS: $CUDA_VISIBLE_DEVICES

module add seas-lab-yeoh

python3 test.py         

uname -a

```  
that script is selecting 2 GPUs to run a task in test.py, and will output information of GPUs

then, you can use 
`sbatch script_name.sh`

this command will submit a job to your partition and add slurm-XXX.out there
 
When it runs, you could use command: `less slurm-XXX.out`
it show the outputs of the task like so:

    I see GPUS: 0,1
    Linux yachay.seas.wustl.edu 3.10.0-862.11.6.el7.x86_64 #1 SMP Tue Aug 14 21:49:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

## miscellaneous
1. Each time you submit a job, do add `module add seas-lab-yeoh` (you could copy the script example, and just change the python3 test.py line there:) )
2. The script and the file it running should under same dirctory
3. You could use $squeue to check all the jobs we send to yachay
4. Yachay has 8 GPUs
5. Once you find your job is finished, you chould remove the slurm-XXX.out file
6. You can $kill the process if you do not want it
