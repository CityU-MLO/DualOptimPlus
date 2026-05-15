# DualOptim+: Bridging Shared and Decoupled Optimizer States for Better Machine Unlearning in Large Language Models


## Installation

```bash
pip install -r requirements.txt
```

## Usage

### Script Directory Structure
```
scripts/
└── tofu_phi1-5/         # Phi-1.5 model TOFU benchmark
```

### Main Script Parameters

#### General Parameters
- `forget_losses`: Unlearning loss function combinations (e.g., ME+GD, DPO+GD, IDK+GD, etc.)
- `task_list`: Unlearning task ID list (1-10)
- `learning_rates`: Learning rate list
- `split`: Dataset split (forget01/forget05/forget10)
- `num_epochs`: Number of training epochs
- `mask`: Whether to use masking (true/false)
- `use_LoRA`: Whether to use LoRA fine-tuning
- `forget_coeff`: Unlearning coefficient
- `regularization_coeff`: Regularization coefficient

#### Optimizer Parameters
- `optim_cfg`: Optimizer configuration (adam, dual_adam, dual_adam_plus, etc.)
- `forget_lr`: Unlearning learning rate
- `alpha`: Weight parameter
- `beta1`, `beta2`: Adam optimizer parameters
- `base_beta1`, `base_beta2`: Base model optimizer parameters

#### Training Parameters
- `max_steps`: Maximum training steps
- `batch_size`: Batch size
- `gradient_accumulation_steps`: Gradient accumulation steps
- `alternate`: Whether to use alternate training
- `retain_freq`: Retention frequency

#### Saving and Evaluation
- `save_root`: Root directory for saving results
- `save_checkpoint`: Whether to save checkpoints
- `save_steps`: Save steps configuration
- `eval_steps`: Evaluation steps configuration

### Running Examples

#### Run ME+GD unlearning for Phi-1.5 model
```bash
cd scripts/tofu_phi1-5/
bash me_gd_dual.sh
```

#### Run benchmark tests
```bash
cd scripts/tofu_phi1-5/
bash baselines.sh
```

### Configuration Files
Main configuration files are located in `config/` directory:
- `phi1-5_tofu.yaml`: Phi-1.5 model TOFU configuration

## Datasets
The project includes multiple datasets:
- TOFU dataset: For model unlearning benchmark testing
- Real-world dataset: Practical application scenario data
- Safety alignment data: Model safety training data. Download from https://github.com/vinid/safety-tuned-llamas/tree/main/data and https://huggingface.co/datasets/walledai/XSTest.