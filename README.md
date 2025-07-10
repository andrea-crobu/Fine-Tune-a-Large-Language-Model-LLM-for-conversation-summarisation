# Conversation Summarization using Fine-Tuned FLAN-T5

## Project Overview
This project fine-tunes the `flan-t5-base` model to improve its performance in conversation summarization. The dataset used for training is [DialogSum](https://www.kaggle.com/datasets/knkarthick/dialogsum) from Kaggle. The model was fine-tuned using LoRA (Low-Rank Adaptation) to efficiently enhance its performance while reducing computational costs.

## Dataset
**Source:** Kaggle - `knkarthick/dialogsum`

The dataset consists of dialogues paired with human-written summaries. Each dialogue is preprocessed and formatted as follows before being fed into the model:

```
Here is a dialogue:

    {dialogue}

Write a short summary!
```

## Model Fine-Tuning
Fine-tuning was performed using LoRA to adapt `flan-t5-base` for better summarization of conversations. The LoRA technique allows for efficient adaptation by modifying a small number of parameters, making training computationally efficient.

## Evaluation
The performance of the base and fine-tuned models was evaluated using ROUGE scores.

### **ROUGE Scores Comparison**

| Model            | ROUGE-1 | ROUGE-2 | ROUGE-L | ROUGE-Lsum |
|-----------------|---------|---------|---------|------------|
| **Base Model**  | 0.3083  | 0.1122  | 0.2579  | 0.2580     |
| **Fine-Tuned**  | 0.4402  | 0.1753  | 0.3561  | 0.3563     |

The fine-tuned model shows a significant improvement over the base model across all ROUGE metrics.

## Example Output

### **Original Dialogue:**
```
#Person1#: Hi, I was wondering if I could get my test results from the other day.
#Person2#: Yes, I would like to schedule an appointment for you to come in and talk with me.
#Person1#: Is something wrong with me?
#Person2#: No, sometimes the test results aren't clear and we need to do more to get a clearer picture.
#Person1#: Can we talk about it now?
#Person2#: I would if I knew anything for sure, but I want to take a second look.
#Person1#: When can I come and see you?
#Person2#: You can come in this afternoon. If you would feel better, bring your husband with you.
#Person1#: Now I know that something bad is up!
#Person2#: Just relax. We will talk about it this afternoon.
```

### **Ground Truth Summary:**
```
#Person2# schedules an appointment with #Person1# and #Person1#'s husband. #Person1# is nervous to know the test results.
```

### **Base Model Summary:**
```
Person1 wants to schedule an appointment for Person2 to come in and talk about the test results from the other day.
```

### **Fine-Tuned Model Summary:**
```
#Person1# wants to get the test results from the other day. #Person2# tells #Person1# they need to do more to get a clearer picture. #Person1# will come and talk about it this afternoon.
```

The fine-tuned model generates a more detailed and contextually accurate summary compared to the base model.

## Installation & Usage
### **Prerequisites**
- Python 3.8+
- PyTorch
- Transformers (Hugging Face)
- PEFT (for LoRA fine-tuning)
- Datasets (Hugging Face)

## Conclusion
This project demonstrates how fine-tuning `flan-t5-base` with LoRA significantly improves conversation summarization performance. Future improvements may include experimenting with different fine-tuning techniques or datasets to further enhance summarization quality.

