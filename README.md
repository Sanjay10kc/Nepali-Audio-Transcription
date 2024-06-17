# Nepali Audio Transcription

## Our approach
0. Remove the (audio, text) pairs that include Devnagari numeric transcriptions
1. Data cleaning (clipping silent gaps from both ends)
2. MFCC feature extraction from audio data
3. Design Neural Network (optimal: CNN + ResNet + BiLSTM) model 
4. Calculate CTC loss for applying gradient (training)
5. Decode the texts by using beam search decoding (infernce)

## Architecture
![Res_block](https://github.com/Sanjay10kc/Nepali-Audio-Transcription/blob/5547a94cbe901896abc99ebb2a66cd70b7644e6c/media/res_block.png)

![Model](https://github.com/Sanjay10kc/Nepali-Audio-Transcription/blob/5547a94cbe901896abc99ebb2a66cd70b7644e6c/media/model.png)

## Running the project
0. Initialize the virtual environment by installing packages from `requirements.txt`.
1. Run the training pipeline & evaluate authors model, which can be also be used to evaluate your own (audio,text) pairs.
```
python trainer.py   # For running the training pipeline
python eval.py      # For testing and evaluating the model already trained by the author
```

## Results
Models and Their character error rate (CER) on Test Data (5% of Total Data.)

| Model | Test Data CER | # Params |
| :---: | :---: | :---: | 
|BiLSTM | 19.71% | 1.17M |
|  1D-CNN + BiLSTM | 24.6% | 1.55M |            
|  1D-CNN + ResNet + BiGRU | 29.6% | 1.30M |            
|  **&check; 1D-CNN + ResNet + BiLSTM** | **&check; 17.06%** | **&check; 1.55M**|
|  1D-CNN + ResNet + LSTM | 30.27% | 0.88M|
