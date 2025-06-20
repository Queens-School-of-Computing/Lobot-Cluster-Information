<p align="center">
  <img src="https://media1.tenor.com/m/e0PUiA9HF7gAAAAd/star-wars.gif" alt="" />
</p>
<h1 align="center">:fire:QSC LOBOT Cluster Instructions:fire:</h1>
<p align="center">
  <span>Contributors: Aaron Visser (https://github.com/wiegerthefarmer)</span>
</p>



# Introduction
This is a tutorial for using the Queen's School of Computing Computing cluster (known as Lobot).  It currently contains 17 hosts(nodes) of varing performance, hosting 121TB of storage, 10.5TB of memory, 2000 cpu cores and 75 NVIDIA GPUs. GPUs being hosted range from A16s, RTX5000, RTX6000, RTX6000-ada, A40s, A100s, and H100 NVLs.  Lobot is ideal for performing computing tasks that wouldn't be possible on your local machine.  Before you begin, please read the Queen's policy on [Acceptable Use of Information Technology Resources](https://www.queensu.ca/secretariat/policies/senate/electronic-information-security-policy-framework/acceptable-use-information).

# Important Links and Resources

- [Server Access](https://lobot.cs.queensu.ca/)
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
- [MatLab](#matlab)
- [Co-Pilot](#co-pilot)
- [VS Code](#vs-code)
- [VS Code Remote Tunnel](#vs-code-remote-tunnel)
- [GPU & Python Packages](#gpu-and-python-packages)
- [Conda Environments](#conda-environments)

# Initialization
Access to Lobot is gained through github credentials and being a member of the Queen's School of Computing Github Organization. After you accept the organization invite, you can access the cluster by logging in at https://lobot.cs.queensu.ca/

Once you have connected your GitHub to the server you will now see the Hub Control Panel. The Hub Control Panel is where you can initialize or terminate your session. 

### Allocating Server Resources
Before you can begin using your the server you must first specify the resources you need.
![image](https://github.com/user-attachments/assets/854a176b-c6db-4a18-9ddd-3e2f37c769e7)

This is a shared resource, so only take what you think you’ll need. If the resources aren’t available, you won’t be able to start your server until they get freed up again. Start with the minimum resources and see how performance is, if you feel you need more. Stop your workload and start it again with more cores/memory/gpu.

**NOTE** Above the resource selection is the current available resources with the active users. If you require immediate resources, please contact the user directly so that they can finish work and stop their server. In case of emergency, please email help@cs.queensu.ca

On your first startup of the server you will be allocated 50G of storage. These 50G will always be yours, so there is no need to worry about your work not being saved when you terminate your session.  If you ever require more storage contact the School of Computing Tech Team at help@cs.queensu.ca

If your server is running during the night, it will be backed up. Only a single snapshot is maintained and is overwritten each night. 

# Termination
![image](https://user-images.githubusercontent.com/25777239/92413201-fdf08c80-f11c-11ea-9f9c-702bfbdf4902.png)

**\*IMPORTANT!\*** Closing your JupyterLab tab will not  end your session and free up resources.  You must go to File -> Hub Control Panel, then in the new tab click the "Stop My Server" button.  All your files on the server will be automatically saved upon ending a session. ALSO, when using the remote desktop, DO NOT log-out of it. Just close the tab if you don't want to use it or want to "logout". If you logout, it will kill the remote desktop and you will have to stop and restart your server.

### Server Life cycle
After 72 hours of inactivity your session will be terminated.  All your files will be automatically saved to your allocated storage.


# JupyterLab
Once you have completed server initialization you will be connected to JupyterLab through the server.

![image](https://github.com/user-attachments/assets/61a83810-f3a9-497f-81af-92c078fee9fb)

From the JupyterLab launcher you can easily create a Jupyter Notebook, console, terminal window,  or VS Code instance.  To re-open the launcher go to File -> New Launcher or type (⌘ / Ctrl) + Shift + L.

## MatLab
*New* Matlab is now installed in the image, see https://github.com/Queens-School-of-Computing/Lobot-Cluster-Information/blob/master/matlab_instructions.md for more details.

## Co Pilot
I've received two recurring requests recently, one is for Github Copilot and the other is Remote VSCode. 

Regarding Copilot, this is available to every verified educational user, just visit https://education.github.com/discount_requests/application and fill out an application. Please note, it may take several days for the verification to take place.

Copilot chat may not work in the notebook version of VSCode. Use the fully fledged remote desktop version.
Launch remote desktop. If you select VS Code from the jupyter desktop it might not support a tunnel.

Open up VSCode which is already installed.
![image](https://github.com/user-attachments/assets/5db10383-6756-4232-bd32-efee06621c51)

Sign into GitHub and then copilot should activate if you have it enabled for your account.

## VS Code
![image](https://user-images.githubusercontent.com/25777239/92413231-1d87b500-f11d-11ea-8d07-889b2b0532c8.png)

VS Code on the server works exactly like a local version, this includes the ability to add extensions.  Your extensions and settings will be automatically saved in your server storage when your connection is terminated.

## VS Code Remote Tunnel
Setting up VSCode remote tunnel to access your cluster resources

Some background documentation:
https://code.visualstudio.com/docs/remote/tunnels
https://marketplace.visualstudio.com/items?itemName=ms-vscode.remoteserver

Launch remote desktop. If you select VS Code from the jupyter desktop it might not support a tunnel.

Open up VSCode which is already installed.
![image](https://github.com/user-attachments/assets/5db10383-6756-4232-bd32-efee06621c51)

Sign into GitHub and then turn on remote tunnel access.

Now you can open your VS Code on your local machine, sign into GitHub and click the bottom left hand icon to bring up the menu to connect to tunnel.
Select GitHub as the account used. And then pick the gpu cluster workload

You are now connected to the remote workload. Files are saved on your  cluster instance. You can drag and drop files to the directory and do all the normal things.

Remember that you have to have vscode open in the remote desktop session for the tunnel to be active.

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


