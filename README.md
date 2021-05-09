# Vision_Transformer
## Paper : An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale
## PDF : https://arxiv.org/pdf/2010.11929

## VisionTransformer.ipynb
기존에 구현했던 model(https://github.com/jo1jun/Transformer/blob/main/Transformer.ipynb) 기반.

ViT 를 논문 참조하여 직접 구현.

## VisualizeAttentionMap.ipynb
MNIST 로 위에서 직접 구현한 model 로 학습 시켜 구한 attention map 을 visualization 해 보았다.

visualize 부분은 아래 code 를 참조하였다.

reference : https://github.com/jeonsworld/ViT-pytorch/blob/main/visualize_attention_map.ipynb

## dataset
CIFAR10
MNIST

## result
### attention example
![image](https://user-images.githubusercontent.com/68524289/117577692-c7dd2f80-b125-11eb-9e50-dee45695f3ab.png)
![image](https://user-images.githubusercontent.com/68524289/117577696-cdd31080-b125-11eb-8040-13fe40bfdba3.png)
![image](https://user-images.githubusercontent.com/68524289/117577699-d0356a80-b125-11eb-9d53-3d974f4067ff.png)
![image](https://user-images.githubusercontent.com/68524289/117577704-d3305b00-b125-11eb-9604-2e1bf99264be.png)
![image](https://user-images.githubusercontent.com/68524289/117577708-d6c3e200-b125-11eb-9326-cfe2bf7cf43c.png)
![image](https://user-images.githubusercontent.com/68524289/117577710-d9bed280-b125-11eb-8362-244dcb67c49f.png)


### accuracy
CIFAR10
  
train accuracy 81.957%

val accuracy 71.700%

test accuracy 70.080%
  
MNIST
  
train accuracy 99.023%

test accuracy 98.330%

## Comment

cifar10 dataset 의 경우 정확도가 그리 높진 않지만, CNN 을 철저히 배제한 transformer 구조로도 image classification 이 가능하다는 것에 의의를 두었고
논문에 나와있듯이 ViT 는 CNN 기반 구조보다 inductive bias 가 약해서 dataset 이 적은 경우 성능이 떨어지지만 
큰 dataset 으로 pre-train 한 경우 CNN 기반 구조(inductive bias)를 능가한다.

attention 을 더 잘 보이게 하기 위해 MNIST 값을 반전시켰다. 숫자부분 값이 0에 가까워져서 숫자 안쪽은 검게 나타나지만, 테두리 부분에서 attention 이 드러난다. 
숫자와 많이 떨어져 있는 부분들은 attention 하지 않으므로 노란색에서 검은색으로 가까워져있다.

핵심 이해 및 구현이 목적이므로 디테일은 추후에 다시 다루어볼 것.

TODO : pre-train & fine-tune 
