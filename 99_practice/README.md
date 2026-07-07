# Machine Learning Repository

머신러닝 수업 및 실습 내용을 정리한 저장소입니다.  
기초 개념부터 회귀, 분류, 결정 트리, SVM, 앙상블, 차원 축소, 비지도 학습까지 단계별로 학습합니다.

## 학습 목차

| 폴더 | 내용 |
| --- | --- |
| `01_overview` | 머신러닝 개요, scikit-learn 기본 사용법, KNN 분류 |
| `02_regression` | 전처리, feature engineering, 선형 회귀, 규제 모델, 경사하강법 |
| `03_classification` | 로지스틱 회귀, odds ratio |
| `04_decision_tree_svm` | 결정 트리, SVC, SVR |
| `05_ensemble` | Voting, Bagging, Random Forest, Boosting, Stacking |
| `06_dimentionality_reduction` | PCA, LDA |
| `07_unsupervised_learning` | K-Means 등 비지도 학습 |
| `99_practice` | 종합 실습 문제 |

## 머신러닝 기본 개념

<details>
<summary><strong>머신러닝</strong></summary>

데이터에서 규칙을 학습하여 새로운 데이터에 대한 결과를 예측하는 방법입니다.

</details>

<details>
<summary><strong>기본 용어</strong></summary>

| 용어 | 설명 |
| --- | --- |
| `feature` | 모델이 판단할 때 사용하는 입력값 |
| `target`, `label` | 모델이 맞춰야 하는 정답 |
| `X` | 입력 데이터 모음 |
| `y` | 입력 데이터에 대한 정답 모음 |

</details>

<details>
<summary><strong>학습 방식과 문제 유형</strong></summary>

- **지도 학습**: 정답이 있는 데이터를 이용해 모델을 학습시키는 방식
- **분류**: 정답이 클래스인 문제  
  예: 생선 종류 예측, 와인 종류 예측
- **회귀**: 정답이 연속적인 숫자인 문제  
  예: 주택 가격 예측, 무게 예측

</details>

<details>
<summary><strong>스케일링</strong></summary>

`feature` 값의 범위를 비슷하게 맞추는 전처리 과정입니다.

한 feature의 값 범위가 다른 feature보다 지나치게 크면, 해당 feature가 모델의 판단을 과도하게 지배할 수 있습니다. 이를 방지하기 위해 스케일링을 사용합니다.

</details>

## 주요 모델 정리

<details>
<summary><strong>KNN</strong></summary>

새 데이터와 가까운 이웃 데이터를 이용해 예측하는 모델입니다.

- **분류**: 가까운 이웃들의 다수결로 class 예측
- **회귀**: 가까운 이웃들의 평균값으로 예측

</details>

<details>
<summary><strong>선형 회귀</strong></summary>

입력값과 정답 사이의 관계를 직선 또는 선형식으로 표현하는 모델입니다.

- 주요 개념: 기울기, 가중치, 절편, 회귀계수
- **다중 선형 회귀**: feature가 여러 개인 선형 회귀 모델
- 여러 입력값을 함께 사용해 target을 예측합니다.

</details>

<details>
<summary><strong>과적합과 과소적합</strong></summary>

| 구분 | 설명 |
| --- | --- |
| 과소적합 | 모델이 훈련 데이터도 충분히 학습하지 못해 예측 성능이 떨어지는 상태 |
| 과대적합 | 모델이 훈련 데이터에 지나치게 맞춰져 새 데이터에 대한 예측 성능이 떨어지는 상태 |

</details>

<details>
<summary><strong>규제 선형 모델</strong></summary>

모델이 너무 복잡해지지 않도록 회귀계수에 벌점을 주는 방법입니다.

| 모델 | 설명 |
| --- | --- |
| L1, Lasso | 일부 계수를 0으로 만듦 |
| L2, Ridge | 계수를 작게 제한하도록 벌점 부여 |
| Elastic Net | L1과 L2 규제를 함께 사용 |

