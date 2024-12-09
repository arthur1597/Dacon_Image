# Dacon 이미지 색상화 및 손실 부분 복원 AI 경진대회

## Image inpainting

![image](https://github.com/user-attachments/assets/6535a55b-9299-496d-87c6-487aa919e3bf)
###### 출처: Omar Elharrouss, Noor Almaadeed, Somaya Al-Maadeed, Younes Akbari - [Image inpainting: A review]

##### 손상되거나 열화된 이미지를 원래 상태로 되돌리는 기술로, 노이즈 제거, 흐림 현상 개선, 해상도 향상 등을 말하는 것으로 최근 딥러닝의 발전으로 더욱 정교하고 효율적인 복원 기법들이 개발 되고 있다
---

## 사용한 라이브러리 


---
## < 모델 설계 전략 >
1. 데이터 증강
2. 기존 Unet 구조의 Decoder 부분에 Sementic Segmentation 적용
3. Masking 처리
4. Unet Encoder에 EfficientNet_b7 추가
5. UNet 구조를 기반으로 Model Tuning => 성능이 가장 높게 나옴

## 성능이 가장 높았던 5번 방법
#### optimizer 비교
![image](https://github.com/user-attachments/assets/747073db-0fa8-45c0-af5f-575ef53b6161)
#### LR 비교 
![image](https://github.com/user-attachments/assets/855d0fc8-2baa-40c0-92bf-b3b26c37ddc8)
#### Loss 비교
![image](https://github.com/user-attachments/assets/de14db90-b0eb-436c-86d2-1d83cfdbcd22)

---

### 결국에는 BCELoss와 MSELoss를 사용한 기본 구조가 가장 높고 Optimizer 변경을 한 것이 큰 성능 향상이 있었다
학습LOSS 그래프 시각화 - 중간에 발산하지만 다시 수렴하는 결과값을 볼 수 있음

![image](https://github.com/user-attachments/assets/487eccdf-5776-4d15-96bc-e7c250fb4577)

## 복원 결과 Test -> Prediction

![TEST_002](https://github.com/user-attachments/assets/716367c2-60c2-4054-ad3c-53e179c445ac)
![TEST_002](https://github.com/user-attachments/assets/18fe69ad-5088-4a74-b8b7-a277fa7a2f7f)

