## Exploration of Seaborn Package

### Table of Contents

* [Importing Libraries](#Importing-Libraries)
* [Loading Datasets](#Loading-Datasets)
* [Barplot](#Barplot)
* [Histogram Plot](#Histogram-Plot)
* [Kernel density estimation](#Kernel-density-estimation)
* [Multiple Histogram Plots](#Multiple-Histogram-Plots)
* [Subplots](#Subplots)
* [Relplot](#Relplot)
* [Jointplot](#Jointplot)
* [Pairplot](#Pairplot)
* [Boxplot and Catplot](#Boxplot-and-Catplot)
* [Aggregation and representing uncertainty](#Aggregation-and-representing-uncertainty)
* [HeatMaps](#HeatMaps)
* [Facetgrid](#Facetgrid)



```python
## Install Seaborn
#!pip install seaborn
```

### Importing Libraries


```python
import seaborn as sns
import matplotlib.pyplot as plt
```

### Loading Datasets


```python
penguins = sns.load_dataset("penguins")
tips = sns.load_dataset("tips")
flights = sns.load_dataset("flights")
fmri = sns.load_dataset("fmri")
titanic = sns.load_dataset("titanic")
iris = sns.load_dataset("iris")


print(sns.get_dataset_names())
```

    ['anagrams', 'anscombe', 'attention', 'brain_networks', 'car_crashes', 'diamonds', 'dots', 'exercise', 'flights', 'fmri', 'gammas', 'geyser', 'iris', 'mpg', 'penguins', 'planets', 'taxis', 'tips', 'titanic']
    

### Barplot


```python
sns.catplot(x="sex", y="survived", hue="class", kind="bar", data=titanic);
```


    
![png](output_8_0.png)
    



```python
sns.catplot(y="deck", hue="class", kind="count",
            palette="pastel", edgecolor=".6",
            data=titanic);
```


    
![png](output_9_0.png)
    



```python
sns.catplot(data=iris, orient="h", kind="box");
```


    
![png](output_10_0.png)
    



```python
sns.countplot(y="deck", data=titanic, color="c");
```


    
![png](output_11_0.png)
    



```python
sns.violinplot(x=iris.species, y=iris.sepal_length);
```


    
![png](output_12_0.png)
    


### Histogram Plot
[*Back to Table of Contents*](#Table-of-Contents)


```python
display(penguins.head())
sns.histplot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
sns.displot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
plt.show()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.1</td>
      <td>18.7</td>
      <td>181.0</td>
      <td>3750.0</td>
      <td>Male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186.0</td>
      <td>3800.0</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195.0</td>
      <td>3250.0</td>
      <td>Female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>Female</td>
    </tr>
  </tbody>
</table>
</div>



    
![png](output_14_1.png)
    



    
![png](output_14_2.png)
    



```python
sns.displot(penguins, x="flipper_length_mm", hue="species", element="step");
```


    
![png](output_15_0.png)
    



```python
sns.displot(penguins, x="flipper_length_mm", hue="sex", multiple="dodge");
```


    
![png](output_16_0.png)
    



```python
sns.displot(penguins, x="flipper_length_mm", col="sex");
```


    
![png](output_17_0.png)
    



```python
### Normalized Histogram

sns.displot(penguins, x="flipper_length_mm", hue="species", stat="density", common_norm=False)
```




    <seaborn.axisgrid.FacetGrid at 0x1e2bd0005b0>




    
![png](output_18_1.png)
    


### Kernel density estimation
[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.kdeplot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
sns.displot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack", kind="kde")
plt.show()

```


    
![png](output_20_0.png)
    



    
![png](output_20_1.png)
    


### Multiple Histogram Plots
[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.displot(data=penguins, x="flipper_length_mm", hue="species", col="species")
plt.show()
```


    
![png](output_22_0.png)
    


### Subplots
[*Back to Table of Contents*](#Table-of-Contents)


```python
f, axs = plt.subplots(1, 2, figsize=(8, 4), gridspec_kw=dict(width_ratios=[4, 3]))
sns.scatterplot(data=penguins, x="flipper_length_mm", y="bill_length_mm", hue="species", ax=axs[0])
sns.histplot(data=penguins, x="species", hue="species", shrink=.8, alpha=.8, legend=False, ax=axs[1])
f.tight_layout()

plt.show()
```


    
![png](output_24_0.png)
    


### Relplot
[*Back to Table of Contents*](#Table-of-Contents)


```python
g = sns.relplot(data=tips, x="total_bill", y="tip")
g.ax.axline(xy1=(10, 2), slope=.2, color="b", dashes=(5, 2))
plt.show()
```


    
![png](output_26_0.png)
    



```python
g = sns.relplot(data=penguins, x="flipper_length_mm", y="bill_length_mm", col="sex")
g.set_axis_labels("Flipper length (mm)", "Bill length (mm)")
plt.show()
```


    
![png](output_27_0.png)
    



```python
sns.relplot(data=flights, x="year", y="passengers", hue="month", kind="line")
plt.show()
```


    
![png](output_28_0.png)
    


#### Using wide dataset Format


```python
flights_wide = flights.pivot(index="year", columns="month", values="passengers")
display(flights_wide.head())
sns.relplot(data=flights_wide, kind="line")
plt.show()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>month</th>
      <th>Jan</th>
      <th>Feb</th>
      <th>Mar</th>
      <th>Apr</th>
      <th>May</th>
      <th>Jun</th>
      <th>Jul</th>
      <th>Aug</th>
      <th>Sep</th>
      <th>Oct</th>
      <th>Nov</th>
      <th>Dec</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1949</th>
      <td>112</td>
      <td>118</td>
      <td>132</td>
      <td>129</td>
      <td>121</td>
      <td>135</td>
      <td>148</td>
      <td>148</td>
      <td>136</td>
      <td>119</td>
      <td>104</td>
      <td>118</td>
    </tr>
    <tr>
      <th>1950</th>
      <td>115</td>
      <td>126</td>
      <td>141</td>
      <td>135</td>
      <td>125</td>
      <td>149</td>
      <td>170</td>
      <td>170</td>
      <td>158</td>
      <td>133</td>
      <td>114</td>
      <td>140</td>
    </tr>
    <tr>
      <th>1951</th>
      <td>145</td>
      <td>150</td>
      <td>178</td>
      <td>163</td>
      <td>172</td>
      <td>178</td>
      <td>199</td>
      <td>199</td>
      <td>184</td>
      <td>162</td>
      <td>146</td>
      <td>166</td>
    </tr>
    <tr>
      <th>1952</th>
      <td>171</td>
      <td>180</td>
      <td>193</td>
      <td>181</td>
      <td>183</td>
      <td>218</td>
      <td>230</td>
      <td>242</td>
      <td>209</td>
      <td>191</td>
      <td>172</td>
      <td>194</td>
    </tr>
    <tr>
      <th>1953</th>
      <td>196</td>
      <td>196</td>
      <td>236</td>
      <td>235</td>
      <td>229</td>
      <td>243</td>
      <td>264</td>
      <td>272</td>
      <td>237</td>
      <td>211</td>
      <td>180</td>
      <td>201</td>
    </tr>
  </tbody>
</table>
</div>



    
![png](output_30_1.png)
    


#### Scatterplot with hue and style


```python
sns.relplot(x="total_bill", y="tip", hue="smoker", style="time", data=tips)
plt.show()
```


    
![png](output_32_0.png)
    


#### Scatterplot with size


```python
sns.relplot(x="total_bill", y="tip", size="size", sizes=(15, 200), data=tips);
plt.show()
```


    
![png](output_34_0.png)
    


### Boxplot and Catplot
[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.catplot(data=flights_wide, kind="box")
plt.show()
```


    
![png](output_36_0.png)
    



```python
sns.catplot(x="day", y="total_bill", kind="box", data=tips);
```


    
![png](output_37_0.png)
    



```python
sns.catplot(x="day", y="total_bill", hue="smoker", kind="box", data=tips);
```


    
![png](output_38_0.png)
    



```python
sns.catplot(x="day", y="total_bill", data=tips);
```


    
![png](output_39_0.png)
    



```python
sns.catplot(x="day", y="total_bill", hue="sex", kind="swarm", data=tips);
```


    
![png](output_40_0.png)
    


### Jointplot

jointplot() plots the relationship or joint distribution of two variables while adding marginal axes that show the 
univariate distribution of each one separately:


[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.jointplot(data=penguins, x="flipper_length_mm", y="bill_length_mm", hue="species")
plt.show()
```


    
![png](output_42_0.png)
    


### Pairplot
[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.pairplot(data=penguins, hue="species")
plt.show()
```


    
![png](output_44_0.png)
    


### Aggregation and representing uncertainty
[*Back to Table of Contents*](#Table-of-Contents)


```python
display(fmri.head())
sns.relplot(x="timepoint", y="signal", kind="line", data=fmri)
plt.show()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject</th>
      <th>timepoint</th>
      <th>event</th>
      <th>region</th>
      <th>signal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>s13</td>
      <td>18</td>
      <td>stim</td>
      <td>parietal</td>
      <td>-0.017552</td>
    </tr>
    <tr>
      <th>1</th>
      <td>s5</td>
      <td>14</td>
      <td>stim</td>
      <td>parietal</td>
      <td>-0.080883</td>
    </tr>
    <tr>
      <th>2</th>
      <td>s12</td>
      <td>18</td>
      <td>stim</td>
      <td>parietal</td>
      <td>-0.081033</td>
    </tr>
    <tr>
      <th>3</th>
      <td>s11</td>
      <td>18</td>
      <td>stim</td>
      <td>parietal</td>
      <td>-0.046134</td>
    </tr>
    <tr>
      <th>4</th>
      <td>s10</td>
      <td>18</td>
      <td>stim</td>
      <td>parietal</td>
      <td>-0.037970</td>
    </tr>
  </tbody>
</table>
</div>



    
![png](output_46_1.png)
    


### HeatMaps
[*Back to Table of Contents*](#Table-of-Contents)


```python
flights2 = flights.pivot("month", "year", "passengers")
sns.heatmap(flights2, annot=True, fmt="d", cmap="YlGnBu")
plt.show()
display(flights2.head())
```


    
![png](output_48_0.png)
    



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>year</th>
      <th>1949</th>
      <th>1950</th>
      <th>1951</th>
      <th>1952</th>
      <th>1953</th>
      <th>1954</th>
      <th>1955</th>
      <th>1956</th>
      <th>1957</th>
      <th>1958</th>
      <th>1959</th>
      <th>1960</th>
    </tr>
    <tr>
      <th>month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan</th>
      <td>112</td>
      <td>115</td>
      <td>145</td>
      <td>171</td>
      <td>196</td>
      <td>204</td>
      <td>242</td>
      <td>284</td>
      <td>315</td>
      <td>340</td>
      <td>360</td>
      <td>417</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>118</td>
      <td>126</td>
      <td>150</td>
      <td>180</td>
      <td>196</td>
      <td>188</td>
      <td>233</td>
      <td>277</td>
      <td>301</td>
      <td>318</td>
      <td>342</td>
      <td>391</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>132</td>
      <td>141</td>
      <td>178</td>
      <td>193</td>
      <td>236</td>
      <td>235</td>
      <td>267</td>
      <td>317</td>
      <td>356</td>
      <td>362</td>
      <td>406</td>
      <td>419</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>129</td>
      <td>135</td>
      <td>163</td>
      <td>181</td>
      <td>235</td>
      <td>227</td>
      <td>269</td>
      <td>313</td>
      <td>348</td>
      <td>348</td>
      <td>396</td>
      <td>461</td>
    </tr>
    <tr>
      <th>May</th>
      <td>121</td>
      <td>125</td>
      <td>172</td>
      <td>183</td>
      <td>229</td>
      <td>234</td>
      <td>270</td>
      <td>318</td>
      <td>355</td>
      <td>363</td>
      <td>420</td>
      <td>472</td>
    </tr>
  </tbody>
</table>
</div>


### Facetgrid
[*Back to Table of Contents*](#Table-of-Contents)


```python
sns.FacetGrid(penguins, col="island", row="sex").map(sns.histplot, "flipper_length_mm")
```




    <seaborn.axisgrid.FacetGrid at 0x1e2bccfd9d0>




    
![png](output_50_1.png)
    



```python
sns.FacetGrid(penguins, col="island", row="sex").map(sns.distplot, "flipper_length_mm");
plt.show()
```

    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\ehbartolo\Anaconda3\lib\site-packages\seaborn\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    


    
![png](output_51_1.png)
    



```python

```