</details>

<details>
<summary><strong>로지스틱 회귀</strong></summary>

이름에는 회귀가 들어가지만 실제로는 분류 모델입니다.

선형 방정식의 결과를 `sigmoid` 또는 `softmax` 함수에 통과시켜 클래스를 예측합니다.

</details>

<details>
<summary><strong>결정 트리</strong></summary>

데이터를 feature 조건에 따라 나누면서 예측하는 모델입니다.

- **분류**: 분할된 리프 노드 sample의 다수결로 class 예측
- **회귀**: 분할된 리프 노드 sample의 평균값으로 예측
- **가지치기**: 트리가 지나치게 복잡해지는 것을 막아 과대적합을 방지
  - 주요 파라미터: `max_depth`, `min_samples_leaf`, `min_samples_split`

</details>

<details>
<summary><strong>SVM</strong></summary>

class를 나누는 결정 경계를 찾는 모델입니다.

- 핵심 목표: 마진이 넓은 결정 경계를 찾는 것
- 주요 파라미터: `C`, `kernel`, `gamma`

</details>


## 앙상블

여러 모델을 함께 사용해 더 안정적인 예측을 만드는 기법입니다. 일반적으로 단일 모델보다 성능이 좋아지는 경우가 많습니다.

<details>
<summary><strong>Voting</strong></summary>

여러 모델의 예측을 투표로 합치는 방식입니다.

- **Hard Voting**: class 예측값으로 투표
- **Soft Voting**: class 확률의 평균으로 예측

</details>

<details>
<summary><strong>Bagging</strong></summary>

같은 모델을 여러 개 만들고 결과를 합치는 방식입니다.

- 각 모델은 bootstrap sampling 방식으로 데이터를 추출해 학습합니다.

</details>

<details>
<summary><strong>Random Forest</strong></summary>

Bagging을 결정 트리에 적용한 대표적인 앙상블 모델입니다.

- 데이터와 feature를 랜덤으로 선택해 여러 트리를 학습합니다.
- `feature_importance`를 통해 모델이 중요하게 본 feature를 확인할 수 있습니다.

</details>

<details>
<summary><strong>Boosting</strong></summary>

이전 모델의 틀린 부분, 즉 오차를 다음 모델이 보완하는 방식입니다.

- 여러 약한 모델을 순차적으로 학습시켜 강한 모델을 만듭니다.

</details>

<details>
<summary><strong>AdaBoost</strong></summary>

틀린 샘플의 가중치를 높여 다음 모델이 더 집중해서 학습하도록 만드는 방식입니다.

- 학습이 끝나면 모델별 신뢰도 가중치를 부여합니다.

</details>

<details>
<summary><strong>Gradient Boosting</strong></summary>

이전 모델의 오차를 다음 모델이 줄여 나가는 방식입니다.

- 대표 라이브러리: XGBoost, CatBoost, LightGBM

</details>

<details>
<summary><strong>Stacking</strong></summary>

여러 기본 모델의 예측 결과를 모아 최종 모델이 다시 학습하는 방식입니다.

</details>

## 차원 축소

많은 feature를 더 적은 수의 feature 또는 새로운 축으로 줄이는 과정입니다. feature 수를 줄이면서 데이터의 중요한 구조와 패턴은 최대한 유지하는 것이 목표입니다.

<details>
<summary><strong>차원의 저주</strong></summary>

feature가 많아질수록 고차원 공간에서 데이터가 드문드문 퍼져 보이는 현상입니다.

- 데이터 수에 비해 feature가 너무 많으면 거리 계산의 의미가 약해질 수 있습니다.
- KNN, SVM, KMeans처럼 거리나 위치를 활용하는 모델에서 특히 영향을 받을 수 있습니다.
- 의미 없는 noise feature가 많을수록 모델 성능과 해석이 어려워질 수 있습니다.

