# ci-mirror

Checksum-addressed mirror of third-party build inputs for intigraph CI.

The upstream release location for ONNX Runtime (github.com/microsoft/onnxruntime) stopped resolving in November 2026. quipu CI downloads a SHA256-pinned ONNX Runtime archive; this repository republishes byte-identical copies so pinned builds keep working.

Layout: each asset is attached to a release whose tag is `sha256/<sha256 of the file>`, so the download URL is

    https://github.com/intigraph/ci-mirror/releases/download/sha256/<sha256>/<filename>

That matches the `CI_ARTIFACT_MIRROR_URL` contract in quipu's `scripts/fetch-pinned-ci-asset.py` (`<mirror>/sha256/<pin>/<name>`). CI verifies the SHA256 of every download against its own pin, so a wrong file here cannot be used.

| File | SHA256 | Upstream |
|---|---|---|
| onnxruntime-linux-x64-1.23.2.tgz | 1fa4dcaef22f6f7d5cd81b28c2800414350c10116f5fdd46a2160082551c5f9b | microsoft/onnxruntime v1.23.2 |

ONNX Runtime is Copyright (c) Microsoft Corporation and is distributed under the MIT License; see LICENSE-onnxruntime. Each archive also carries its own LICENSE and ThirdPartyNotices.txt.
