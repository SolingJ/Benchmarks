
## 今回使用するモデル

今回は以下の4つのモデルを使用します．

| モデル | 量子化 | 実行時 n_ctx_slot | K/Vキャッシュ量子化 | GPUオフロード結果（MoE） | リンク |
|---|---|---:|---|---|---|
| Qwen3.5 9B | Q4 | 131072 | `q8_0`（K/Vとも） | — | https://huggingface.co/lmstudio-community/Qwen3.5-9B-GGUF |
| Gemma4 12B | Q4 | 65536 | `q4_0`（K/Vとも） | — | https://huggingface.co/google/gemma-4-12B|
| Qwen3.6 35B A3B | Q4 | 131072 | `q8_0`（K/Vとも） | `n_gpu_layers=999999`（最大指定）。一部テンソルはCPUへオーバーライド | [ https://huggingface.co/bartowski/deepreinforce-ai_Ornith-1.0-35B-GGUF](https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF)|
| Qwen3.8 27B | IQ2_S | 65536 | `q4_0`（K/Vとも） | — | [https://huggingface.co/bartowski/deepreinforce-ai_Ornith-1.0-35B-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF)|

GPUはNVIDIA GeForce RTX 3060（VRAM: 12GB）を用い，システムメモリは16GBのPCを用いました．

※ `n_ctx_slot`、K/Vキャッシュ量子化、GPUオフロード結果は、`solver.ps1`実行時に使用されたLM Studioのモデル別ロード設定に基づく．Qwen3.8は結果ファイルを生成した最終ロード時の値を記載している．
