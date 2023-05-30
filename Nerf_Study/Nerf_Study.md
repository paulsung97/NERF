# what is Nerf?
Nerf proposes a new way to effectively represent and synthesize 3D scenes.
The method uses machine learning, specifically neural network models, to generate 3D scenes from 2D images.


## paper
https://arxiv.org/abs/2003.08934


## To-do
I used room data to try this out for the first time.

## Setting Up the Environment
1. I built it on python = 3.7 using the anaconda prompt on Windows 10. 
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
