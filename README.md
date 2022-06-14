# Enhancing Model Paralleism via Neural Architecture Search (Title Modified)
*Note that this work is currently under-review and thus speicific explanation and details are not available.

## Requirements and Setup
- For Runtime: 
    - **TVM 0.8.dev0** or higher
    - **LLVM 8.0.0** or higher
    - **OpenCL (aarch64)**
- For Search and Evaluation:
    - **PyTorch==1.7.1** or higher
    - **Torchvision**
- For Python libraries, use:
    ```
    pip3 install -r requirements.txt
    ```
- Set the environment variable PYTHONPATH
    ```
    export PYTHONPATH=/path/to/MobileHeteroNAS
    ```

## How to use
- To simply load PyTorch model :
```
#~/MobileHeteroNAS/

from modules.torch_modules import TorchBranchedModel
from utils import load_adapted_params

#base_model: mobilenet_v2
model = TorchBranchedModel('model_configs/mobilenet_v2_adapted.json')
model.load_state_dict(load_adapted_params('mobilenet_v2'))
```

- To evaluate on ImageNet :
```
$ python3 eval.py --base_model mobilenet_v2 --path 'your/path/to/imagenet'  

    # --base_model: base model that is being adapted -> available: ['mobilenet_v2', 'mnasnet_b1', 'fbnet_c']
    # -j: number of workers (default: 4)
    # -b: batch_size (default: 128)
```

## File Structure 
- [model_configs]('model_configs/'): model configuration files (Can be built using TorchPretrainedModel or TorchBrancedModel from modules.torch_modules)
- [modules]('modules/'): custom modules to build models and subblocks (PyTorch, TVM Relay)

→ Belows are currently omitted due to maintenance and policy

- ~~search: code for network adaptation search~~
    - ~~local_client: code for local_client during search (MCTS agent)~~
    - ~~remote_host: code for remote_host during search (bridge between client and server container)~~
    - ~~remote_container: code for server containers (Actual training nodes)~~
- ~~runtime_profile: code for runtime profiling (execution & sync )~~

## Model Visualization
- To be Updated Soon!
