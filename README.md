# SoundPalette Extractor

Below are setup steps to install and run the SoundPalette extractor.

1. first, lets install docker!
    - https://docs.docker.com/docker-for-mac/install/
2. now open the terminal app
    - press command+spacebar to open spotlight, type `terminal` and press enter
3. navigate to your source-code folder
    - if you don't have one, open the terminal app, and type the following commands to make a folder inside of your home folder:
        - ```shell
          cd ~/
          mkdir src
          cd src
4. let's verify that git is installed
    - type `git version` and press enter
5. great, now clone the project repo with the following git command
    - ```shell
      git clone git@github.com:philipkobernik/sound-palette-extractor.git
      cd sound-palette-extractor
6. now its time to start the docker image
    - ```javascript
      docker run --rm -p 8888:8888 --mount type=bind,source=$(pwd),target=/notebooks mtgupf/mir-toolbox
    - if successful, we should see something like this:
        - ```shell
          [I 01:49:29.963 NotebookApp] Writing notebook server cookie secret to /root/.local/share/jupyter/runtime/notebook_cookie_secret
          [I 01:49:31.404 NotebookApp] Serving notebooks from local directory: /notebooks
          [I 01:49:31.405 NotebookApp] The Jupyter Notebook is running at:
          [I 01:49:31.405 NotebookApp] http://(6cd0a12dffe2 or 127.0.0.1):8888/?token=...
7. open the notebook in your web browser by navigating to [http://localhost:8888?token=mir](http://localhost:8888?token=mir)
8. click on the file called `palette-extractor.ipynb` to open the notebook
9. the extractor looks for your audio files inside of the folder called `corpus`
    - please move all of your archive audio files here, without subfolders
10. click `Cell` > `Run All`
11. The extractor may take some hours to complete, depending on the size of your archive
    - on my 2016 macbook pro, the exractor runs about 2 files/minute
    - for my archive of 941 files, it will run for about 8 hours
12. The notebook is not very efficient with memory, and memory usage will blow up like a balloon when processing large archives.
    - for this reason, I recommend allocating 7+ GB of memory to the docker container
    - if the notebook runs out of memory, the kernel will die and restart
        - if this happens, simply re-start the process with `Cell` > `Run All`
        - it will skip files that it has already processed
