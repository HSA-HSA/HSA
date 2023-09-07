# Hidden States Attack


## Requirements

- Python 3.6.8
- Keras 2.2.4
- Tensorflow 1.14.0
- Numpy 1.16.2
- Pillow 6.0.0
- Scipy 1.2.1

## Experiments

You should download the  pretrained models from ( https://github.com/tensorflow/models/tree/master/research/slim, and https://github.com/tensorflow/models/tree/archive/research/adv_imagenet_models) before running the code. Then place these model checkpoint files in `./models_tf`.

You should also download the dataset from (https://github.com/jpzhang1810/NAA/tree/master/dataset).

#### Introduction


- `HSA.py` : the implementation for HSA attack.

- `verify.py` : the code for evaluating generated adversarial examples on different models.

#### Layer setting

- inception_v3: InceptionV3/InceptionV3/Mixed_5b/concat

- inception_v4: InceptionV4/InceptionV4/Mixed_5e/concat

- inception_resnet_v2: InceptionResnetV2/InceptionResnetV2/Conv2d_4a_3x3/Relu

- resnet_v2_152: resnet_v2_152/block2/unit_8/bottleneck_v2/add
  

#### Example Usage

##### Generate adversarial examples:

- HSA

```
python HSA.py --model_name inception_v3 --attack_method HSA --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 40 --output_dir ./adv/HSA/
```

- HSA-PD

```
python HSA.py --model_name inception_v3 --attack_method HSAPIDI --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 40 --amplification_factor 2.5 --gamma 0.5 --Pkern_size 3 --prob 0.7 --output_dir ./adv/HSAPIDI/
```


##### Evaluate the attack success rate

```
python verify.py --ori_path ./dataset/images/ --adv_path ./adv/HSA/ 
```


## Acknowledgments

Code refer to: [Feature Importance-aware Attack](https://github.com/hcguoO0/FIA) and [Neuron Attribution-based Attacks](https://github.com/jpzhang1810/NAA)
