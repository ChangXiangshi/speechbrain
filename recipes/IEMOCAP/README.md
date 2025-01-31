# Emotion recognition experiments with IEMOCAP (speech only)
This folder contains scripts for running emotion recognition experiments with the IEMOCAP dataset (https://sail.usc.edu/iemocap/).

# Training ECAPA-TDNN
Run the following command to train the model:
`python train.py hparams/train.yaml`
or with wav2vec2 model:
`python train_with_wav2vec2.py hparams/train_with_wav2vec2.yaml`

# Results
| Release | hyperparams file | Val. Acc. | Test Acc. | Model link | GPUs |
|:-------------:|:---------------------------:| -----:| -----:| --------:| :-----------:|
| 2021-07-04 | train.yaml |  65.3 | 65.7 | [model](https://drive.google.com/drive/folders/1U9SiO4KkCNBKfxilXzJqBZ_k-vHz4ltV?usp=sharing) | 1xV100 16GB |
| 2021-10-17 | train_with_wav2vec2.yaml (wav2vec2 base) |  best 78.1 | best: 78.7 (avg 75.3) | [model](https://drive.google.com/drive/u/0/folders/11iZkcxvXYPnhf1yfYO_WVfRpGbN6HmNw) | 1xV100 32GB |
| 2021-10-17 | train_with_wav2vec2.yaml (voxpopuli base) |  best 73.3 | best: 73.3 (avg 70.5) | [model](https://drive.google.com/drive/u/0/folders/1hCL2vCQe2WS5wv5LU7JYkh7QSHNH9m4d) | 1xV100 32GB |
| 2021-10-17 | train_with_wav2vec2.yaml (hubert base) |  best 74.9  | best: 79.1 (avg 73,4) | [model](https://drive.google.com/drive/u/0/folders/1m8xggbhbsXHedMbF6dNVkNEW1bfGTjvi) | 1xV100 32GB |

# Training Time
About 40 sec for each epoch with a TESLA V100 (with ECAPA-TDNN).
About 3min 14 sec for each epoch with a TESLA V100 (with wav2vec2 BASE encoder).

# Note on Data Preparation
We here use only the audio part of the dataset. The assumpion is that the data folder is structured as:

    ```<session_id>/<emotion>/<file:name>.wav```

e.g. ```session1/ang/psno1_ang_s084_orgn.wav```

Our `iemocap_prepare.py` will:
1- Do labelling transformation to 4 emitions [neural, happy, sad, anger]
2- Prepare IEMOCAP data with random split. (Note for becnhmarking: you need to run 5 folds)

# PreTrained Model + Easy-Inference
You can find the wav2vec2 pre-trained model with an easy-inference function on HuggingFace:
- https://huggingface.co/speechbrain/emotion-recognition-wav2vec2-IEMOCAP/


# **About IEMOCAP**

```bibtex
@article{Busso2008IEMOCAPIE,
  title={IEMOCAP: interactive emotional dyadic motion capture database},
  author={C. Busso and M. Bulut and Chi-Chun Lee and Ebrahim Kazemzadeh and Emily Mower Provost and Samuel Kim and J. N. Chang and Sungbok Lee and Shrikanth S. Narayanan},
  journal={Language Resources and Evaluation},
  year={2008},
  volume={42},
  pages={335-359}
}
```

# **About SpeechBrain**
- Website: https://speechbrain.github.io/
- Code: https://github.com/speechbrain/speechbrain/

# **Citing SpeechBrain**
Please, cite SpeechBrain if you use it for your research or business.

```bibtex
@misc{speechbrain,
  title={{SpeechBrain}: A General-Purpose Speech Toolkit},
  author={Mirco Ravanelli and Titouan Parcollet and Peter Plantinga and Aku Rouhe and Samuele Cornell and Loren Lugosch and Cem Subakan and Nauman Dawalatabad and Abdelwahab Heba and Jianyuan Zhong and Ju-Chieh Chou and Sung-Lin Yeh and Szu-Wei Fu and Chien-Feng Liao and Elena Rastorgueva and François Grondin and William Aris and Hwidong Na and Yan Gao and Renato De Mori and Yoshua Bengio},
  year={2021},
  eprint={2106.04624},
  archivePrefix={arXiv},
  primaryClass={eess.AS},
  note={arXiv:2106.04624}
}
```

