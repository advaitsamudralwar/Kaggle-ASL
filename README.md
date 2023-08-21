# Google American Sign Language Fingerspelling Recognition Kaggle Research Code Competition

## Approach: Converting Mediapipe Landmarks to Hand Model Images for ASL Fingerspelling Translation

In this exciting Kaggle research code competition focused on American Sign Language (ASL) fingerspelling recognition, we've adopted a multi-step approach leveraging Mediapipe landmarks and innovative preprocessing techniques.

### Mediapipe get_hand Block:
Our initial step involves extracting landmark coordinates from Mediapipe for both right and left hands. These coordinates are then transformed into hand model images of size 256 x 256. This representation forms the foundation for translating ASL fingerspelling to text.

### Preprocess Block:
1. The preprocessing phase extracts coordinates for right hand, left hand, and pose.
2. We intelligently determine the dominant hand, factoring in NaN values. If both hands have NaN values, we randomly select the right hand as the dominant hand.
3. To ensure consistent sequence lengths, blank frames are added to sequences with fewer than 413 frames, aligning all image sequences for each phrase.

### Preprocess Ground Truth Block:
1. We enhance ground truth phrases by padding them with start (<) and end (>) tokens respectively.
2. Furthermore, each phrase is padded with 'p' characters at the end, ensuring uniform length for the training data.

### Split Data Block:
The data is thoughtfully divided into training and validation sets, crucial for robust model evaluation.

### Vision Transformer Block:
1. Token and landmark embeddings are pivotal for effective data representation and positional encoding. This approach facilitates robust input data and ground truth transformation.
2. The core of our approach involves the Encoder-Decoder architecture, enriched with the Transformer model's essence. The Encoder-Decoder class integrates Token Embedding, Landmark Embedding, and the Encoder-Decoder block, delivering a comprehensive architecture.

**Note:** At the moment, the Transformer Decoder encounters a shape error within the MultiAttention Head layer. Rest assured, our team is actively working on resolving this issue, and the solution is a work in progress.


