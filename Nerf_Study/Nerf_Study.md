# what is Nerf?
Nerf proposes a new way to effectively represent and synthesize 3D scenes.
The method uses machine learning, specifically neural network models, to generate 3D scenes from 2D images.


## paper
https://arxiv.org/abs/2003.08934


# To-do
I used room data to try this out for the first time.

## Setting Up the Environment
1. built on Python = 3.7 using the Anaconda prompt on Windows 10. The graphics card used is an Nvidia RTX3060. 
2. After downloading the file, I installed reqirement.txt. 
The detailed requirement is as follows.
[
torch==1.11.0
torchvision>=0.9.1
imageio
imageio-ffmpeg
matplotlib
configargparse
tensorboard>=2.0
tqdm
opencv-python
]

3. For learning purposes, we configured CUDA as follows.
Configured with pytorch cuda 11.6.
torch +116, 
torchaudio +116, 
torchvision +116 
were all set to 11.6.

## solved Error
python run_nerf.py --config configs/room.txt
I ran the code for learning and got the following error.

An error occurred when the imread function of the imageio library received 'ignoregamma'. 
The error was resolved by removing the 'ignoregamma' argument from line 110 of load_llff.py. 

The code was modified as follows 
[
return imageio.imread(f, ignoregamma=True)
->>
return imageio.imread(f)
]

This removes ignoregamma=True and allows the file to be trained.

# Start training
<img width="978" alt="image" src="https://github.com/paulsung97/3D_myStudy/assets/63456050/01cfa364-6e1e-4830-b651-f5099faf08be">

The study took about 10 hours and 18 minutes. 
The end result is the following

<img width="978" alt="image" src="https://github.com/paulsung97/3D_myStudy/assets/63456050/93b2c8f0-daf7-4a35-b30f-637f476ee856">

[[TRAIN] Iter: 200000 Loss: 0.0008910191827453673 PSNR: 36.04010772705078]

<img width="978" alt="image" src="https://github.com/paulsung97/3D_myStudy/assets/63456050/1d95833d-9583-4fcc-9df2-d541e4e45bbf">


# This is the finished result.


https://github.com/paulsung97/3D_myStudy/assets/63456050/2ebb0f45-14ee-4686-82cb-783586a749da