</details>

<details>
<summary><strong>Feature Extraction과 Feature Selection</strong></summary>

| 구분 | 설명 | 예시 |
| --- | --- | --- |
| Feature Extraction | 기존 feature를 조합해 새로운 feature를 만듦 | PCA, LDA |
| Feature Selection | 기존 feature 중 중요한 feature만 선택함 | 중요 컬럼 선택 |

</details>

<details>
<summary><strong>PCA</strong></summary>

`PCA(Principal Component Analysis)`는 원본 feature를 조합해 데이터의 분산을 가장 잘 설명하는 새 축을 찾는 비지도 차원축소 방법입니다.

- `PC1`: 원본 데이터의 변동을 가장 많이 설명하는 첫 번째 주성분
- `PC2`: `PC1`과 겹치지 않으면서 남은 변동을 가장 많이 설명하는 두 번째 주성분
- `explained_variance_ratio_`: 각 주성분이 원본 데이터의 변동을 얼마나 설명하는지 나타내는 비율
- target 없이 `X`만 사용합니다.

</details>

<details>
<summary><strong>PCA 주요 처리 흐름</strong></summary>

1. feature 스케일을 맞춥니다.
2. `PCA(n_components=2)`처럼 줄일 차원 수를 정합니다.
3. train 데이터에 `fit_transform()`을 적용해 주성분 방향을 학습하고 변환합니다.
4. test 데이터에는 train에서 배운 기준으로 `transform()`만 적용합니다.
5. `explained_variance_ratio_`로 정보가 얼마나 유지되는지 확인합니다.

</details>

<details>
<summary><strong>LDA</strong></summary>

`LDA(Linear Discriminant Analysis)`는 class가 잘 구분되는 방향을 찾는 지도학습 기반 차원축소 방법입니다.

- PCA와 달리 target class를 사용합니다.
- class 간 거리는 멀게, class 내부 데이터는 가깝게 만드는 축을 찾습니다.
- 분류 문제에서 class 분리 시각화나 전처리에 사용할 수 있습니다.
- target이 없는 데이터에는 사용할 수 없습니다.

</details>

<details>
<summary><strong>PCA와 LDA 비교</strong></summary>

| 구분 | PCA | LDA |
| --- | --- | --- |
| target 사용 | 사용하지 않음 | 사용함 |
| 학습 방식 | 비지도 차원축소 | 지도학습 기반 차원축소 |
| 찾는 방향 | 데이터 분산이 큰 방향 | class가 잘 구분되는 방향 |
| 주요 목적 | 구조 파악, 시각화, 압축 | class 분리 시각화, 분류 전처리 |
| target 없는 데이터 | 사용 가능 | 사용 불가 |

</details>

<details>
<summary><strong>데이터 누수 주의</strong></summary>

모델 평가를 할 때는 train/test를 먼저 나눈 뒤, 스케일러와 차원축소 모델을 train 데이터에만 `fit`해야 합니다.

- train 데이터: `fit_transform()`
- test 데이터: `transform()`

test 데이터까지 함께 `fit`하면 평가 데이터의 정보가 학습 과정에 들어가 데이터 누수가 발생할 수 있습니다.

</details>

## 비지도 학습과 군집화

정답 `y` 없이 feature `X`만 보고 데이터 안의 구조나 패턴을 찾는 학습 방식입니다.

- **군집화**: 비슷한 데이터끼리 그룹으로 묶음
- **차원축소**: 많은 feature를 적은 축으로 줄여 구조를 보기 쉽게 만듦
- **이상치 탐지**: 대부분의 데이터와 다른 특이한 데이터를 찾음

<details>
<summary><strong>군집화</strong></summary>

비슷한 데이터끼리 같은 그룹으로 묶는 비지도 학습 방법입니다. 이때 만들어진 그룹을 `cluster`, 즉 군집이라고 부릅니다.

