# Searching for Modern Mobile Architectures by Rethinking Model Paralleism
*Note that this work is currently under-review and thus speicific explanation and details are not available.

<br>

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
    export PYTHONPATH=/path/to/hetero_network_adaptation
    ```
    
<br>

## How to use
- To simply load PyTorch model :
```
#~/hetero_network_adaptation/

from modules.torch_modules import TorchBranchedModel
from utils import load_adapted_params

#base_model: mobilenet_v2
model = TorchBranchedModel('model_configs/mobilenet_v2_adapted.json')
model.load_state_dict(load_adapted_params('mobilenet_v2'))
```

- To evaluate on ImageNet :
```
$ python3 eval.py --base_model mobilenet_v2 --path 'your/path/to/imagenet'  

    # -j: number of workers (default: 4)
    # -b: batch_size (default: 512)
```

<br>

## File Structure 
<ul>
    <li><a href='model_configs/'>model_configs</a>: model configuration files (Can be built using TorchPretrainedModel or TorchBrancedModel from modules.torch_modules)</li>
    <li><a href='modules/'>modules</a>: custom modules to build models and subblocks (PyTorch, TVM Relay)</li>
    <li style="color: #404040; text-decoration: line-through">
        search: code for network adaptation search
        <ul>
            <li>local_client: code for local_client during search (MCTS agent)</li>
            <li>remote_host: code for remote_host during search (bridge between client and server container)</li>
            <li>remote_container: code for server containers (Actual training nodes)</li>
        </ul>
    </li>
    <li style="color: #404040; text-decoration: line-through">
    runtime_profile: code for runtime profiling (execution & sync )
    </li>
</ul>

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  $\rightarrow$ currently omitted due to maintenance and policy

<br>

## Model Visualization
- To be Updated Soon!