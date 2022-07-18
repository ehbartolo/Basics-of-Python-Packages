# Basics of Python Packages

Prepared by: Eldion Vincent H. Bartolo

## :books: Table of Contents

* [Seaborn](#Seaborn)
* [Pandas](#Pandas)
* [SkLearn](#SkLearn)
* [Optimization Packages](#Optimization-Packages)

## Seaborn

```python
# Install Seaborn
!pip install seaborn
```

Go to [Seaborn_Notebook](https://github.com/ehbartolo/Basics-of-Python-Packages/blob/main/Seaborn%20Tutorials.ipynb)

Sample output
```python
import seaborn as sns
import matplotlib.pyplot as plt
penguins = sns.load_dataset("penguins")

sns.jointplot(data=penguins, x="flipper_length_mm", y="bill_length_mm", hue="species")
plt.show()
```
![png](images/Seaborn_Sample.PNG)

## Pandas

## SkLearn

## Optimization Packages
Explores Optimization using **Scipy, PulP, OR Tools, Pyomo**
Go to [Optimization Pakages](https://github.com/ehbartolo/Basics-of-Python-Packages/blob/main/Optimization_Packages.ipynb)


<details>
  <summary>Version of Packages Used</summary>

|       | Python  | Seaborn | Pandas | SkLearn | Scipy |
| :---: | :---: | :---: | :---: | :---:  | :---:  |
| Version  | 1 | 2 | 3 | 4 | 5     | 

</details>



## To Do
## :computer: Section 1

## :books: Section 2

## :key: Section 3

## :mag_right: Section 3



