# 📄 Paper Reviews

논문 리뷰 슬라이드 모음 — Computer Vision / AI 분야 주요 논문을 읽고 발표한 자료입니다.

---

## Reviews

| # | Paper | Venue | Slides |
|---|-------|-------|--------|
| 1 | [InkLayer: Instance Segmentation of Scene Sketches Using Natural Image Priors](https://inklayer.github.io) | SIGGRAPH 2025 | [📄 슬라이드](./InkLayer/) |

---

## 01. InkLayer — Sketch Instance Segmentation

**논문:** Instance Segmentation of Scene Sketches Using Natural Image Priors  
**저자:** Mia Tang, Yael Vinker, Chuan Yan, Lvmin Zhang, Maneesh Agrawala (Stanford / MIT)  
**게재:** SIGGRAPH Conference Papers 2025

### 핵심 아이디어

- **문제:** 스케치는 픽셀이 희박하고 스타일 편차가 커서 기존 이미지 세그멘테이션 모델이 잘 작동하지 않음
- **방법:** Grounding DINO를 스케치 도메인에 파인튜닝 → Average Precision **26% → 74%** 향상
- **정제:** SAM으로 마스크 생성 후 depth cue 기반 refinement로 겹치는 영역 처리
- **출력:** 세그멘테이션 결과를 sorted layer로 분해 → 오브젝트 이동/삭제 등 스케치 편집 자동화

### 연결되는 개념

- Open-vocabulary segmentation (Grounded SAM = Grounding DINO + SAM)
- Real-image → Sketch domain adaptation
- Synthetic dataset 구축 (InkScenes, 20,542장)
- Inpainting으로 가려진 영역 복원

### 의의 & 한계

- 기존 방법 대비 다양한 스케치 스타일에서 강건한 성능
- 클래스 종속 학습 없이 open-vocabulary 탐지 가능
- 복잡한 장면에서 depth 추정이 부정확할 경우 레이어 순서 오류 가능성

---

*세미나 발표 자료 (학부연구생 논문 리뷰 세미나)*
