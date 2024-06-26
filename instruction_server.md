<p align="center">
  <img src="https://media.giphy.com/media/U7nYAGksLRanU3i4vp/giphy-downsized-large.gif" alt="" />
</p>
<h1 align="center">:fire:LOBOT Cluster Instruction:fire:</h1>
<p align="center">
  <a href="#"><img src="http://hits.dwyl.io/L1NNA/Information.svg" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/github/issues/L1NNA/Information.svg?style=flat-square" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/badge/badges-awesome-green.svg?style=flat-square&color=brightgreen" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/github/license/Naereen/StrapDown.js.svg?style=flat-square&color=brightgreen" alt="" /></a>
</p>
<p align="center">
  <span>Contributors: Aaron Visser</span>
</p>



# Introduction
This is a tutorial for using the Queen's School of Computing  GPU computing cluster (known as Lobot).  It currently contains 13 hosts(nodes) of varing performance, hosting 118TB of storage, 2.4TB of memory, 1900 cpu cores and 65 NVIDIA GPUs. GPUs being hosted range from A16s, RTX5000, RTX6000, RTX6000-ada, A40s, and A100s.  Lobot is ideal for performing GPU-intensive computing tasks that wouldn't be possible on your local machine.  Before you begin, please read the Queen's policy on [Acceptable Use of Information Technology Resources](https://www.queensu.ca/secretariat/policies/senate/electronic-information-security-policy-framework/acceptable-use-information).
# Important Links and Resources

