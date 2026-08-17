# MOSFET Gate Poly & Oxide Contact 2대 Wet Etch 공정 수율 분석 및 Root Cause 역추적

Monte Carlo 시뮬레이션을 활용한 가상 데이터 확장 및 Machine Learning(Random Forest) 기반의 반도체 습식 식각(Wet Etch)
공정 수율 분석 프로젝트입니다. Gate Poly Etch 및 Oxide Contact Etch 2대 주요 공정 변수를 통합 추적하여 주요 불량 원인을 정량적으로
규명하고 Process Window를 도출합니다.



## 1. 프로젝트 개요 (Overview)

 **목적**: 실습 표본 데이터의 한계를 극복하기 위해 Monte Carlo 시뮬레이션 기반 1,000개 데이터 세트를 구축하고,
  소자 특성 열화(Lg, SS) 및 Contact 저항(Rc)에 미치는 핵심 공정 변수를 역추적함
 **주요 타깃 공정**:
   **Gate Poly Etch**: Poly Etchant 사용, Gate Length(Lg) 변동 및 Short Channel Effect(SCE) 제어
   **Oxide Contact Etch**: HF/BOE 사용, ILD Oxide 개봉 및 접촉 저항(Rc) 제어
 **분석 기법**: Monte Carlo Simulation, Random Forest Classifier, Cpk (공정 능력 지수) 평가



## 2. 주요 기능 및 물리 모델 (Key Features)

### A. Gate Poly Etch 물리 모델
 **Target Lg**: 100 nm (Spec: 90 nm ~ 110 nm)
 **Short Channel Effect (SCE)**: Lg < 90nm 영역 진입 시 Subthreshold Swing(SS) 열화 페널티 적용
 **주요 평가 지표**: Gate 공정 Cpk

### B. Oxide Contact Etch 물리 모델
 **Target Contact CD**: 80 nm / **Target Rc**: <= 100 Ω
 **Under-etch Fail**: 식각 시간 부족 시 Contact hole 미 개봉으로 인한 접촉 저항 지수함수적 증가
 **주요 평가 지표**: Contact 공정 Cpk

### C. ML 기반 Root Cause 역추적 & Process Window
 **Feature Importance**: PR 두께, Develop 시간, Gate Etch 시간, Contact Etch 시간 중 전체 Spec Out(Fail)에
  가장 치명적인 영향 요인 산출
 **Margin Mapping**: Gate Etch Time vs Contact Etch Time 2축 기반 합격/불합격 공정 마진 영역 시각화



## 3. 분석 결과 요약 (Main Results)

1. **Gate Process 능력 (Cpk = 0.52)**: Over-etch로 인한 LSL(90nm) 미달 다이 발생으로 Cpk 저하 (Cpk >= 1.33 대비 개선 필요)
2. **Contact Process 능력 (Cpk = 4.92)**: 접촉 저항 50~60 Ω 수준으로 매우 안정적 산출
3. **Root Cause 도출**: ML 역추적 결과 Gate Etch Time 기여도가 67.1%로 전체 불량의 주원인임을 입증
4. **Process Window 최적 조건**: Gate Poly Etch Time을 190초 이하로 만드는 제어가 수율 확보의 최우선 조건임



