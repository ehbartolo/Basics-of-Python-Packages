# Basics of Python Packages

Prepared by: Eldion Vincent H. Bartolo

## :books: Table of Contents

* [Seaborn](#Seaborn)
* [SkLearn](#SkLearn)

### Seaborn
```python
# Install Seaborn
!pip install seaborn
```
![png](output_8_0.png)


# :computer: Installation
* Clone this repo by `git clone https://github.com/kwea123/ngp_pl`
* Python>=3.8 (installation via [anaconda](https://www.anaconda.com/distribution/) is recommended, use `conda create -n ngp_pl python=3.8` to create a conda environment and activate it by `conda activate ngp_pl`)

# :books: Data preparation

Download preprocessed datasets from [NSVF](https://github.com/facebookresearch/NSVF#dataset).

# :key: Training

Quickstart: `python train.py --root_dir <path/to/lego> --exp_name Lego`


# :mag_right: Testing

| Method    | avg PSNR | FPS   | GPU     |
| :---:     | :---:    | :---: | :---:   |
| torch-ngp | 31.46    | 18.2  | 2080 Ti |
| mine      | 32.96    | 36.2  | 2080 Ti |
| instant-ngp paper | **33.18** | **60** | 3090 |


<p align="center">
  <img src="https://user-images.githubusercontent.com/11364490/176800109-38eb35f3-e145-4a09-8304-1795e3a4e8cd.png", width="45%">
  <img src="https://user-images.githubusercontent.com/11364490/176800106-fead794f-7e70-4459-b99e-82725fe6777e.png", width="45%">
  <br>
  <sup>Left: torch-ngp. Right: mine.</sup>
</p>


<details>
  <summary>Synthetic-NeRF</summary>

|       | Mic   | Ficus | Chair | Hotdog | Materials | Drums | Ship  | Lego  | AVG   |
| :---: | :---: | :---: | :---: | :---:  | :---:     | :---: | :---: | :---: | :---: |
| PSNR  | 35.59 | 34.13 | 35.28 | 37.35  | 29.46     | 25.81 | 30.32 | 35.76 | 32.96 |
| SSIM  | 0.988 | 0.982 | 0.984 | 0.980  | 0.944     | 0.933 | 0.890 | 0.979 | 0.960 |
| LPIPS | 0.017 | 0.024 | 0.025 | 0.038  | 0.070     | 0.076 | 0.133 | 0.022 | 0.051 |
| FPS   | 40.81 | 34.02 | 49.80 | 25.06  | 20.08     | 37.77 | 15.77 | 36.20 | 32.44 |
| Training time | 3m9s | 3m12s | 4m17s | 5m53s | 4m55s | 4m7s | 9m20s | 5m5s | 5m00s |

</details>

