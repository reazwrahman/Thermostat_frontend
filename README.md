# Project Description

Project context can be found at this link (published version of this site), 
avoiding rewriting it here to maintain a single source of truth:  
https://reazwrahman.github.io/thermostat_frontend/background_pages/context_page/index.html  

Hardware Setup for some perspective: https://reazwrahman.github.io/thermostat_frontend/background_pages/hardware_page/index.html  

## General Comments 

- I have used React in non-build approach to create the navigation bar for the website. I found this to be an excellent use-case for React. Everytime I was making any change to the navbar, I had to copy-paste the same change across all of my pages. A reusable React component made a lot of sense for this. 

- Youtube Link to the presentation: https://www.youtube.com/watch?v=SZcvlecOQ6Y 

- Github Repo: https://github.com/reazwrahman/thermostat_frontend  

- Backend API Repo: https://github.com/reazwrahman/Thermostat_Backend_API 

## First Time Setup Instructions    

You can run this site in two different ways: both options are described below.

### VS Code Live Server  

Run the index.html found at the root directory of the Github Repo (```thermostat_frontend/index.html```)

### Python Server  

- VS Code Liver server is not an option for target hardware where the server 
needs to be started from CLI.

- To fix this problem, I have copied the index.html from the root directory and moved it one directory up (and changed a couple of the directory references). 
This copy of index.html can be found in a folder called "backup" in the root directory. If you choose run the site with Python Server, you would have to copy the backup/index.html and paste in one directory above the the root(thermostat_frontend). Directory tree:

>index.html  (run python server from here)
>....thermostat_frotnend (git root directory)

- Make sure you have Python(3.x) installed 

- Now run ```python3 -m http.server 3000 --bind 127.0.0.1 ```

- Find the site on ```http://127.0.0.1:3000/```


### Instructions for configs.js  

- navigate to ```thermostat_frontend/configs.js``` file. You will have to make the following changes: 

1) Provide a valid API Key for the weather api (included with the git repo). 

2) for const laptop_ip, provide your computer's ip address followed by 
port 8080 (```<your-ip>:8080```). You can ignore the 
raspberry_pi ip field. 
NOTE: This step assumes that you already have (or will run) the backend API on another shell in your terminal. See the Backend API instruction section below.

3) Make sure running mode is set to simulation and not target, look for this line: ```const MODE = RUNNING_MODES.SIM```


## Running Modes of the Website

This site is intended to run in 3 different modes: public mode, simulation mode and target mode. 

```Public Mode```: This is the published site on the internet (https://reazwrahman.github.io/thermostat_frontend/). This mode does not require any backend API setup. You will see that all the backend data pipelines are stubbed with static
json data located within the project directory. 

While this mode is great for ease of access and viewing the UI of the site,
it doesn't even begin to show the full power of this system. 

```Simulation Mode```: This is the mode if you want to test the site on your local machine and want to fully appreciate the power of the site. I call this the simulation mode because it will run on your computer and doesn't need any 
embedded hardware. There are built in simulated temperature sensor and simulated power relay to mimic the exact behavior of the embedded hardware setup. 

To run this mode, you HAVE TO setup the backend API in parallel to running the
frontend site. Please see the Backend API Setup section below. Setting up the backend can take as little as 5 minutes if you are somewhat familiar with Python package management.  

```Target Mode```: This is basically the production equivalent of the site. It runs on actual hardware setup with a microprocessor, sensor and a power relay. It uses same backend API as the simulation mode. The endpoints are dynamically routed to the right place based on the target ip address and running mode defined in the Configs files.  


## Backend API Setup 

Run this api in a different shell in your terminal. The detailed instruction for the setup can be found on the README for that repository: https://github.com/reazwrahman/Thermostat_Backend_API/blob/master/README.md  