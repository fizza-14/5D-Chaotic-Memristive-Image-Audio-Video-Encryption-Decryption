## 5D Chaotic Memristive Model: Image, Audio and Video Encryption and Decryption

Image, audio and video encryption and decryption using the 5D tangent-hyperbolic memristive chaotic system (RK4, α = 1), 16-bit/8-bit chaotic keystreams and bitwise XOR, with 12 statistical tests.

**Platform:** Python · Google Colab

## How to Run

1. Open the `.ipynb` notebook you want in Google Colab (image, audio, video, or the 12-tests notebook).
2. Select **Runtime → Run all** and upload the matching test file when prompted (image, WAV audio, or video).
3. View the original, encrypted and decrypted results, the exact-recovery check and the statistical measurements.

For video, set `MAX_SECONDS` and `SCALE_WIDTH` to small values (for example 2 and 160) for a quick run. Decrypt from `encrypted_video.mkv`, not from the preview MP4.

## Repository contents

| File | Purpose |
|---|---|
| `5D_Chaotic_Model_Image_Encryption_Decryption.ipynb` | Image encryption and decryption |
| `5D_Chaotic_Model_Audio_Encryption_Decryption.ipynb` | Audio (16-bit PCM WAV) encryption and decryption |
| `5D_Chaotic_Model_Video_Encryption_Decryption.ipynb` | Video frames + audio encryption and decryption |
| `5D_Chaotic_Model_12_Tests.ipynb` | 12 statistical and performance tests for image, audio and video |
| `reports/` | Project report for image, audio and video (PDF) |
| `test data/` | Sample image, audio and video used in the reports |

## Model

```
dx1/dt = a(x2 - x1) + 0.25*x3 + g*(delta + gamma*tanh(x5))*x3
dx2/dt = b*x1 - x1*x3 + c*x2 - x4
dx3/dt = d*x1*x2 - e*x3
dx4/dt = x1
dx5/dt = x3
```

Parameters: a = 78, b = -16, c = 58, d = 35, e = 15, g = 1, δ = 1, γ = 0.5. Initial state: [0, 0, 8, 6, 0]. Step h = 0.001.

## Note

- Based on Qureshi et al., *Cap like trajectories in 5D chaotic tangent hyperbolic memristive model*, Physica Scripta 99 (2024) 075238, https://doi.org/10.1088/1402-4896/ad5476
- The paper demonstrates image encryption only. Audio and video here are project extensions.
- The solver is RK4 (α = 1). The paper's ABC fractional-order scheme (α = 0.99) is not implemented.
- The cipher is XOR only, with no diffusion, so NPCR/UACI are low by design. High entropy and low correlation do not prove cryptographic security. This is an experimental prototype, not for confidential data.
- Reported video results cover only a short, reduced-size preview of the test video.
