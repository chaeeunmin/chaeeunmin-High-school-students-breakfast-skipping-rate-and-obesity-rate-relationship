
# 11주차 팀 과제: DAG 기반 인과모형 설계 및 복합표본 로지스틱 회귀분석

## C-1. DAG (인과방향도) 및 변수 역할 설계

### 1. 연구 질문 및 추정 목표
* **노출 ($X$)**: 아침식사 결식 (`bf_skip`, 1: 주 5회 이상 결식, 0: 주 0–4회 결식)
* **결과 ($Y$)**: 비만 유병 여부 (`obesity`, 1: $BMI \ge 25\text{ kg/m}^2$, 0: $BMI < 25\text{ kg/m}^2$)
* **추정 목표**: 대한민국 고등학생에서 아침식사 결식이 비만 유병에 미치는 **총효과(Total Effect)** 추정

### 2. 인과 DAG (인과방향도)

```mermaid
graph LR
    SEX["성별 (SEX)"] --> X["아침식사 결식 (bf_skip)"]
    SEX --> Y["비만 유병 (obesity)"]
    GRADE["학년 (GRADE)"] --> X
    GRADE --> Y
    ESES["주관적 경제상태 (E_SES)"] --> X
    ESES --> Y

    X --> SLP["수면충족감 (M_SLP_EN)"]
    SLP --> Y
    X --> PA["신체활동 실천 (PA_TOT)"]
    PA --> Y
    X --> FNE["야식 섭취 (F_NE)"]
    FNE --> Y

    X --> Y
    Y -->|"역방향 인과 (12주차 민감도분석)"| WCMN["체중 조절 시도 (WC_MN)"]
