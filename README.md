# 해석 가능한 잠재변수를 활용한 다음 프레임 예측

## 실험 데이터
1. Moving-Mnist
2. KTH
3. Driving Dataset


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
BetaVAE: build_vgg_encoder + build_translator + build_deep_resnet_vgg_decoder

### 상세 구성
1. build_vgg_encoder
2. build_translator
   - inception_module
3. build_deep_resnet_vgg_decoder
   - identity_block
   - cbam_block
     - channel_attention
     - spatial_attention

![제안하는 모델](https://github.com/jmin07/Next-Frame-Prediction-Using-Beta-VAE/assets/103296979/901e68bc-e060-494a-a654-3585b3b647e5)

