# Fine-Tuning Whisper Model for Tamil ASR

This README provides instructions for fine-tuning OpenAI's Whisper model for Tamil Automatic Speech Recognition (ASR) using the Common Voice 11.0 dataset.

## Prerequisites

### GPU Connection
Ensure you're connected to a GPU for faster training.

### Install Required Libraries
Ensure you have the following Python libraries installed:
- `datasets[audio]`
- `transformers`
- `accelerate`
- `evaluate`
- `jiwer`
- `tensorboard`
- `gradio`

### Login to Hugging Face
Authenticate your session with Hugging Face to access datasets and model hub.

## Dataset Preparation

### Load and Prepare the Dataset
- Load the Common Voice dataset for Tamil (ta) from the Hugging Face Datasets library.
- Remove unnecessary columns such as `accent`, `age`, `client_id`, `down_votes`, `gender`, `locale`, `path`, `segment`, and `up_votes`.
- Resample audio data to 16kHz.

## Preprocessing

### Feature Extraction and Tokenization
- Use the `WhisperFeatureExtractor` to extract features from audio samples.
- Use the `WhisperTokenizer` to tokenize the text data.
- Combine these into a `WhisperProcessor` for streamlined preprocessing.

### Prepare Dataset
- Process each dataset entry to extract features and encode labels.

## Model Initialization
- Initialize the `WhisperForConditionalGeneration` model.
- Configure the model for Tamil language transcription.

## Data Collator
- Create a data collator to handle padding of inputs and labels during training.

## Evaluation Metric
Use Word Error Rate (WER) as the evaluation metric to assess model performance.

## Training

### Training Arguments
Define training arguments including batch size, learning rate, warmup steps, max steps, evaluation strategy, and more.

### Trainer
Initialize the `Seq2SeqTrainer` with the model, datasets, data collator, and evaluation metric.
Train the model and save the best checkpoint.

## Push Model to Hub
Push the fine-tuned model to the Hugging Face Model Hub for sharing and deployment.

## Real-time Inference with Gradio
Create a Gradio interface for real-time speech-to-text transcription using the fine-tuned model.
