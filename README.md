# Text-Translation
text translation (english->korean)

  We are using many to many model of seq2seq modelling to get output text.
  We are using encoder decoder architecture for the model.

we are using advance RCNN model
what is RCNN model?
R-CNN is a two-stage detection algorithm. The first stage identifies a subset of regions in an image that might contain an object. The second stage classifies the object in each region. Applications for R-CNN object detectors include: Autonomous driving.

The previous output is provided as input to the model to predict next step.
example:'Behave yourself'-처신 잘해.
step 1: add start and end tokens. As initial start value is required in the teacher forcing and end token to make the model understatnd that the sentence is completed

Encoder-Decoder Workflow in NMT(neural machine translation)

Note:
LSTM gives 3 outputs:
output for next layer
Hidden State
Cell State

Procedure:
Encoder LSTM outputs: we only keep the state outputs of encoder LSTM layer as it will contain all the information about the input data.
This states of encoder lstm will be used to initialize the decoder lstm. Also, the [start] token will be provided as first word as we are performing teacher forcing.
The output of this decoder lstm layer will be passed through Dense layer to predict the output word.


Workflow:
Encoder side:
input -> Encoder LSTM -> encoder states
Decoder side:
encoder states + [start] -> Decoder LSTM -> word + decoder states
decoder_states + word -> Decoder LSTM -> word2 + decoder states 2
word2 + decoder states 2 -> Decoder LSTM -> word3 + decoder states 3 ... so on
The process stops when [end] token is predicted
Note2:
There are 2 stages of this model:
Training with english input and french output
inference mode where we will initialize model to take english words and predict french words
