# BlendME: A VR Blendshape Microexpression Dataset with Retrospective Self-Annotation

**CVPR 2026 Workshop on Subtle Visual Computing (SVC 2026)**

Swethasree Sribabu¹, Vishnu Raj², Gouthaman KV², Manivannan Muniyandi¹

¹Indian Institute of Technology Madras &nbsp;&nbsp; ²Dolby Laboratories

[[Paper]](PAPER_LINK_HERE) &nbsp; [[Video]](VIDEO_LINK_HERE) &nbsp; [[Dataset]](#dataset-access)

---

## Overview

BlendME is the first VR-native microexpression dataset captured using Meta Quest Pro face tracking. It records 70 blendshape activations (63 facial, 7 eye) at 45 Hz from 30 participants under a suppression paradigm, yielding 112 high-confidence microexpression clips from 21 participants across six basic emotions.

Key contributions:
- First microexpression dataset captured via HMD face tracking, natively in blendshape format
- Temporal Residual Microactivation (TRM) pipeline for ME candidate detection from blendshape time series
- Retrospective self-annotation interface with avatar replay, bypassing expert FACS coding
- Cross-dataset validation against CASME II, SAMM, and SMIC at the FACS AU level

---

## Video

A walkthrough of the data collection pipeline, annotation interface, and key results is available here:

**[Watch the BlendME overview video](VIDEO_LINK_HERE)**

---

## Repository Structure

```
BlendME/
├── annotation/          # Retrospective annotation interface (Unity)
├── detection/           # TRM detection pipeline
│   ├── trm.py           # Core TRM implementation
│   └── quality_filter.py
├── translation/         # FLAME-to-OVR and OVR-to-FLAME pipelines
├── analysis/            # Emotion separability, AU correlation scripts
├── calibration/         # 11-step calibration sequence scripts
└── README.md
```

> **Note:** Code will be uploaded upon paper publication. This repository is currently a placeholder.

---

## Dataset Access

The dataset (112 blendshape ME clips, annotation labels, stimulus metadata) will be released upon publication under a research-use license.

To request early access for review purposes, contact: `am24s015@smail.iitm.ac.in`

---

## TRM Pipeline Summary

The Temporal Residual Microactivation (TRM) pipeline detects ME candidates from blendshape time series in five stages:

1. **Baseline subtraction** - remove per-participant neutral resting state
2. **Temporal derivatives** - compute velocity, acceleration, and jerk
3. **Bandpass filtering** - isolate 2-25 Hz ME-frequency range from velocity signal
4. **Temporal energy** - RMS over 150 ms sliding window
5. **Adaptive thresholding** - peaks at 2 SD above per-channel mean energy, duration-gated to 40-500 ms

---

## Dataset Statistics

| Emotion   | N clips | %     |
|-----------|---------|-------|
| Sadness   | 42      | 37.5% |
| Happiness | 36      | 32.1% |
| Disgust   | 18      | 16.1% |
| Fear      | 7       | 6.3%  |
| Surprise  | 6       | 5.4%  |
| Anger     | 3       | 2.7%  |
| **Total** | **112** |       |

Mean clip duration: 136 ms (SD = 77 ms), consistent with the ME definition of ≤ 500 ms.

---

## Citation

If you use BlendME in your research, please cite:

```bibtex
@inproceedings{sribabu2026blendme,
  title     = {BlendME: A VR Blendshape Microexpression Dataset with Retrospective Self-Annotation},
  author    = {Sribabu, Swethasree and Raj, Vishnu and KV, Gouthaman and Muniyandi, Manivannan},
  booktitle = {CVPR Workshop on Subtle Visual Computing (SVC)},
  year      = {2026}
}
```

---

## License

The dataset and code are released for non-commercial research use only.
Details will be specified upon full release.

---

## Acknowledgments

This work was conducted at IIT Madras in collaboration with Dolby Laboratories.
