# Developer Cookbook — kubernetes-manifests
**Stack:** Kubernetes 1.29+, kubectl, Helm 3.14+, AIOSS_FORMAT
**Domain:** Sovereign Kubernetes deployment: air-gapped K8s manifests for Anticloud
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```bash
# Apply Anticloud manifests
kubectl apply -f ./manifests/

# Verify AIOSS chain PVC
kubectl exec -n anticloud deploy/pax-inference -- aioss verify /mnt/aioss/inference.aioss

# PAX manifest validation
anticloud tool pax --prompt 'Check these K8s manifests for sovereign compliance' \
  --dir ./manifests/ --max-tokens 1024

# Scale PAX inference
kubectl scale deployment pax-inference -n anticloud --replicas=2
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every kubernetes-manifests output:
chain_hash = aioss_append("./kubernetes_manifests.aioss",
                           result_bytes, "kubernetes-manifests")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all kubernetes-manifests operations are logged to api-oss-logging and audited by api-oss-compliance.
