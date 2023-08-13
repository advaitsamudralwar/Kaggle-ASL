# Kaggle-American-Sign-Language-Transformer

Approach:
Converting mediapipe landmarks coordinates sequences into mediapipe handmodel image sequences for translating American sign langugage 
to text.

Mediapipe get_hand Block:
Extracts righthand and lefthand landmark coordinates and convert them to images of size 256 x 256

Preprocess Block:
1) Extracts right-left and pose coordinates.
2) Choose a dominant hand based on NaN values. The hand with minimum number of NaN value is selected. Incase both the hands
   have all NaN values, right hand (Choosen randomly) is selected as the dominant hand.
3) Maximum number of sequence frames are 413, so incase of sequence frame length lower than that, blank frames are added to the
  sequences to make all image sequences for every phrase to be of length 413
3) For efficiency the hand images and phrases are converted to TF Records.

Preprocess Ground Truth Block:
1) All phrases are padded with start(<) and end(<) token respectively.
2) All phrses are padded with p at the end to make them of equal length

Split Data Block:
Splits the data into Training and Validation Set

Transformer Block:
1) Token Embedding and Landmarks embedding are used for embedding and positional encoding of the input data and ground truth.
2) Encoder Decoder Class Define the encoder decoder block
3) Transfomer model imports Token Embedding , Landmark Embedding , Encoder-Decoder Class to execute the complete architecture.

Transformer Decoder throws shape error in MultiAttention Head layer.
Work in Progress...

