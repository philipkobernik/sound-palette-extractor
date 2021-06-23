# SoundPalette Extractor

### The following are step-by-step instructions to install and run the SoundPalette extractor on an archive of sounds on an external hard drive

1. first, lets install docker!
    - https://docs.docker.com/docker-for-mac/install/
2. now open the terminal app
    - press `command` + `spacebar` to open spotlight, type `terminal` and press enter
3. navigate to your source-code folder
    - if you don't have one, open the terminal app, and type the following commands to make a folder inside of your home folder:
        - ```shell
          cd ~/
          mkdir src
          cd src
4. let's verify that git is installed
    - type `git version` and press enter
    - if there is an error here, let Philip know via email
5. great, now clone the project repo with the following git command
    - ```shell
      git clone git@github.com:philipkobernik/sound-palette-extractor.git
      cd sound-palette-extractor
6. Now let's copy our python notebook file:
    - open finder by typing `open .`
    - click on the file called `palette-extractor.ipynb` and copy it with keyboard combo `command` + `c`
    - navigate to your external drive in finder
    - paste the file with keyboard combo `command` + `v`
7. Now it's time to start the docker image
    - focus on the terminal window from earlier
    - type `cd ` then drag your external drive directly into the terminal window. Now press enter.
      - for Rouzbeh, this should be `cd /Volumes/T7`
    - Now, paste the following line and press enter:
    - ```javascript
      docker run --rm -p 8888:8888 --mount type=bind,source=$(pwd),target=/notebooks mtgupf/mir-toolbox
    - if successful, we should see something like this:
        - ```shell
          [I 01:49:29.963 NotebookApp] Writing notebook server cookie secret to /root/.local/share/jupyter/runtime/notebook_cookie_secret
          [I 01:49:31.404 NotebookApp] Serving notebooks from local directory: /notebooks
          [I 01:49:31.405 NotebookApp] The Jupyter Notebook is running at:
          [I 01:49:31.405 NotebookApp] http://(6cd0a12dffe2 or 127.0.0.1):8888/?token=...
8. open the notebook in your web browser by navigating to [http://localhost:8888?token=mir](http://localhost:8888?token=mir)
9. click on the file named `palette-extractor.ipynb` to open the notebook
10. at the top of the file, update the second line of code to specify the folder to search for audio files.
    - for Rouzbeh, this should be `siblingSourceFolder = "User Library"`
11. click `Cell` > `Run All`
12. The extractor may take some hours to complete. I recommend letting it run over-night or when you finish work for the day.
    - sometimes, the app "kernel" will simply "die" and stop
      - if this happens, simply re-start the analysis process by clicking `Cell` > `Run All`
      - the algorithm will skip files that it has already processed
