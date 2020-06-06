# RL-Sepsis-Prediction
Using public data from https://physionet.org/content/challenge-2019/1.0.0/

we're creating RL model to classify patients with sepsis at each hour.

The RL environment is using open ai's gym : https://github.com/openai/gym

# Install dependencies
If using conda, create an environment with python 3.7:
`conda create -n rl_sepsis python=3.7`

Activate the environment:
`conda activate rl_sepsis`

Then, install the necessary packages:
`pip install -r requirements.txt`

# Clean data
We have upload training set A from the physionet competition into the repo.
To load and clean the data, run:

`make load_data`

This will take about 10 minutes, and the progress bar will be displayed using tqdm. It will create 
a `cache\` directory, created from the cache_em_all package.

Now, in a notebook or .py file, you can load the data with  

```
from load_data import load_data
df = load_data()
```

where df is a pandas data frame. 

# Add Rewards
Using the utility function provided by the competition, 
we have added two columns that correspond to the reward
recieved at each hour depending on whether predicting a zero or a one.

To create the reward columns, run:
`make add_reward`
