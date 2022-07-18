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
  <summary>Version of Packages Used</summary>

|       | Python  | Seaborn | Pandas | SkLearn | Scipy |
| :---: | :---: | :---: | :---: | :---:  | :---:  |
| Version  | 1 | 2 | 3 | 4 | 5     | 

</details>