- [Server Access](https://lobot.caslab.queensu.ca/)
- [Jupyter Lab Docs](https://jupyterlab.readthedocs.io/en/latest/)
- [Jupyter Notebook Docs](https://jupyter-notebook.readthedocs.io/en/stable/)
- [Bash Introduction](https://programminghistorian.org/en/lessons/intro-to-bash)
- [VSCode Introduction](https://code.visualstudio.com/docs/introvideos/basics)
- [Conda Docs](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html)
- [Conda Cheatsheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)
- [Tensorflow Guide](https://www.tensorflow.org/guide)
- [PyTorch Guide](https://pytorch.org/docs/stable/index.html)

# Table of Contents:

- [Initialization](#initialization)
- [Termination](#termination)
- [JupyterLab](#jupyterlab)
- [Co-Pilot](#co-pilot)
- [VS Code](#vs-code)
- [VS Code Remote Tunnel](#vs-code-remote-tunnel)
- [GPU & Python Packages](#gpu-and-python-packages)
- [Conda Environments](#conda-environments)

# Initialization
Access to Lobot is gained through github credentials and being a member of the Queen's School of Computing Github Organization. After you accept the organization invite, you can access the cluster by logging in at https://lobot.caslab.queensu.ca/

Once you have connected your GitHub to the server you will now see the Hub Control Panel. The Hub Control Panel is where you can initialize or terminate your session. 

### Allocating Server Resources
Before you can begin using your the server you must first specify the resources you need.
This is a shared resource, so only take what you think you’ll need. If the resources aren’t available, you won’t be able to start your server until they get freed up again. Start with the minimum resources and see how performance is, if you feel you need more. Stop your workload and start it again with more cores/memory/gpu.

![image](https://user-images.githubusercontent.com/25777239/92413172-dbf70a00-f11c-11ea-8fc7-2b22fd881824.png)

On your first startup of the server you will be allocated 10G of storage. These 10G will always be yours, so there is no need to worry about your work not being saved when you terminate your session.  If you ever require more storage contact the server host.
# Termination

![image](https://user-images.githubusercontent.com/25777239/92413201-fdf08c80-f11c-11ea-9f9c-702bfbdf4902.png)

**\*IMPORTANT!\*** Closing your JupyterLab tab will not  end your session and free up resources.  You must go to File -> Hub Control Panel, then in the new tab click the "Stop My Server" button.  All your files on the server will be automatically saved upon ending a session.
### Server Life cycle
After 24 hours of inactivity your session will be terminated.  All your files will be automatically saved to your allocated storage.


# JupyterLab

Once you have completed server initialization you will be connected to JupyterLab through the server.

![image](https://user-images.githubusercontent.com/25777239/92413219-152f7a00-f11d-11ea-8be6-8688cac65986.png)

From the JupyterLab launcher you can easily create a Jupyter Notebook, console, terminal window, or VS Code instance.  To re-open the launcher go to File -> New Launcher or type (⌘ / Ctrl) + Shift + L.

## Co Pilot
I've received two recurring requests recently, one is for Github Copilot and the other is Remote VSCode. 

Regarding Copilot, this is available to every verified educational user, just visit https://education.github.com/discount_requests/application and fill out an application. Please note, it may take several days for the verification to take place.

## VS Code

![image](https://user-images.githubusercontent.com/25777239/92413231-1d87b500-f11d-11ea-8d07-889b2b0532c8.png)

VS Code on the server works exactly like a local version, this includes the ability to add extensions.  Your extensions and settings will be automatically saved in your server storage when your connection is terminated.

## VS Code Remote Tunnel
Setting up VSCode remote tunnel to access your cluster resources
*DRAFT*
Some background documentation:
https://code.visualstudio.com/docs/remote/tunnels
https://marketplace.visualstudio.com/items?itemName=ms-vscode.remoteserver

Spawn a workload with the most recent image.
Note: Older images may not have the components necessary to authenticate with GitHub)
Launch remote desktop. If you select VS Code from the jupyter desktop it will not support a tunnel.
In remote desktop, launch the browser (chrome) and navigate to
https://code.visualstudio.com/docs/?dv=linux64_deb
(you can just search for vscode download and select the .deb version)
Once it’s downloaded, open a terminal and type
```
sudo dpkg –i ~/Downloads/code_1_88.0***.deb
```
(whatever the file version is) And now you can launch vs code.
VSCode will remember its settings, and although you will have to reinstall it if you power off or reboot your workload, at least the settings and tunnel connection is already done for you.

Sign into GitHub and then turn on remote tunnel access.

Now you can open your VS Code on your local machine, sign into GitHub and click the bottom left hand icon to bring up the menu to connect to tunnel.
Select GitHub as the account used. And then pick the gpu cluster workload

You are now connected to the remote workload. Files are saved on your  cluster instance. You can drag and drop files to the directory and do all the normal things.

Remember that you have to have vscode open in the remote desktop session for the tunnel to be active.

### Extensions & Themes
Here are some helpful extensions and themes that will make your time with VS Code more enjoyable. Go to the extensions tab on the leftmost column of VS Code to input these extensions for download.

+ ```ms-python.python``` - Python package (Highly recommended)
+ ```eamodio.gitlens``` - GitHub extension (Highly recommended)
+ ```streetsidesoftware.code-spell-checker``` - Code spell checker
+  ```christian-kohler.path-intellisense``` - Path autocomplete
+ ```esbenp.prettier-vscode``` - Code formatter 
+ ```vscodevim.vim``` - Vim extension 


These are some themes that you can install to personalize your VS Code:

+ ```onecrayon.theme-quietlight-vsc``` - light theme with a bit more color than VS Code default light theme
+ ```eliverlara.andromeda ``` - Dark theme
+  ```robbowen.synthwave-vscode``` - Matches Cyberdeck aesthetic 

Shortcut for changing your current theme:  ```CTRL+K CTRL+T```


# GPU and Python Packages

### GPU

To check if the GPUs are actually avaiable, you can open a terminal and issue:
```
nvidia-smi
```
This will show the utilization status of the attached GPU devices. If you want to keep monitoring the utilization, you can type:
```
nvidia-smi -i
```

### Tensorflow and PyTorch

Tensor flow and PyTorch are both part of the base python environment on the server. To ensure that both packages are correctly installed you can test a Python import statement.  Note that after creating a new Conda environment, installing Tensorflow and PyTorch is required.

```
import tensorflow
tensorflow.__version__
```

to ensure Tensorflow has been installed, and 
```
import torch
torch.__version__
```
to ensure Pytorch has been installed.

If both snippets return a version number then that package has been correctly installed.

### Other Packages

The server comes with a default python environment that is not in Conda.  This is the one that will be used in the JupyterLab terminal by default.  If you install a package into this environment it will be saved in the `~/.local` directory.  This means that any packages you install here will also persist through a server restart.  
```
~$ pip install --user pytest  
~$ ls .local/lib/python3.7/site-packages/  
magic.py  __pycache__  pytest  _pytest  pytest-6.0.1.dist-info  python_magic-0.4.18.dist-info
```

# Conda Environments
By default, all your new conda environments will be saved into your home folder. So that will be persisted even if you stop/restart your server. Before you activate an environment, you need to create it.
[Source](https://saturncloud.io/blog/how-to-use-conda-environment-in-a-jupyter-notebook/)
```
# to view existing envs
$ conda info --envs

# to create a new environment
$ conda create -n yourenvname python=3.9
```

To activate an environment in JupyterLab terminal, you can:
```
# conda activate doesn't work in jupyter notebooks
$ source activate yourenvname 
```
This is the **ONLY** way it will work with the JupyterLab web terminal. 

### Linking Conda Environments to Python
After creating a new Conda environment, you can create a quick-link on the JupyterLab launcher to create a Python terminal with the new Conda environment.  First, activate your new Conda environment.  Then install `ipykernel` into that new environment.  Finally create a new kernel :

```
$ source activate yourenvname
# now you can create links in the jupyter launcher
(yourenvname)$ conda install ipykernel
(yourenvname)$ ipython kernel install --user --name=mykernelnamehere
(yourenvname)$ conda deactivate
```
Now, the a notebook for the new kernel should appear in your JupyterLab launcher after restarting JupyterLab.

![EnvironmentTutorial](https://user-images.githubusercontent.com/25777239/92413251-385a2980-f11d-11ea-95dc-bf666647be53.jpg)

[Source](https://stackoverflow.com/questions/53004311/how-to-add-conda-environment-to-jupyter-lab)



### Removing an added Environment
If you decide you no longer want a Conda environment simply deleting it should remove the linked Jupyter notebook launcher.  It it persists, however, you can type 
`jupyter kernelspec list`
into the JupyterLab console to list avaliable kernels and remove the unwanted one with `jupyter kernelspec uninstall unwanted-kernel`

[Source](https://stackoverflow.com/questions/42635310/remove-kernel-on-jupyter-notebook)

### Accessing Conda from terminal

To access Conda directly from your terminal you can input:

```source activate your_conda_env_here```

# Setting up an SSH Key
Setting up an SSH key for your Github will provide you both with security and quality of live benefits.
* With an SSH key you will no longer need to login to your Github account on that machine 
* The key is generated by a computer, making it much harder to crack than your normal human generated GitHub password :)

To setup an SSH key on p.l1nna simply follow these steps:

1. Open the terminal from the JupiterLab Launcher and run the command:
   

```
ssh-keygen -t rsa -b 4096 -C "GitHubaccEmailHere"
```
* This will generate an SSH key specifically for your email.

* Put a password on your ssh key when prompted.

2. Ensure that your SSH key has successfully generated 
```
ls .ssh/
```
The output should be:

```id_rsa  id_rsa.pub```

2. (b) Ensure that you have the correct credentials for your SSH key.
```
chmod 600 .ssh/id_rsa
```

3. Copy your SSH key to your clipboard by copying the output from the command:
   
```
cat .ssh/id_rsa.pub
```

4) Go to your GitHub account settings and add your newly generated SSH key to the SSH and GPG keys section.
![image](https://user-images.githubusercontent.com/25777235/95110565-34b1c680-070c-11eb-93bc-ef60c5f61d8f.png)
5) You're Done! You should now be able to run GitHub from JupiterLab without the need to login to your GitHub account.

## Cloning
From now on ensure that when you run a ```git clone``` command you copy the SSH link from the repository you are cloning. 
When asked if you want to continue connecting type ```yes```.

![image](https://user-images.githubusercontent.com/25777235/95110579-3c716b00-070c-11eb-8583-3cc6f06fecb0.png)


# Locally Installing Python Packages

If you install a python package normally it will be uninstalled when you end your server session.

To ensure that your python packages stay installed on your server account use ```--user``` when installing a package.

Example:
```
pip install --user pytest
```


###### 