- 군집 번호는 정답 class가 아니라 모델이 붙인 임의의 그룹 이름입니다.
- 군집 결과는 군집별 평균, 분포, 특징을 확인한 뒤 사람이 해석해야 의미가 생깁니다.
- 고객 세분화, 문서/이미지 탐색, 이상치 탐지 전 사전 분석 등에 사용할 수 있습니다.

</details>

<details>
<summary><strong>KMeans</strong></summary>

`KMeans`는 데이터를 `k`개의 군집으로 나누는 대표적인 군집화 알고리즘입니다.

- `K`: 만들 군집의 개수
- `Means`: 각 군집의 평균 위치, 즉 중심점 `centroid`
- 정답 class를 맞히는 분류 모델이 아니라, feature 값이 가까운 데이터끼리 묶는 비지도 학습 모델입니다.

</details>

<details>
<summary><strong>KMeans 동작 흐름</strong></summary>

1. 사람이 먼저 군집 개수 `k`를 정합니다.
2. 모델이 각 군집을 대표할 중심점 `centroid`를 잡습니다.
3. 각 데이터는 가장 가까운 중심점에 배정됩니다.
4. 같은 군집에 배정된 데이터들의 평균 위치로 중심점이 이동합니다.
5. 군집 배정과 중심점 위치가 거의 바뀌지 않을 때까지 반복합니다.

</details>

<details>
<summary><strong>KMeans 주요 용어</strong></summary>

| 용어 | 설명 |
| --- | --- |
| `n_clusters` | 만들 군집의 개수 `k` |
| `centroid` | 각 군집의 중심점 |
| `cluster label` | 각 샘플에 붙은 군집 번호 |
| `inertia` | 각 샘플과 자기 군집 중심점 사이 거리 제곱합 |
| `fit_predict()` | 중심점을 학습하고 각 샘플의 군집 번호를 반환 |

</details>

<details>
<summary><strong>KMeans 주의점</strong></summary>

- 거리 기반 알고리즘이므로 스케일링이 중요합니다.
- 학습에는 `X`만 사용하고 `y`는 사용하지 않습니다.
- `cluster 0`, `cluster 1` 같은 번호는 정답 이름이 아니라 임의의 군집 번호입니다.
- 원형에 가깝고 크기가 비슷한 군집에는 잘 맞지만, 복잡한 모양이나 밀도가 다른 군집에는 한계가 있습니다.

</details>

<details>
<summary><strong>Elbow Method</strong></summary>

`inertia`를 이용해 적절한 `k` 후보를 찾는 방법입니다.

- `k`가 커지면 중심점이 많아지므로 `inertia`는 보통 감소합니다.
- 감소 폭이 갑자기 완만해지는 지점을 `Elbow`, 즉 팔꿈치 지점으로 봅니다.
- 정확한 정답을 알려주는 방법은 아니며, 그래프가 뚜렷하게 꺾이지 않을 수도 있습니다.

</details>

<details>
<summary><strong>Silhouette Score</strong></summary>

군집이 안쪽으로는 잘 뭉쳐 있고, 바깥쪽으로는 잘 떨어져 있는지 확인하는 지표입니다.

| 값 | 해석 |
| --- | --- |
| 1에 가까움 | 자기 군집에 잘 속해 있고 다른 군집과도 잘 떨어져 있음 |
| 0 근처 | 두 군집 사이 경계에 있어 애매함 |
| 음수 | 자기 군집보다 다른 군집에 더 가까울 수 있음 |

</details>

<details>
<summary><strong>k 선택 기준</strong></summary>

최종 `k`는 하나의 지표만 보고 결정하지 않고, 여러 기준을 함께 고려합니다.

- Elbow Method의 `inertia` 감소 폭
- Silhouette Score
- PCA 2차원 시각화 결과
- 군집별 feature 평균과 해석 가능성
- 업무나 수업 목적에서 필요한 그룹 수

</details>
