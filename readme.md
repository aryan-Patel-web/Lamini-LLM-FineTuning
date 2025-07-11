

# Lamini-LLM-FineTuning

Fine-tune Meta-Llama-3-8B-Instruct using Lamini’s managed LLM engine and custom training data.  
This repo shows:
- How to format your dataset
- How to call Lamini’s `.tune()` method
- How to adjust key hyperparameters like learning rate

---


Example directory structure:

Lamini-LLM-FineTuning/
├── README.md
├── requirements.txt
├── finetune.py
└── .env

## 🚀 Quickstart

### 1. Install Lamini SDK

```bash
pip install lamini


 Prepare Data like this ---

 def get_data():
    data = [
        {
            "input": "Are there tutorials in the documentation?",
            "output": "Yes, there are step-by-step tutorials in the documentation."
        },
        {
            "input": "What is Lamini?",
            "output": "Lamini is a platform for building and executing LLMs."
        }
    ]
    return data


Run Fine-tuning

import lamini
from lamini import Lamini

lamini.api_key = "YOUR_API_KEY"

llm = Lamini(model_name="meta-llama/Meta-Llama-3-8B-Instruct")

data = get_data()

llm.tune(
    data_or_dataset_id=data,
    finetune_args={
        'learning_rate': 1.0e-4
    }
)

✅ Hyperparameters
Available arguments for finetune_args:

learning_rate: (float) e.g. 1e-4

early_stopping: (bool) enable early stopping

max_steps: (int) maximum training steps

optim: (str) optimizer, e.g. "adam"



📝 Example
Once tuned, you can use your model like this:


response = llm("What does Lamini do?")
print(response)