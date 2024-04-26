# 해석 가능한 잠재변수를 활용한 다음 프레임 예측
※ 해당 코드는 구글 코렙(Google Colab)에서 작성 되었습니다.

## 실험 데이터

1. [Moving-Mnist](https://www.cs.toronto.edu/~nitish/unsupervised_video/)
2. [KTH](https://www.csc.kth.se/cvap/actions/)
    - 스톡홀롬 공과대학 제작
3. [Driving Dataset](https://rpg.ifi.uzh.ch/event_driving_datasets.html)
    - 취리히 대학 제작


## 실험 데이터 구성
해당 구성은 Moving MNIST 를 기준
- 학습 데이터
    - 이미지 5장을 하나의 학습 데이터로 구성
    - shape: (5, 64, 64, 1)
- 정답 데이터
    - 이미지 1장을 정답 데이터로 구성
    - shape: (64, 64, 1)

![image](https://github.com/jmin07/Next-Frame-Prediction-Using-Beta-VAE/assets/103296979/1b095194-f35f-472c-b119-1c842228494b)

## 실험 모델
BetaVAE = build_vgg_encoder + build_translator + build_deep_resnet_vgg_decoder

- `BetaVAE`는 클래스(Class)
    - build_vgg_encoder는 함수(Function)
    - build_translator는 함수(Function)
    - build_deep_resnet_vgg_decoder는 함수(Function)

### 상세 구성
VGG / Inception / ResNet 아키텍처 구조로 구성 됨.

1. `build_vgg_encoder`
    - VGG
        - Conv2D
        - AveragePooling2D
        - GroupNormalization
2. `build_translator`
   - Inception
       - 1x1 Conv
       - 3x3 Conv
       - 5x5 Conv
3. `build_deep_resnet_vgg_decoder`
    - ResNet  
       - identity_block
       - cbam_block

![제안하는 모델](https://github.com/jmin07/Next-Frame-Prediction-Using-Beta-VAE/assets/103296979/901e68bc-e060-494a-a654-3585b3b647e5)
