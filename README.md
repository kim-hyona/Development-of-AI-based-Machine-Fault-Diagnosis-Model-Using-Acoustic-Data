 # 기계고장진단AI모델개발


------
이 프로젝트를 계기로 Hitachi 데이터셋을 이용해 FFT를 통해 주파수 도메인 데이터를 생성하고, Isolation Forest 알고리즘으로 이상치를 탐지하였으며, SHAP을 사용하여 모델의 해석 가능성을 높였습니다. 
또한 발된 모델은 높은 정확도와 안정성을 보이며, 기계 고장 진단 시스템으로 활용될 수 있음을 확인하였습니다.


#데이터셋소개
----------


활용된 데이터셋은 Hitachi 주식회사에서 제공된 음향 데이터를 사용하였다. 데이터셋은 학습(train) 데이터와 테스트(test) 데이터로 구성되어 있으며, 학습 데이터는 1279개의 팬 소리 샘플을 포함하고 있습니다.


#데이터 특징 추출 (FFT 고속푸리의 변환)
--------
1.상단 플롯: 단일 오디오 신호 (Single Audio Signal)

+ 이 플롯은 시간 영역에서 오디오 신호의 파형을 나타냅니다.


+ x축: 시간 (샘플 단위, 보통 초나 밀리초)


+ y축: 진폭 (Amplitude)


+ 플롯의 전체 모양을 보면, 신호가 일정한 시간 동안 지속되며, 진폭이 시간에 따라 변동하는 것을 볼 수 있습니다. 이는 원시 오디오 데이터를 그대로 시각화한 것입니다.




2.중간 플롯: FFT 변환된 오디오 신호 (FFT of Audio Signal)


+ 이 플롯은 오디오 신호의 주파수 성분을 나타내기 위해 푸리에 변환(FFT)을 적용한 결과입니다.


+ x축: 주파수 (Frequency)


+ y축: 진폭 (Magnitude)


+ 플롯의 왼쪽 부분에 여러 피크가 보이며, 이는 특정 주파수에서 강한 성분을 나타냅니다. 오른쪽으로 갈수록 주파수 성분이 약해지는 것을 볼 수 있습니다. 이러한 피크는 신호에서 주된 주파수 성분을 시각적으로 보여줍니다.




3.하단 플롯: Mel 스펙트로그램 (Mel Spectrogram of Audio Signal)


+ 이 플롯은 시간과 주파수의 변화를 동시에 시각화한 Mel 스펙트로그램입니다.


+ x축: 시간 (초 단위)


+ y축: 주파수 (Mel 스케일)


+ 색상: 신호의 세기 (Amplitude, dB 단위)


+ 색상 막대를 보면, 색상은 신호의 강도를 나타냅니다. 일반적으로 밝은 색상은 높은 에너지를, 어두운 색상은 낮은 에너지를 나타냅니다.


+ 스펙트로그램은 시간에 따른 주파수 성분의 변화를 보여주며, 오디오 신호의 패턴을 분석하는 데 유용합니다.




![image](https://github.com/kim-hyona/Development-of-AI-based-Machine-Fault-Diagnosis-Model-Using-Acoustic-Data/assets/148624727/d936adfa-aa2b-4ac2-89a6-7a0d5c0a76a3)





# Isolation Forest 모델 학습 (PCA, Z-score 적용)
-----

![image](https://github.com/kim-hyona/Development-of-AI-based-Machine-Fault-Diagnosis-Model-Using-Acoustic-Data/assets/148624727/4682422f-88c8-40bc-acb2-93dd213a8a4d)

모델 학습 결과 

+ 평가 점수: 모델이 0.9992181391712275의 뛰어난 성능 점수를 기록했습니다. 이 점수는 정확도 또는 F1 스코어와 같은 평가 지표일 가능성이 큽니다.
+ Best model_0 score: model_0의 최고 점수는 0.9992181391712275입니다.
+ Best model_2 score: model_2의 최고 점수는 0.9992181391712275입니다.

  
**이 결과는 model_0과 model_2가 사용된 평가 지표에서 거의 완벽한 성능을 달성했음을 나타내며, 훈련된 모델의 효과성을 입증합니다.**



