---
title: "CRASH: Raw Audio Score-based Generative Modeling for Controllable High-resolution Drum Sound Synthesis"
layout: default
---

On this page, we present audios and plots in order to illustrate our paper. We recommend you to wear headphones in order to hear all the subtleties.
# Listening to the dataset
Here are 200 drum sounds from the dataset (the lengths of the audio are restricted from 21000 to 12000):
<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/200_drums_train_set.wav" type="audio/wav"> </audio>

# Unconditioned Generation via SDE discretization

Here are 3 drum sounds (Snare, Kick and HiHat) with their waveform plots generated via discretization of SDE with 400 steps.

<img src="{{ site.baseurl }}/assets/images/snare_1.png"
                    alt="" width="50%" height="50%"> 

<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/snare_1.wav" type="audio/wav"> </audio>

<img src="{{ site.baseurl }}/assets/images/kick_2.png"
                    alt="" width="50%" height="50%"> 

<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/kick_2.wav" type="audio/wav"> </audio>

<img src="{{ site.baseurl }}/assets/images/hat_1.png"
                    alt="" width="50%" height="50%"> 

<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/hat_1.wav" type="audio/wav"> </audio>



Here are 200 drum sounds generated via ODE discretization (sub-VP-1_1 schedule and 400 steps of discretization): 

<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/200_generated_drums.wav" type="audio/wav"> </audio>

We note that the generated samples are less diverse than in the original dataset. This is not dramatic
because the most interesting applications are in the domain of interactive sound design.
# Interpolations in the latent space x(T) via ODE discretization

Here is a schema to explain the interpolation process:

<img src="{{ site.baseurl }}/assets/images/interpolation_schema.png"
                    alt="" width="50%" height="50%"> 

We provide the associated sounds:

The HiHat (x1): <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_hat.wav" type="audio/wav"></audio>, The snare (x2): <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_snare.wav" type="audio/wav"></audio>

The associated noises (be careful if you are wearing headphones, it might be loud!): <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_noise_hat.wav" type="audio/wav"></audio>, <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_noise_snare.wav" type="audio/wav"></audio>

The interpolations (the first and the last one are the reconstruction of the 2 original sounds): <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_4.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_5.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_6.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_7.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_8.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_9.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1_10.wav" type="audio/wav"></audio>

Click here if you want to hear the 11 sounds in a row: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_1.wav" type="audio/wav"></audio>
## Second Interpolation
This is an interpolation between two kicks, you can see that the interpolation attenuates at different levels the "saturated vibration" of the second kick. Once again, we let you appreciate the quality of the reconstruction of the first and last sound.

Kick 1: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_kick_1.wav" type="audio/wav"></audio>, Kick 2: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_kick_2.wav" type="audio/wav"></audio>

Interpolations: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_4.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_5.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_6.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_7.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_8.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_9.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2_10.wav" type="audio/wav"></audio>

Click here if you want to hear the 11 sounds in a row: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/interpolations/interpolation_2.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/interpolation_2.png"
                    alt="" width="100%" height="100%"> 

# Inpainting

Imagine that you don't like a part of a drum sound, you can regenerate the desired part by fixing the part you like (readjusted with the accurate noise level at each step) during inference time. All the presented examples are from the test set. For each example, the first sound is the original sound and the following are inpainted versions.
## Kick Inpainting 1

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_inpainting_orig.png"
                    alt="" width="40%" height="40%">  <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_inpainting_0.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_2.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_4.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_inpainting_5.wav" type="audio/wav"></audio>

## Kick Inpainting 2

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_2_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_2_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_2_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_2_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_2_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_2_inpainting_2.wav" type="audio/wav"></audio>

## Kick Inpainting 3

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_3_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_3_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_3_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_3_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_3_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_3_inpainting_2.wav" type="audio/wav"></audio>

## Kick Inpainting 4

Note that if the original waveform is thick, the generated part is also thick.

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_4_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_4_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_4_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_4_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_4_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_4_inpainting_2.wav" type="audio/wav"></audio>

## Kick Inpainting 5

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_5_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_5_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/kick_5_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_5_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_5_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/kick_5_inpainting_2.wav" type="audio/wav"></audio>

## Snare Inpainting 1

<img src="{{ site.baseurl }}/assets/images/inpainting/snare_2_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_2_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/snare_2_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_2_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_2_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_2_inpainting_2.wav" type="audio/wav"></audio>

## Snare Inpainting 2

<img src="{{ site.baseurl }}/assets/images/inpainting/snare_3_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_3_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/snare_3_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_3_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_3_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/snare_3_inpainting_2.wav" type="audio/wav"></audio>

