---
title: 선형대수학 학습 목차
date: 2026-05-17 14:00:00 +0900
categories: [Math, Linear Algebra]
tags: [linear-algebra, ai, deep-learning, gnn]
---

# 선형대수학 학습 목차

> Gilbert Strang 식 기하학적 접근 + AI/딥러닝 응용을 염두에 둔 자기주도 학습 커리큘럼.

---

## 0단계: 워밍업 — 왜 선형인가?

- **벡터의 두 얼굴**: 좌표(숫자 묶음) vs 화살표(공간의 점). 두 관점을 자유롭게 오가는 훈련.
- **행렬의 두 얼굴**: 숫자 표 vs 공간을 변형하는 함수.

> 학습 동기: 3Blue1Brown "Essence of Linear Algebra" 1~3편 시청 권장.

---

## 1단계: 벡터 공간과 선형 변환 (The Geometry)

> "행렬 = 공간을 비트는 함수"라는 직관 확립.

- **선형 결합(Linear Combination)과 생성(Span)**: 도달 가능한 영역을 시각화.
- **선형 독립(Linear Independence)**: 정보 중복 없는 최소 단위 찾기.
- **기저(Basis)와 차원(Dimension)**: 공간을 표현하는 좌표계 선택.
- **선형 변환(Linear Transformation)**: 변환의 핵심 성질 $T(av+bw)=aT(v)+bT(w)$.
- **행렬 곱셈 = 변환의 합성**: $AB$ 가 왜 비가환인지 기하적으로 이해.
- **기저 변환(Change of Basis)**: 같은 변환을 다른 좌표계에서 표현.

---

## 2단계: 선형 시스템과 부분공간의 구조 (The Fundamental Structure)

> $Ax = b$ 의 해 구조를 완전히 해부.

- **가우스 소거법과 LU 분해**: 계산 알고리즘과 수치적 효율성.
- **역행렬(Inverse)과 가역성(Invertibility)**: 어떤 변환이 되돌릴 수 있는가?
- **랭크(Rank)와 자유도**: 행렬이 담고 있는 실제 정보량.
- **네 가지 근본 부분공간(Four Fundamental Subspaces)**: 행공간 / 열공간 / 영공간 / 좌영공간 — Strang의 핵심 다이어그램.
- **Invertible Matrix Theorem**: 가역성·랭크·영공간·행렬식의 동치 명제 정리.

---

## 3단계: 직교성과 투영 (The Projections)

> 거리·각도·근사 — 데이터 분석의 시작점.

- **내적(Inner Product)과 노름(Norm)**: 길이와 각도의 일반화.
- **직교성(Orthogonality)과 직교 여공간(Orthogonal Complement)**.
- **투영(Projection)과 최소제곱법(Least Squares)**: 해가 없는 방정식의 "최선의 답".
- **Gram-Schmidt 과정과 QR 분해**: 직교 기저 구성 알고리즘.

> 응용: 회귀 분석, 신호 잡음 제거.

---

## 4단계: 행렬식과 고윳값 (The Spectral Theory)

> 행렬의 "본질"을 추출.

- **행렬식(Determinant)**: 부피 변화율 / 가역성 판정 / 부호 있는 양.
- **특성방정식** $\det(A-\lambda I) = 0$.
- **고윳값(Eigenvalue)과 고유벡터(Eigenvector)**: 변환에서 방향이 보존되는 축.
- **대각화(Diagonalization)**: $A = PDP^{-1}$ — 거듭제곱·미분방정식·마르코프 체인 해결.
- **대칭 행렬의 스펙트럼 정리(Spectral Theorem)**: 실수 고윳값 + 직교 고유벡터 보장.
- **그래프 라플라시안(Graph Laplacian)**: 네트워크 구조와 커뮤니티 분석 (GNN 연결고리).

---

## 5단계: SVD와 행렬 분해의 응용 (The Universal Tool)

> 모든 행렬에 통하는 분해.

- **특잇값 분해(SVD)**: $A = U\Sigma V^T$ — 4가지 부분공간의 직교 기저를 한 번에 제공.
- **저랭크 근사(Low-Rank Approximation)**: 데이터 압축, 추천 시스템, 임베딩 압축의 원리.
- **주성분 분석(PCA)**: SVD의 통계적 응용.
- **양의 정부호 행렬(Positive Definite Matrix)**: 최적화의 볼록성·Hessian과 극값 판정.
- **이차 형식(Quadratic Form)과 에너지 함수**.

---

## 부록 A: 행렬 미적분 (For Deep Learning)

- **그래디언트와 야코비안(Jacobian)** — 벡터 함수의 도함수.
- **연쇄 법칙(Chain Rule)의 행렬 표기** — 역전파의 수식적 근거.
- **헤시안(Hessian)** — 2차 근사와 뉴턴법.

---

## 부록 B: 다차원 데이터 구조

- **텐서(Tensor)**: 다차원 배열로서의 실용적 이해 (엄밀한 텐서 대수와 구분).
- **아인슈타인 표기법**과 텐서 연산(contraction, einsum).

---

## Animus 엔진을 위한 응용 트랙 (선택)

각 단계 학습 후 케이스 스터디:

| 학습 단계 | 응용 |
|---|---|
| 1~2단계 후 | 게임 캐릭터 스킨 행렬 변환, 카메라 행렬 |
| 3단계 후 | 임베딩 벡터 유사도(코사인 유사도)로 NPC 의도 매칭 |
| 4단계 후 | Graph Laplacian 으로 캐릭터 관계망 클러스터링 |
| 5단계 후 | LLM 임베딩 차원 축소·압축, 어텐션 가중치 행렬의 low-rank 해석 |

---

## 학습 계획

- **추천 진행 속도**: 1단계 1~2주, 2~3단계 각 2주, 4~5단계 각 3주 → 총 **12~14주**.
- **메인 교재**: Strang, *Introduction to Linear Algebra* + MIT 18.06 강의.
- **보조 시각화**: 3Blue1Brown 시리즈를 단계마다 해당 편 시청.

---

## 진행 체크리스트

- [ ] 0단계: 워밍업
- [ ] 1단계: 벡터 공간과 선형 변환
- [ ] 2단계: 선형 시스템과 부분공간
- [ ] 3단계: 직교성과 투영
- [ ] 4단계: 행렬식과 고윳값
- [ ] 5단계: SVD와 행렬 분해
- [ ] 부록 A: 행렬 미적분
- [ ] 부록 B: 다차원 데이터 구조

---

## 관련 노트

- [[Animus]]
- [[개인LLM]]
