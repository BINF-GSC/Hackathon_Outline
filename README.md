# Hackathon Outline
An outline of the University of Guelph Bioinformatics Hackathon!
Feel free to fork this document and update it with information you feel others would benefit from, then perform a pull request and we will review and merge!

## Environment Setup
1. Install Ubuntu
   - You don't have to use Ubuntu, you are free to try any other operating system but our recommendation is Ubuntu and these instructions are based on Ubuntu
     - Nextflow does not work on Windows, you can use the Windows 10 Linux subsystem with ubuntu bash but you can't run a docker daemon within it. One work around is to communicate with a Windows 10 docker daemon from the Linux subsystem but you will run into issues with mount paths for data between the Linux subsystem and the expectations of the Windows 10 Docker daemon that I am not sure how to solve
     - Other workflow languages (Snakemake, CWL, etc.) also do not appear to work on Windows but you are free to try
   - You have a few options for installation
     - As the sole operating system on your machine (come over to the sunny side)
     - Dual boot (if you just can't make a commitment)
     - In a VM (if you just aren't ready for more than a temporary relationship)
       - Recommend Virtual Box on Win 10
         - [Here](https://linuxhint.com/install_ubuntu_18-04_virtualbox/) is a guide, others can be found using google
       - Be aware that computations will be slower using this option since you will be sharing hardware with the underlying OS (less RAM, fewer cores available)
    - [Here](https://linuxconfig.org/how-to-install-ubuntu-18-04-bionic-beaver) is a guide for downloading and installing Ubuntu
2. Needed Software
   - Git, Java, Nextflow
     - Git is the version control software you will be required to use
     - Nextflow is a domain specific language for creating software pipelines
     - Open a terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
sudo apt-get install default-jdk
cd /usr/bin/local
sudo wget -qO- https://get.nextflow.io | bash
cd
```
   - [Visual Studio Code](https://code.visualstudio.com/download)
     - This is our recommended code editor. It is light weight and versatile with many extensions that are very useful for us.
     - Install the following extensions (open the extension pane with Ctrl+Shift+x)
       - Docker
       - GitLens
       - Nextflow
     - Optional extensions
       - vscode-icons
         - A set of file type icons for making types more visually distinct
         - Enable under Manage > File Icon Theme
           - Manage is the gear icon in the bottom left
       - One Dark Pro
         - A very nice theme for syntax highlighting, others are available!
         - Enable under Manage > Color Theme
       - Python
         - If you want to use Python instead of Nextflow
           - Python can be used on Windows 10
         - Make sure to turn on flake8, pep8, pylint, and pydocstyle linting in the extension's settings. Manage > Settings > Extensions > Python.
           - This will warn you when you are writing poorly formatted code.  It might take some time to figure out what you are doing wrong but proper style is an important factor in the hackathon.
           - You will also have to install some of these but VS code will prompt you to do this when you save a python file.
   - Docker
     - Guide [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/) for Docker CE
     - You also need to install [docker-compse](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
     - You then need to give your USER account docker permission
`sudo usermod -a -G docker $USER`
   - Restart Ubuntu