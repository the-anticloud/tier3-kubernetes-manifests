# Deploy Guide — kubernetes-manifests
**Platform:** Anticloud sovereign infrastructure | Air-gap capable
**Stack:** Kubernetes 1.29+, kubectl, Helm 3.14+, AIOSS_FORMAT

## Prerequisites
Python 3.11+. See stack: Kubernetes 1.29+, kubectl, Helm 3.14+, AIOSS_FORMAT. AIOSS_FORMAT required. PAX 27B weights for AI-assisted features.

## AIOSS Integration
```bash
aioss init --module kubernetes-manifests --output ./kubernetes_manifests.aioss
aioss append --chain ./kubernetes_manifests.aioss --payload ./output.bin --module kubernetes-manifests
aioss verify --chain ./kubernetes_manifests.aioss
```

## Air-Gap Deployment
```bash
# On networked machine:
pip download -r requirements.txt -d ./wheels/
# Transfer wheels/ to air-gap host, then:
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="kubernetes-manifests",
    aioss_chain="./kubernetes_manifests.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./kubernetes_manifests.aioss --verbose
python -m kubernetes_manifests.tests.smoke
```
