# Hackathon Outline
An outline of the University of Guelph Bioinformatics Hackathon!
Feel free to fork this document and update it with information you feel others would benefit from, then perform a pull request and we will review and merge! [Here](https://help.github.com/articles/basic-writing-and-formatting-syntax/) is a guide to formatting in this document.

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
2. Install Software
   - Git, Java, Nextflow
     - Git is the version control software you will be required to use
     - Nextflow is a domain specific language for creating software pipelines
     - Open a terminal
       - ```
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
   - [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
   - [docker-compse](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
     - You then need to give your USER account docker permission
`sudo usermod -a -G docker $USER`
   - Restart Ubuntu

3. Setup Github Repository and Access
   - As a team you are required to use a single public Github repository for version control and collaboration to participate in the Hackathon
   - [Here](https://guides.github.com/activities/hello-world/) is a guide to getting started with your first Github Repository
   - [Here](https://guides.github.com/introduction/flow/) is a guide to understanding the Github workflow
   - You are required to make your Github repository a public repository. This way the Hackathon Judges will be able to inspect your code, including all your commits so that we can see how the code was developed, we may do this during the competition
     - Your final commit on the last day of the competition will be the one judged
   - In the first three days of the competition you are required to send us the URL for your Github repository, we will not share this with the other competitors.
   - It is recommended that you use SSH keys to push commits to your Github repository
     - [Here](https://help.github.com/articles/connecting-to-github-with-ssh/) is a guide for doing so
       - VS Code cannot handle SSH keys that require passphrases so do not use one, leave it blank
       - If on Ubuntu you can setup your .bashrc to load the ssh-agent when a terminal is opened and add your ssh key to it
         - ```
           echo "eval `ssh-agent`
           ssh-add ~/.ssh/id_rsa" >> ~/.bashrc
           ```
    - VS Code integrates with Git and Github you can stage commits, push, using the source control pane (Ctrl+Shift+G) and resolve pull requests

## Using Docker
1. Understanding Docker
   - [Here](https://www.docker.com/resources/what-container) is a description of what Docker is
   - [Here](https://docs.docker.com/get-started/) is a guide for getting started with Docker, you only need concern yourself with the first two parts
2. Hackathon Expectations
   - Using Docker is not required for the competition but it is recommended, projects that employ Docker will have an advantage in the competition
   - In using Docker we would like to see you create your own Docker images from a base OS. You are free to use pre-made containers in whole or as guides though, original containers will be given more weight in the judgement.
     - Examples of bioinformatics containers can be found [here](https://biocontainers.pro/). The council has also built some example containers which are up on our [Github](https://github.com/BINF-GSC)
     - Create a dockerfile and build locally or integrate your Github with [Dockerhub](https://docs.docker.com/docker-hub/) and have your containers online ready to be used anywhere with a simple download

## Using Nextflow
1. Understanding Nextflow
   - [Nextflow](https://www.nextflow.io/) is a domain specific language (DSL) designed to make writing and executing analytical pipelines simple, robust, and reproducible.
     - The same pipeline can be used be on your local machine, on Compute Canada HPCs, and on cloud services like AWS just by changing the configuration file!
     - These pipelines remember where in the analysis you were so that previously completed steps are not repeated in case of premature stopping of the analysis due to errors or if proceeding steps are modified.
     - It works using two simple concepts channels and processes
       - A channel contains the input files for processes, either sourced from disk or the output of a previous process
       - A process processes the files in some way (read quality control, alignment, etc.) and outputs the results. Any arbitrary program or language can be used.
     - Documentation can be found [here](https://www.nextflow.io/docs/latest/index.html)
     - There are many example pieplines for bioinformatic analyses available online [e.g.](https://github.com/nextflow-io/patterns)
2. Hackathon Expectations
   - You are not required to use Nextflow but it is recommended, projects that use it will have an advantage in the competition
   - If you have a different preferred workflow language like Snakemake you are free to use that as well, this will be considered the same as Nextflow
   - We would like to see you create your pipelines from scratch but you are free to use publicly available pipelines in whole or as guides, original pipelines will be given greater weight in the judgement. If you use publicly available pipelines make sure to indicate this in a comment at the top of you pipeline file.

