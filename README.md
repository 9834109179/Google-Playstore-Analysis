# Google-Playstore-Analysis

This project involves a comprehensive analysis of the Google Playstore dataset. The primary goal is to clean and preprocess the data, followed by conducting exploratory data analysis (EDA) to uncover interesting insights and patterns.

---

<p>

## Dataset Overview

The dataset used in this analysis is the Google Playstore dataset, which contains information about various apps available on the platform. The key columns in the dataset include:

- **App**: Name of the app
- **Category**: Category under which the app is listed
- **Rating**: User rating of the app
- **Reviews**: Number of user reviews
- **Size**: Size of the app
- **Installs**: Number of installs
- **Type**: Type of the app (Free/Paid)
- **Price**: Price of the app
- **Content Rating**: Content rating of the app
- **Genres**: Genres of the app
- **Last Updated**: Last updated date of the app
- **Current Ver**: Current version of the app
- **Android Ver**: Minimum Android version required

## Data Cleaning and Preprocessing

Several steps were taken to clean and preprocess the data:

1. **Removing Duplicates**: Duplicate records were identified and removed to ensure data integrity.
   ```python
   df.drop_duplicates(inplace=True)
   ```

2. **Handling Missing Values**: Missing values were handled by either filling them with appropriate statistics (like mode) or by converting them to a suitable format.
   ```python
   df['Rating'].fillna(df['Rating'].mode()[0], inplace=True)
   df['Type'].fillna(df['Type'].mode()[0], inplace=True)
   df['Current Ver'].fillna(df['Current Ver'].mode()[0], inplace=True)
   ```

3. **Data Type Conversion**: Columns like `Reviews`, `Installs`, `Price`, `Current Ver`, and `Android Ver` were converted to numeric types after appropriate transformations.
   ```python
   df.Reviews = pd.to_numeric(df.Reviews, errors="coerce")
   df.Installs = df.Installs.apply(lambda x: str(x).replace(',', '').replace('+', '')).astype(int)
   df.Price = df.Price.str.replace("$", "").astype(float)
   df['Current Ver'] = pd.to_numeric(df['Current Ver'], errors='coerce')
   df['Android Ver'] = pd.to_numeric(df['Android Ver'], errors='coerce')
   ```

## Exploratory Data Analysis (EDA)

The cleaned data was then subjected to exploratory data analysis to derive meaningful insights. Some key analyses included:

1. **Distribution of App Ratings**:
   ```python
   plt.figure(figsize=(10,10))
   sns.countplot(x=df.Rating)
   plt.title("Distribution of App Ratings")
   plt.show()
   ```

2. **Category-wise Rating Distribution**:
   ```python
   plt.figure(figsize=(10,10))
   sns.barplot(x=df.Rating, y=df.Category)
   plt.title("Category-wise Rating Distribution")
   plt.show()
   ```

## Insights

From the analysis, several interesting insights were obtained:

- The majority of apps have high user ratings, indicating overall user satisfaction.
- Certain categories tend to have higher ratings on average compared to others.
- The distribution of installs and reviews varies significantly across different app categories.

## Conclusion

This project demonstrates the process of data cleaning, preprocessing, and exploratory data analysis using the Google Playstore dataset. The insights derived can help developers and stakeholders make informed decisions about app development and marketing strategies.

Feel free to explore the code and contribute to further enhance this analysis.

## Requirements

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn

## Usage

To run this analysis, clone the repository and execute the Jupyter notebook or Python script provided. Make sure to install the required libraries using:
```bash
pip install -r requirements.txt
```

## License

This project is licensed under the MIT License.

---

By following this structure, you provide a comprehensive overview of the project, its purpose, and the methods used, making it easy for others to understand and contribute.
  
</p>
