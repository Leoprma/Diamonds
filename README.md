# Diamonds

![Diamonds](https://github.com/Leoprma/Diamonds/blob/main/diamonds.jpg)

This project aim is to predict the price of 5000 diamonds based in their caracteristics (carat, color, clarity, cut, depth, etc.) contained in the dataset using a simple model of linear regression.
To develop the model, it is used a dataset with caracteristics and price of 48940 diamonds.

# Tools
- Python
- Jupyter Notebook
- Pandas

# Data Source 
- [Dataset - Diamonds to predict price](https://github.com/Leoprma/Diamonds/blob/main/rick_diamonds.csv)
- [Dataset - Diamonds historical data](https://github.com/Leoprma/Diamonds/blob/main/diamonds.csv)

# Dataset columns

| Column  | Description  |
|---|---|
| Price  | Price in US dollars (326-18,823)  |
| Carat  | Weight of the diamond (0.2--5.01)  |
| Cut  | Quality of the cut (Fair, Good, Very Good, Premium, Ideal)  |
| Color  | Diamond colour, from J (worst) to D (best)  |
| Clarity  | A measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (best))   |
| x  | Length in mm (0--10.74)  |
| y  | Width in mm (0--58.9)  |
| z  | Depth in mm (0--31.8)  |
| Depth  | Total depth percentage = z / mean(x, y) = 2 * z / (x + y) (43--79)  |
| Table  | Width of top of diamond relative to widest point (43--95)  |

# Data Cleaning
## Change in categorical columns

Since the Color and Clarity classification is familiar just to diamond experts, it was opted for changing the scale for a more understandable one (starting in 0 for the worst and increasing until the best)

## Checking the diamonds without data in any dimension (x, y or z)

The next step was to check if there was some diamond which had x, y or z=0.
For all of them which had one dimension equal to zero and information about Depth, that dimension was calculated.

## Looking for outliers

The last step was to look for outliers. 
It was discovered that many of them were caused by an typing errors on one dimension. So, once again, that dimension was calculated using the depth.

# Exploratory Data Analysis (EDA)

After cleaning the data, the EDA was made to give hints about the best variable(s) to been used in the regression.
As a result of this analysis, it has been discovered that the variable with the strongest correlation with the price, and consequently, the best candidate for a first regression is the carat.
It was also observed a relevant relationship between color and clarity with price.

# Results

| Attempt  | Description  | RMSE  |
|---|---|---|
| 1  | Used the mean of the historical dataset as prediction method to create a baseline |  3980.713883 |
| 2  | Regression using carat as predictor variable |  1605.151757 |
| 3  | Creating ranges of carat and doing different regressions for each carat range |  1467.873633 |
| 4  | Using regressions with carat, clarity and color as predictors for each carat range |  872.770784 |
| 5  | Fixing the errors caused by extrapolation |  871.795200 |