## Snare Inpainting 3

<img src="{{ site.baseurl }}/assets/images/inpainting/clap_2_inpainting_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/clap_2_inpainting_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/clap_2_inpainting.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/clap_2_inpainting_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/clap_2_inpainting_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/clap_2_inpainting_2.wav" type="audio/wav"></audio>

## Snare Inpainting 4

<img src="{{ site.baseurl }}/assets/images/inpainting/inpainting_resonnant_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/inpainting_resonnant_orig.wav" type="audio/wav"></audio>

<img src="{{ site.baseurl }}/assets/images/inpainting/inpainting_resonnant.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/inpainting_resonnant_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/inpainting_resonnant_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/inpainting/inpainting_resonnant_2.wav" type="audio/wav"></audio>

# Obtaining Variations of a Sound by Noising it and Denoising it via SDE

Let's take a sound x(0) of the test set. We can noise it at a t level (associated to a value of σ): \\[ \mathbb{x}(t) = m(t) \mathbb{x}(0) + \sigma(t) \epsilon \\]
where Ɛ is an isotropic Gaussian 

Then, we perform SDE denoising from t to 0 and we obtain variations of the sound.

The more σ is big, the more the variations are diverse. 

## Cymbal Variations

The original: 

<img src="{{ site.baseurl }}/assets/images/variations/cymbal_variations_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_orig.wav" type="audio/wav"></audio>

For σ=0.1 and a VP schedule.

<img src="{{ site.baseurl }}/assets/images/variations/cymbal_variations_multiple.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_4.wav" type="audio/wav"></audio>

All in a row:<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/cymbal_variations_multiple.wav" type="audio/wav"></audio>

## Snare Variations

The original: 

<img src="{{ site.baseurl }}/assets/images/variations/snare_variations_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_orig.wav" type="audio/wav"></audio>

For σ=0.1 and a VP schedule.

<img src="{{ site.baseurl }}/assets/images/variations/snare_variations_0.1.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1_4.wav" type="audio/wav"></audio>

All in a row:<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.1.wav" type="audio/wav"></audio>

For σ=0.2 and a VP schedule.

<img src="{{ site.baseurl }}/assets/images/variations/snare_variations_0.2.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2_4.wav" type="audio/wav"></audio>

All in a row:<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.2.wav" type="audio/wav"></audio>

For σ=0.4 and a VP schedule.

<img src="{{ site.baseurl }}/assets/images/variations/snare_variations_0.4.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4_4.wav" type="audio/wav"></audio>

All in a row:<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.4.wav" type="audio/wav"></audio>

For σ=0.7 and a VP schedule.

<img src="{{ site.baseurl }}/assets/images/variations/snare_variations_0.4.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7_4.wav" type="audio/wav"></audio>

All in a row:<audio controls preload="none" src="{{ site.baseurl }}/assets/audio/variations/snare_variations_0.7.wav" type="audio/wav"></audio>


# Class-Conditioning and Class-Mixing with a Classifier via ODE

We separately trained a noise-conditioned classifier to recognize the class of a sound at different noise levels σ. Then we can generate sounds from only one class and even mix them !

For instance, this is a cymbal from the test set:

<img src="{{ site.baseurl }}/assets/images/class/class_hat_orig.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_hat_orig.wav" type="audio/wav">

When we use the forward ODE to obtain its latent representation and do the backward ODE with a kick-class constraint, we obtain a "kicky" version of it:

<img src="{{ site.baseurl }}/assets/images/class/class_hat_kick_converted.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_hat_kick_converted.wav" type="audio/wav">

Now, here are the kick, snare and cymbal versions when running backward the constrained ODE starting from a random noise:

<img src="{{ site.baseurl }}/assets/images/class/kick_snare_hat_classifier.png"
                    alt="" width="100%" height="100%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/kick_snare_hat_classifier.wav" type="audio/wav">

Here are the results of the class-mixing, with different weightings:

\\[ \lambda_\text{kick}=0, \lambda_\text{snare}=1, \lambda_\text{cymbal}=0 \\]
\\[ \lambda_\text{kick}=0.2, \lambda_\text{snare}=0.8, \lambda_\text{cymbal}=0 \\]
\\[ ... \\]
\\[ \lambda_\text{kick}=1, \lambda_\text{snare}=0, \lambda_\text{cymbal}=0 \\]
<img src="{{ site.baseurl }}/assets/images/class/class_mixing_5_steps.png"
                    alt="" width="100%" height="100%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_mixing_5_steps.wav" type="audio/wav">


