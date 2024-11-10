# DMSF
The code will be available soon！
## Overall Model Structure
![02](https://github.com/user-attachments/assets/212ff31b-2bc1-40da-9ab1-dea757c95fd0)

Specifically, in the feature coding module, our model is fed into audio and visual sequences, and feature vectors are extracted from the encoder of the pre-trained AudioCLIP model on the Audioset dataset by fine-tuning the Adapter layer. The spatial attention model AGVA is employed to coarsely align audio and visual features. In the subsequent SNS module, Bi-LSTM and a self-attention mechanism are employed to capture the temporal dependence of intra-modal information. The encoded information $v^S$ and $a^S$ are then transmitted to the CIC module for refinement. During this stage, a multi-head dual-attention structure is designed to filter and fuse correlation information between audio and visual modalities. This fused information guides the generation of refined visual feature $v^C$ and audio feature $a^C$, respectively. In the prediction head module, the features $v^C$ and $a^C$ undergo linear transformation to generate predictions for audio-visual events. Lastly, a novel mutual learning loss function within the classification module is designed to mitigate noise during the audio-visual fusion stage. It is important to note that $v^S$, $a^S$, $v^C$, $a^C$, $v^I$, and $a^I$ are all vectors of dimension $\mathbb{R}^{ B \times T \times d_v}$, where $d_v$ is the vector dimension of the encoded visual feature.
## Main Innovations
our main innovations of this paper include:

* A novel two-branch mutual-learning-based framework DMSF is designed for AVEL to make full use of the relevant information before and after audio-visual fusion. This approach enriches the multi-view compensation of audio-visual correlation information and mitigates fusion noise through multi-modal mutual learning.

* The audio-visual correlation prior knowledge of the VLP model is introduced to construct the encoders of DMSF to improve the semantic complementarity of audio-visual features. In particular, we design an Adapter layer with controllable sampling rate to adjust the fine-tuning parameters of the encoders.

* The SNS module is employed to enhance temporal dependencies within single modalities, utilizing a gate-controlled self-attention mechanism to adaptively suppress noise. While the CIC module, through a multi-headed cross-modal fusion attention strategy, comprehensively extracts semantic information of audio-visual events. Together, these modules collaborate to encode high-quality audio-visual representations.

* Experimental results on the extensively employed AVE dataset demonstrate that our proposed model has superior performance in both fully supervised and unsupervised settings compared to the latest State-of-the-Art (SOTA) models.
The code will soon be available

## Comparison Experiments
Results of comparison of our model and SOTA models on the AVE dataset under both fully supervised and weakly supervised settings.
![image](https://github.com/user-attachments/assets/2aaed997-fb5f-4ac5-b3ed-92da90214854){:height="100" width="50"}

## Qualitative Analysis
Qualitative visual analysis of our DMSF model on two event examples ("Bark" and "Bus"). The first row of each example shows the audio waveform image with event labels (divided into 10 segments), while the third row presents segment-level images with Ground Truth (GT) labels (red boxes denote event labels). Additionally, attention heatmaps for both the baseline AVGA model (second row) and our DMSF model (fourth row) are provided, with predicted event location frames highlighted by orange and green boxes, respectively.
![06](https://github.com/user-attachments/assets/6acb1dc2-6dc2-4d1c-bf87-e7e54db91b67)


