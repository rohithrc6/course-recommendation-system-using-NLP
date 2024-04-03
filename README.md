## 1. Coursera Course Recommendation System
**Project Title:** Coursera Course Recommendation System

[![YouTube Presentation](https://img.shields.io/badge/-YouTube%20WebApp%20Working%20Demo-FF0000?logo=youtube&style=flat)](https://youtu.be/L3OfajGpx7M)


## 2. Background

### What is it about?
As part of this project, we will be using a course recommendation system to recommend courses to learners based on course rating, skills, course name, course description, etc. We can use content-based similarity filtering or collaborative filtering or a hybrid approach that uses both to make recommendations.

### Why does it matter?
The project addresses a specific problem or question relevant to a particular online education domain. By providing solutions or insights into this problem, it has the potential to make a decent impact on that domain. This problem-solving aspect is at the core of data science's practical applications.

### Some of the Research questions that will be addressed
- How can we create a course recommendation system that takes into account each user's unique learning preferences and history?

- What methods can be used to personalize course recommendations based on a user's academic or career goals?
- How can we address the "cold-start" problem, where the system needs to recommend courses to new users with limited interaction history?
- What strategies can be employed to make relevant recommendations to new users or users with sparse activity?

## 3. Data

[![Data Source](https://img.shields.io/badge/-Data%20Source-1E90FF&style=flat)](https://www.kaggle.com/datasets/khusheekapoor/coursera-courses-dataset-2021)


### Data Size
8.72 MB

### Data Shape
Before Data Cleaning - 3522 rows x 7 columns

After Data Cleaning - 3392 rows x 8 columns

### Each Row Represents
A course on Coursera

### Columns Details:

Before Data Cleaning:

| Column             | Non-Null Count | Dtype  |
|--------------------|----------------|-------|
| Course Name        | 3522 non-null  | object|
| University         | 3522 non-null  | object|
| Difficulty Level   | 3522 non-null  | object|
| Course Rating      | 3522 non-null  | object|
| Course URL         | 3522 non-null  | object|
| Course Description | 3522 non-null  | object|
| Skills             | 3522 non-null  | object|

After Data Cleaning:

| Column             | Non-Null Count | Dtype  |
|--------------------|----------------|-------|
| Index              | 3392 non-null  | int64|
| Course Name        | 3392 non-null  | object|
| University         | 3392 non-null  | object|
| Difficulty Level   | 3392 non-null  | object|
| Course Rating      | 3392 non-null  | float64|
| Course URL         | 3392 non-null  | object|
| Course Description | 3392 non-null  | object|
| Skills             | 3392 non-null  | object|
 
### Target/Label Variable
There is no target variable as this is a recommendation system.

### Features/Predictors
Features used for recommendation - Course Name, Course Description, Difficulty Level, Skills

## 4. EDA

### Data Cleansing and Preparation

In this recommendation system to perform data preprocessing and feature extraction we import the necessary libraries and then perform vectorization and stemming processes. We perform these two tasks on the column 'Tokens', which is a combination of columns 'Course Name', 'Course Description', 'Skills', and 'Difficulty Level'. So to make the data ready for these tasks we remove all the special characters (like,(,),-, etc.) in between words from the four columns mentioned in the previous statement and then make sure that they are only separated by single spaces. Then we concat the four columns into a new column called 'Tokens'. With this, the data is ready for vectorization and stemming processes. We perform these two tasks on a new data frame called 'CourseData'.

### Visualizations and Interpretations

- Universities CertNexus, SV Academy, and Karlsruhe Institute for Technology have the highest course ratings.
- Universities Universidad Nacional Autnoma de Mxico, Carnegie Mellon University, and Yandex have the lowest course ratings.
- Courses from almost all difficulty levels have an average course rating of 4.5
- Number of courses by difficulty level

| Difficulty Level| Count| 
|-----------------|------|
| Beginner        | 1425 | 
| Advanced        | 969  |
| Intermediate    | 823  |
| Conversant      | 175  |

![image](https://github.com/DATA-606-2023-FALL-TUESDAY/Challa_Rohith/assets/97656473/c66da3fb-8e23-440a-a3d9-414c65033f36)

Most of the courses are beginner-level level and the rest of them mostly being advanced and intermediate.

Due to the nature of the dataset, there is relatively less scope for visualizations and interpretations.

## 5. Model

- Model: Item-based collaborative filtering, stemming, and vectorization

Implemented stemming and vectorization NLP techniques using the NLTK module. Made use of the Porter Stemmer module to create a stemming function that takes a token (a string of words) and applies stemming to each word in the token. The 'Tokens' column in 'courseData' dataframe undergoes stemming to ensure consistency in word representation. The Scikit-learn library's CountVectorizer is utilized to convert the text data into a document-term matrix. A maximum of 20,000 features (words) is set to capture a wide range of vocabulary. The 'Tokens' column in 'courseData' is transformed into a numerical format suitable for machine learning models.
- Training: Computed cosine-similarity matrix to obtain the cosine similarities of all the vectors with each other.
- Python packages: pandas, numpy, pickle, matplotlib, nltk, scikit-learn
- Development environment: Google CoLab

## 6. Application of the Model
Below is a screenshot from the web application that was developed using Streamlit. For a given course of interest, it recommends courses along with their course ratings and difficulty levels.![image](https://github.com/DATA-606-2023-FALL-TUESDAY/Challa_Rohith/blob/main/docs/WebApp_SS.png)

### Instructions to run the web page:

1. Download all the necessary files: Course Recommendation System.ipynb, Coursera.csv, courses.pkl, coursesFull.pkl, similarity.pkl, web_app.ipynb, courseimage.jpeg, web_app_script1.py

Note: All the files except similarity.pkl are available in the docs folder of this repository. The 'similarity.pkl' file can be downloaded  after executing the main notebook 'Course Recommendation System.ipynb'.

2. Run the web_app notebook and open the URL in the last cell (the link next to 'your url is'), and then paste the IP obtained in the last but one cell in the appropriate field of the URL mentioned previously.
3. Make sure to install the streamlit package before executing the web_app notebook.

## 7. Conclusion

### Summary
The presented work involves the development of a Coursera Course Recommendation System. It includes data cleaning, analysis, and visualization to derive insights into universities, course ratings, and difficulty levels. The pre-processing step involves tokenization, stemming, and vectorization of course data, enabling the computation of cosine similarity for course recommendations. paraphrase.
### Potential Application
The Coursera Course Recommendation System serves as a valuable tool for learners, providing personalized course suggestions based on user input. This can significantly enhance the user experience on the platform, making course discovery more tailored and efficient.
### Limitations
While the system offers personalized recommendations, it relies on user interaction data, which may introduce biases. Additionally, the system's effectiveness could be influenced by the availability and quality of data. Acknowledging these limitations is crucial for managing user expectations.
### Lessons Learned
The data cleaning and pre-processing steps are critical for building a robust recommendation system. Handling Inaccurate values, and data types, and removing non-alphabetic characters are key aspects of preparing the data. Stemming and vectorization contribute to the effectiveness of the recommendation algorithm.
### Future Research Direction
Future research can explore advanced recommendation techniques, considering additional features such as course content or user demographics. Addressing biases and improving the handling of new courses could enhance the system's accuracy. Exploring emerging technologies or methodologies in recommendation systems is also a potential avenue for future research.

## 8. References

- [![References](https://img.shields.io/badge/-References-9cf?style=flat)](https://www.kaggle.com/code/sagarbapodara/coursera-course-recommendation-system-webapp)
