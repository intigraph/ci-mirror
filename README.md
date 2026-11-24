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

Additional recovered catalogue-pinned archives:

| File | SHA256 | Upstream |
|---|---|---|
| onnxruntime-win-x64-1.23.2.zip | 0b38df9af21834e41e73d602d90db5cb06dbd1ca618948b8f1d66d607ac9f3cd | microsoft/onnxruntime v1.23.2 |
| onnxruntime-osx-arm64-1.23.2.tgz | b4d513ab2b26f088c66891dbbc1408166708773d7cc4163de7bdca0e9bbb7856 | microsoft/onnxruntime v1.23.2 |
| onnxruntime-osx-x86_64-1.23.2.tgz | d10359e16347b57d9959f7e80a225a5b4a66ed7d7e007274a15cae86836485a6 | microsoft/onnxruntime v1.23.2 |
| onnxruntime-linux-aarch64-1.23.2.tgz | 7c63c73560ed76b1fac6cff8204ffe34fe180e70d6582b5332ec094810241e5c | microsoft/onnxruntime v1.23.2 |

The added archives were recovered from [PhotoPrism's archive](https://dl.photoprism.app/onnx/runtime/v1.23.2/) and verified byte-for-byte against the existing Quipu archive pins. Their selected native libraries also matched the existing core-library SHA256 and size. The catalogue pins, archive contents and Microsoft MIT attribution are unchanged.
