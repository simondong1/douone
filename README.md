# DouOne: Mastering DouDizhu by Self-Play Deep Reinforcement Learning with better network

Our repo consists four folders. You can `cd` into each folder and run the code for different training models.

After you are in the folder, follow the instructions below.
## Training
To use GPU for training, run
```
python3 train.py
```
This will train DouOne on one GPU. To train DouOne on multiple GPUs. Use the following arguments.
*   `--gpu_devices`: what gpu devices are visible
*   `--num_actor_devices`: how many of the GPU deveices will be used for simulation, i.e., self-play
*   `--num_actors`: how many actor processes will be used for each device
*   `--training_device`: which device will be used for training DouZero

For example, if we have 4 GPUs, where we want to use the first 3 GPUs to have 15 actors each for simulating and the 4th GPU for training, we can run the following command:
```
python3 train.py --gpu_devices 0,1,2,3 --num_actor_devices 3 --num_actors 15 --training_device 3
```



## Evaluation

### Step 1: Generate evaluation data
```
python3 generate_eval_data.py
```


### Step 2: Self-Play
```
python3 evaluate.py
```
Some important hyperparameters are as follows.
*   `--eval_data`: the pickle file that contains evaluation data
*   `--num_workers`: how many subprocesses will be used

