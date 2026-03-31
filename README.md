# v9.4 Lean vs Circom/Groth16

Artifact-backed comparison drawn from:

- [artifacts/leanvm-v9_4-benchmarks-full/README.md](/home/ubuntu/tiny-privacy-vm-ere/artifacts/leanvm-v9_4-benchmarks-full/README.md)
- [artifacts/circom-v9_4-full-benchmarks/README.md](/home/ubuntu/tiny-privacy-vm-ere/artifacts/circom-v9_4-full-benchmarks/README.md)

## Representative Rows

| Flow | Case | Lean v9.4 Proof Time | Lean v9.4 Verify Time | Lean v9.4 Proof Size | Circom/Groth16 Proof Time | Circom/Groth16 Verify Time | Circom/Groth16 Proof Size |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Action leaf | `TX2` | `188.369 ms` | `22.179 ms` | `222,700 B` | `16,080.783 ms` | `874.174 ms` | `805 B` |
| Voucher leaf | `TX2` | `147.558 ms` | `21.707 ms` | `194,424 B` | `3,140.793 ms` | `915.352 ms` | `806 B` |
| Pair entry | `TX2` | `6,179.374 ms` | `43.303 ms` | `300,196 B` | `15,424.273 ms` | `844.930 ms` | `806 B` |
| Action leaf | `RTX2` | `232.312 ms` | `26.651 ms` | `204,788 B` | `17,132.733 ms` | `934.994 ms` | `805 B` |
| Voucher leaf | `RTX2` | `195.139 ms` | `22.816 ms` | `194,052 B` | `3,045.704 ms` | `950.586 ms` | `805 B` |
| Pair entry | `RTX2` | `14,231.920 ms` | `49.866 ms` | `299,608 B` | `16,482.900 ms` | `826.997 ms` | `807 B` |

## Headline Ranges

| Component | Lean v9.4 Proof Time | Lean v9.4 Verify Time | Lean v9.4 Proof Size | Circom/Groth16 Proof Time | Circom/Groth16 Verify Time | Circom/Groth16 Proof Size |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Action leaves | `144.507-391.478 ms` | `19.836-26.651 ms` | `197,368-227,172 B` | `15,617.854-17,767.252 ms` | `827.308-1,062.786 ms` | `803-806 B` |
| Voucher leaves | `147.558-212.542 ms` | `18.864-26.349 ms` | `190,676-196,092 B` | `2,977.517-3,352.675 ms` | `805.221-950.586 ms` | `803-806 B` |
| Pair entry | `6,008.255-15,244.695 ms` | `35.490-205.641 ms` | `299,608-301,368 B` | `15,424.273-17,233.704 ms` | `766.478-1,022.575 ms` | `803-807 B` |

## Slide Takeaway

- **Lean v9.4**: much faster proving, much larger proofs.
- **Circom/Groth16**: much slower proving, tiny proofs.

## Caveat

The Circom `pair_entry` benchmarks are native Circom flow circuits, not recursive proof verification inside Circom, so they are comparable at the surface level but not identical internally.
