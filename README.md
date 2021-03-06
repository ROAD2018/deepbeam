# Deepbeam
Deep learning based Speech Beamforming

## Requirements
tensorflow, scipy, fftw, h5py

## Train Wavenet-based enhancement model
Noisy input data filename: noisy_train.mat

Dimension:                 [24570, NUM_TOKENS]

Content:                   noisy waveforms

Clean ouput data filename: target_train.mat

Dimension:                 [16384, NUM_TOKENS]

Content:                   256 mu-law quantized bin index of clean waveforms

The above become numpy arrays after loaded into python,
you can generate your own traning data and modify the model architecture accordingly.

To train the enhancement model, place the data in the same directory as the training code,
then execute the following:

python bawn_sp_multi_gpu_train_v2.py /logdir NUM_GPUS

## Demo using pre-trained model
A pre-trained enhancement model using 109 speakers and 100 noises is available in assets.

"demo.ipynb" contains a complete enhancement and beamforming workflow using a short 8-channel noisy speech.

The noisy input is a [length, NUM_CHANNELS] matrix, where each column is a channel. Another input contains only the multi-channel noise itself is required in order to compute signal-to-noise-ratio.