Now, we can operate a more subtle weighting in order to "snarify" a bit the kick:


\\[ \lambda_\text{kick}=0.95, \lambda_\text{snare}=0.05, \lambda_\text{cymbal}=0 \\]

<img src="{{ site.baseurl }}/assets/images/class/95_kick_5_snare.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/95_kick_5_snare.wav" type="audio/wav">



\\[ \lambda_\text{kick}=0.9, \lambda_\text{snare}=0.1, \lambda_\text{cymbal}=0 \\]

<img src="{{ site.baseurl }}/assets/images/class/90_kick_10_snare.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/90_kick_10_snare.wav" type="audio/wav">



\\[ \lambda_\text{kick}=0.85, \lambda_\text{snare}=0.15, \lambda_\text{cymbal}=0 \\]

<img src="{{ site.baseurl }}/assets/images/class/85_kick_15_snare.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/85_kick_15_snare.wav" type="audio/wav">

# Obtaining Variations of a sound by Noising it and applying Class-Mixing Denoising via SDE

Like in the paragraph "Obtaining Variations of a Sound by Noising it and Denoising it via SDE", we add noise to our sound: \\[ \mathbb{x}(t) = m(t) \mathbb{x}(0) + \sigma(t) \epsilon \\]

Then, we denoise it with the class conditional SDE in order to orient the variations of the sound to a particular class or mix of classes:

## Cymbal

Original: 

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_cymbal_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_orig.wav" type="audio/wav"></audio>

Variations with σ=0.5 in the snare class:

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_cymbal_100_snare_0.5_multiple.png"
                    alt="" width="100%" height="100%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple_0.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple_1.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple_2.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple_3.wav" type="audio/wav"></audio><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple_4.wav" type="audio/wav"></audio>

All in a row: <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5_multiple.wav" type="audio/wav"></audio>

Another variation

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_cymbal_100_snare_0.5.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.5.wav" type="audio/wav"></audio>

Another with σ=0.6 in the snare class:

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_cymbal_100_snare_0.6.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_cymbal_100_snare_0.6.wav" type="audio/wav"></audio>

## From HiHat to Kick

Original: 

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_hat_100_snare_0.6_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_hat_100_snare_0.6_orig.wav" type="audio/wav"></audio>

One variation with σ=0.6 in the kick class:

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_hat_100_snare_0.6_0.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_hat_100_snare_0.6_0.wav" type="audio/wav"></audio>

It seems that the model keeps the length, the shape and the percussive aspect of the sound.

## From Kick to Snare

Original: 

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_kick_100_snare_0.95_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_kick_100_snare_0.95_orig.wav" type="audio/wav"></audio>

It is difficult to change the class of a kick because of its thin and low frequency waveform even with σ=0.95

When trying to change a kick to a snare, it makes the sound a bit higher

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_kick_100_snare_0.95.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_kick_100_snare_0.95.wav" type="audio/wav"></audio>

## Mixing the classes from a Snare

The Snare is here noised at the level σ=0.8. Then we show the effect of differents weightings of the classes:

Original:

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_snare_50_kick_50_snare_0.8_orig.png"
                    alt="" width="40%" height="40%"> <audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_snare_50_kick_50_snare_0.8_orig.wav" type="audio/wav"></audio>


\\[ \lambda_\text{kick}=0.0, \lambda_\text{snare}=0.05, \lambda_\text{cymbal}=0.95 \\]

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_snare_5_hat_95_snare_0.8.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_snare_5_hat_95_snare_0.8.wav" type="audio/wav">

\\[ \lambda_\text{kick}=0.8, \lambda_\text{snare}=0.2, \lambda_\text{cymbal}=0 \\]

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_snare_20_kick_80_snare_0.8.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_snare_20_kick_80_snare_0.8.wav" type="audio/wav">

\\[ \lambda_\text{kick}=0.5, \lambda_\text{snare}=0.5, \lambda_\text{cymbal}=0 \\]

<img src="{{ site.baseurl }}/assets/images/class/class_predictor_snare_50_kick_50_snare_0.8.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_snare_50_kick_50_snare_0.8.wav" type="audio/wav">


<img src="{{ site.baseurl }}/assets/images/class/class_predictor_snare_50_kick_50_snare_0.8_2.png"
                    alt="" width="40%" height="40%"><audio controls preload="none" src="{{ site.baseurl }}/assets/audio/class/class_predictor_snare_50_kick_50_snare_0.8_2.wav" type="audio/wav">


