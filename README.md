# EMPIR: Ensembles of Mixed Precision Deep Networks for Increased Robustness against Adversarial Attacks
[![Build Status](https://travis-ci.org/tensorflow/cleverhans.svg?branch=master)](https://travis-ci.org/tensorflow/cleverhans)

This repository contains the source code for the paper EMPIR: Ensembles of Mixed Precision Deep Networks for Increased Robustness against Adversarial Attacks ([Accepted at ICLR 2020](https://openreview.net/forum?id=HJem3yHKwH))

It is based on [CleverHans](https://github.com/tensorflow/cleverhans) 1.0.0, a Python library to
benchmark machine learning systems' vulnerability to
[adversarial examples](http://karpathy.github.io/2015/03/30/breaking-convnets/).
You can learn more about such vulnerabilities on the accompanying [blog](http://cleverhans.io).

## Setting up
+ Install [TensorFlow](https://www.tensorflow.org/) 
+ Git clone this repository
+ Set environment variable PYTHONPATH to include this repository `export PYTHONPATH="/path/to/EMPIR":$PYTHONPATH`

We tested this setup on Python X.X, Tensorflow X.X, Ubuntu X.X and a single RTX 2080 Ti GPU 

## Example commands
+ `python examples/mnist_attack.py --nb_samples=10000 --attack_iterations=50 
--wbits=$model1_weight_prec --abits=$model1_activation_prec --wbits2=$model2_weight_prec --abits2=$model2_activation_prec --ensembleThree --model_path1=/path/to/model1/ckpt --model_path2=/path/to/model2/ckpt --model_path3=/path/to/model3/ckpt` - White-Box CW attack on MNISTconv EMPIR model
+ `python examples/mnist_attack.py --nb_samples=10000 --attack_iterations=50 
--model_path=/path/to/baseline/model/ckpt` - White-Box CW attack on MNISTconv baseline model
+ `python examples/cifar10_attack.py --nb_samples=10000 --attack_iterations=50 --abits=$model1_activation_prec --wbits=$model2_weight_prec --abits2=$model2_activation_prec --wbits2=$model2_weight_prec --model_path1=/path/to/model1/ckpt --model_path2=/path/to/model2/ckpt --model_path3=/path/to/model3/ckpt --ensembleThree` - White-Box CW attack on CIFARconv EMPIR model
+ `python examples/cifar10_attack.py --nb_samples=10000 --attack_iterations=50 
--nb_filters=32 --model_path=/path/to/baseline/model/ckpt` - White-Box CW attack on CIFARconv baseline model
+ `python examples/alexnet_attack.py --batch_size=100 --imagenet_path=/path/to/imagenet/tf_records --ensembleThree --abits=$model1_activation_prec --wbits=$model1_weight_prec --abits2=$model2_activation_prec --wbits2=$model2_weight_prec --model_path1=/path/to/model1/ckpt --model_path2=/path/to/model2/ckpt --model_path3=/path/to/model3/ckpt` - White-Box CW attack on AlexNet EMPIR model
+ `python examples/alexnet_attack.py --batch_size=100 --imagenet_path=/path/to/imagenet/tf_records --model_path=/path/to/baseline/model/ckpt` - White-Box CW attack on AlexNet baseline model

## Results
<table>
    <tr align="center">
        <th rowspan="2">Dataset</th>
        <th rowspan="2">Ensemble Type</th>
        <th colspan=3>Precisions</th>
        <th rowspan=2>Unperturbed Accuracy (%)</th>
        <th colspan=4>Adversarial Accuracy (%)</th>
    </tr>
    <tr align="center">
        <th>Model 1</th>
        <th>Model 2</th>
        <th>Model 3</th>
        <th>CW</th>
        <th>FGSM</th>
        <th>BIM</th>
        <th>PGD</th>
    </tr>
    <tr align="center">
       <td>MNIST</td>
       <td> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
    </tr>
    <tr align="center">
       <td>CIFAR-10</td>
       <td> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a></td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
    </tr>
    <tr align="center">
       <td>ImageNet</td>
       <td> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a></td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> abits=4, wbits=2 <a href="https://github.com/sancharisen/cleverhans_EMPIR">Download</a> </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
       <td> 100 </td>
    </tr>
</table>

## Citing this work

```
@inproceedings{
sen2020empir,
title={{\{}EMPIR{\}}: Ensembles of Mixed Precision Deep Networks for Increased Robustness Against Adversarial Attacks},
author={Sanchari Sen and Balaraman Ravindran and Anand Raghunathan},
booktitle={International Conference on Learning Representations},
year={2020},
url={https://openreview.net/forum?id=HJem3yHKwH}
}
```
## Copyright

Copyright 2017 - Google Inc., OpenAI and Pennsylvania State University.
