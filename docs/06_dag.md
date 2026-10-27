# Team 5 - DAG 기반 보정집합 설계 및 변수 분류

## 1. 연구 질문 및 추정 목표
- **노출 (X)**: 규칙적 운동 수행 여부 (`exercise`, 1: 비운동군, 2: 규칙적 운동군)
- **결과 (Y)**: 고혈압 유병 여부 (`htn`, 0: 정상, 1: 고혈압)
- **추정 목표**: 규칙적 운동이 고혈압 유병에 미치는 **총효과(Total Effect)** 추정

---

## 2. DAG (인과방향도)
```text
age -> exercise
age -> htn
sex -> exercise
sex -> htn
income -> exercise
income -> htn
smk -> htn
drink -> htn
exercise -> bmi
bmi -> htn
exercise -> htn
