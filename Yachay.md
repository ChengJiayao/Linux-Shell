# Yachay
Here are some steps for quick use yachay:

1. Firstly, you can using your WUSTL Key ssh directly to yachay.seas.wustl.edu when on SEAS network or connected to the VPN.

2. The scheduler is SLURM; there's a short overview and link to more docs here: https://sites.wustl.edu/eitrc/home/seas-compute-cluster/
   You can write a script like:
   #!/bin/bash
   #SBATCH -p SEAS-Lab-Yeoh
   #SBATCH -J my_job_name
   #SBATCH --gres=gpu:GF1080TI:2

   echo I see GPUS: $CUDA_VISIBLE_DEVICES
   uname -a
   
   that will submit a job to your partition, which contains yachay, selecting 2 of the GPUs.
   When it runs, it outputs like so:

I see GPUS: 0,1
Linux yachay.seas.wustl.edu 3.10.0-862.11.6.el7.x86_64 #1 SMP Tue Aug 14 21:49:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
