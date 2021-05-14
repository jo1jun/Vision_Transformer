# Vision_Transformer
## Paper : An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale
## PDF : https://arxiv.org/pdf/2010.11929

## VisionTransformer.ipynb
기존에 구현했던 model(https://github.com/jo1jun/Transformer/blob/main/Transformer.ipynb) 기반.

ViT 를 논문 참조하여 직접 구현.

## VisualizeAttentionMap.ipynb
위에서 직접 구현한 model 로 MNIST를 학습 시켜 구한 attention map 을 visualization 해 보았다.

visualize 부분은 아래 code 를 참조하였다.

reference : https://github.com/jeonsworld/ViT-pytorch/blob/main/visualize_attention_map.ipynb

## dataset
VisionTransformer.ipynb : CIFAR10

VisualizeAttentionMap.ipynb : MNIST

## result
### MNIST Attention Map
![image](https://user-images.githubusercontent.com/68524289/117996078-cf4a4600-b37c-11eb-9d6d-c1e872ce0bd9.png)
![image](https://user-images.githubusercontent.com/68524289/117996156-e0935280-b37c-11eb-9a80-982f84886e11.png)
![image](https://user-images.githubusercontent.com/68524289/117996175-e426d980-b37c-11eb-8395-741f5a0506cc.png)

### ViT-B/14-224 Attention Map
![image](https://user-images.githubusercontent.com/68524289/117996596-3e279f00-b37d-11eb-8139-ba09f78a504b.png)
![image](https://user-images.githubusercontent.com/68524289/117996613-41228f80-b37d-11eb-9391-12ee37263343.png)
![image](https://user-images.githubusercontent.com/68524289/117996628-454ead00-b37d-11eb-8717-8135f57b7fac.png)

### accuracy

[Tensorboard](https://tensorboard.dev/experiment/UmmgbIlzQzefEK2i3jCvlQ/)


  
MNIST
  
train accuracy 97.944%

val accuracy 97.790%

test accuracy 97.470%

CIFAR10
  
train accuracy 87.943%

val accuracy 76.000%

test accuracy 74.720%

pretrain & finetune CIFAR10

train accuracy 100.000%

val accuracy 96.600%

test accuracy 96.840%

## Comment

<VisionTransformer.ipynb>

cifar10 dataset 의 경우 정확도가 그리 높진 않다. (매우 단순한 CNN architecture 의 성능인 74.5% 와 비슷한 수준.)

(simple cnn architecture : https://github.com/jo1jun/CS231N/blob/main/assignment2/PyTorch.ipynb at the bottom)

CNN 을 철저히 배제한 transformer 구조로도 image classification 이 가능하다는 것에 의의를 두었다.

논문에 나와있듯이 ViT 는 CNN 기반 구조보다 inductive bias 가 약해서 dataset 이 적은 경우 성능이 떨어진다.

하지만, 큰 dataset 으로 pre-train 한 경우 CNN 기반 구조(inductive bias)를 능가한다.

<VisualizeAttentionMap.ipynb>

attention 을 더 잘 보이게 하기 위해 MNIST 값을 반전시켰다. 

숫자부분 값이 0에 가까워져서 숫자 안쪽은 검게 나타나지만, 테두리 부분에서 attention 이 드러난다. 

숫자와 많이 떨어져 있는 부분들은 attention 하지 않으므로 노란색에서 검은색으로 가까워져있다.

핵심 이해 및 구현이 목적이므로 디테일은 추후에 다시 다루어볼 것.

## TODO
1. pre-train & fine-tune

2.  응용 task 접목

3.  Inductive bias 를 조절하는 idea 구현해보기
