# InkLayer: Instance Segmentation of Scene Sketches Using Natural Image Priors

> **SIGGRAPH Conference Papers 2025**  
> Mia Tang, Yael Vinker, Chuan Yan, Lvmin Zhang, Maneesh Agrawala (Stanford / MIT CSAIL)

🔗 [논문 홈페이지](https://inklayer.github.io) · [arXiv](https://doi.org/10.1145/3721238.3730606)

---

## 한 줄 요약

스케치 이미지에서 오브젝트별 인스턴스 세그멘테이션을 수행하고, 결과를 레이어로 분해해 스케치 편집을 자동화하는 방법론.

---

## 핵심 아이디어

- **문제:** 스케치는 픽셀이 희박하고 스타일 편차가 커서 기존 이미지 세그멘테이션 모델이 잘 작동하지 않음
- **탐지:** Grounding DINO를 소규모 스케치 데이터셋(SketchyScene)으로 파인튜닝 → AP **26% → 74%**
- **세그멘테이션:** SAM을 스케치 도메인에 그대로 적용 (제로샷으로도 어느 정도 작동함)
- **정제:** Depth estimator로 depth map 추출 → 겹치는 오브젝트 간 경계 ambiguity 해소
- **출력:** 세그멘테이션 마스크를 sorted layer로 분해 + inpainting으로 가려진 영역 복원

---

## 방법론 파이프라인

```
입력 스케치
    ↓
Grounding DINO (파인튜닝) → bounding box 탐지
    ↓
SAM → 인스턴스 마스크 생성
    ↓
Depth Extractor → depth cue 기반 마스크 정제
    ↓
sorted layer 분해 + inpainting
    ↓
편집 가능한 레이어드 스케치
```

---

## InkScenes 데이터셋

- 총 20,542장의 주석 달린 장면 스케치
- SketchyScene 기반 + Visual Genome 기반 2가지 파이프라인
- 72개 카테고리, Calligraphic / Charcoal / Brush Pen 등 다양한 획 스타일 포함

---

## 의의 & 한계

**의의**
- 클래스 종속 없이 open-vocabulary 탐지 가능
- 기존 방법 대비 다양한 스케치 스타일에서 강건한 성능
- 스케치 편집 자동화(이동, 삭제, 재배치)로 실용적 응용 가능

**한계**
- 복잡한 장면에서 depth 추정이 부정확하면 레이어 순서 오류 발생 가능
- 파인튜닝에 일부 레이블 데이터 필요 (완전 제로샷 아님)

---

*세미나 발표 자료 (학부연구생 논문 리뷰 세미나)*  
[← 목록으로 돌아가기](../)
