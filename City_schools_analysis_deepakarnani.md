

```python
# Dependencies and Setup
import pandas as pd
import numpy as np

# File to Load (Remember to Change These)
school_data = "Resources/schools_complete.csv"
student_data = "Resources/students_complete.csv"

# Read School and Student Data File and store into Pandas Data Frames
school_csv = pd.read_csv(school_data)
student_csv = pd.read_csv(student_data)

schools_df = school_csv.rename(columns={"name":"school"})
# Combine the data into a single dataset
data_complete = pd.merge(schools_df, student_csv, on='school')
# data_complete = pd.merge(student_csv, school_csv, how="left", left_on="school", right_on = "name")
```


```python
school_csv.head()
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
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
student_csv.head()
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
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_complete.head()
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
# data_complete.drop(['name_y'], axis = 1, inplace=True)
```


```python
# data_complete.rename(columns= {'name_x': 'student_name'}, inplace=True)
```


```python
data_complete.head()
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
total_schools = data_complete.school.nunique()
```


```python
total_students = data_complete.name.count()
total_students
```




    39170




```python
total_budget = school_csv.budget.sum()
```


```python
data_complete.school.value_counts(normalize=True)
```




    Bailey High School       0.127036
    Johnson High School      0.121547
    Hernandez High School    0.118330
    Rodriguez High School    0.102093
    Figueroa High School     0.075287
    Huang High School        0.074470
    Ford High School         0.069926
    Wilson High School       0.058284
    Cabrera High School      0.047434
    Wright High School       0.045954
    Shelton High School      0.044958
    Thomas High School       0.041741
    Griffin High School      0.037478
    Pena High School         0.024560
    Holden High School       0.010901
    Name: school, dtype: float64




```python
data_complete.columns
```




    Index(['School ID', 'school', 'type', 'size', 'budget', 'Student ID', 'name',
           'gender', 'grade', 'reading_score', 'math_score'],
          dtype='object')




```python
avg_math_score = data_complete.math_score.mean()
```


```python
avg_read_score = data_complete.reading_score.mean()
```


```python
data_complete.dtypes
```




    School ID         int64
    school           object
    type             object
    size              int64
    budget            int64
    Student ID        int64
    name             object
    gender           object
    grade            object
    reading_score     int64
    math_score        int64
    dtype: object




```python
# data_complete = data_complete.dropna(how = 'any')
data_complete.count()
```




    School ID        39170
    school           39170
    type             39170
    size             39170
    budget           39170
    Student ID       39170
    name             39170
    gender           39170
    grade            39170
    reading_score    39170
    math_score       39170
    dtype: int64




```python
# data_complete.reset_index(level = 'school', col_level=1)
```


```python
# total_students_perschool = data_complete(['student_name']).size()["student_name"]
```


```python
passing_math = (data_complete.loc[data_complete['math_score']>=70]).count()["name"]
math_passing = (passing_math/total_students)*100
math_passing
```




    74.9808526933878




```python
passing_read = (data_complete.loc[data_complete['reading_score']>=70]).count()["name"]
read_passing = (passing_read/total_students)*100
read_passing
```




    85.80546336482001




```python
math_read_passing = (read_passing + math_passing)/2
math_read_passing
```




    80.39315802910392




```python
school_summary = pd.DataFrame({"Total Schools": [total_schools],
                                 "Total Students": [total_students],
                                 "Total Budgets": [total_budget],
                                 "Average Math Score": [avg_math_score],
                                 "Average Reading Score": [avg_read_score],
                                 "% Passing Math": [math_passing],
                                 "% Passing Reading": [read_passing],
                                 "Overall Passing Rate": [math_read_passing]})

school_summary = school_summary[["Total Schools", 
                                     "Total Students", 
                                     "Total Budgets", 
                                     "Average Math Score", 
                                     "Average Reading Score",
                                     "% Passing Math",
                                     "% Passing Reading",
                                     "Overall Passing Rate"]]

school_summary
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
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budgets</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15</td>
      <td>39170</td>
      <td>24649428</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>74.980853</td>
      <td>85.805463</td>
      <td>80.393158</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_type = schools_df.set_index(["school"])["type"]
school_type
```




    school
    Huang High School        District
    Figueroa High School     District
    Shelton High School       Charter
    Hernandez High School    District
    Griffin High School       Charter
    Wilson High School        Charter
    Cabrera High School       Charter
    Bailey High School       District
    Holden High School        Charter
    Pena High School          Charter
    Wright High School        Charter
    Rodriguez High School    District
    Johnson High School      District
    Ford High School         District
    Thomas High School        Charter
    Name: type, dtype: object




```python
students_per_school = data_complete.groupby('school')['name'].count()
students_per_school
```




    school
    Bailey High School       4976
    Cabrera High School      1858
    Figueroa High School     2949
    Ford High School         2739
    Griffin High School      1468
    Hernandez High School    4635
    Holden High School        427
    Huang High School        2917
    Johnson High School      4761
    Pena High School          962
    Rodriguez High School    3999
    Shelton High School      1761
    Thomas High School       1635
    Wilson High School       2283
    Wright High School       1800
    Name: name, dtype: int64




```python
total_budget_per_school = schools_df.set_index('school')['budget']
total_budget_per_school
```




    school
    Huang High School        1910635
    Figueroa High School     1884411
    Shelton High School      1056600
    Hernandez High School    3022020
    Griffin High School       917500
    Wilson High School       1319574
    Cabrera High School      1081356
    Bailey High School       3124928
    Holden High School        248087
    Pena High School          585858
    Wright High School       1049400
    Rodriguez High School    2547363
    Johnson High School      3094650
    Ford High School         1763916
    Thomas High School       1043130
    Name: budget, dtype: int64




```python
total_budget_per_student = total_budget_per_school/students_per_school
total_budget_per_student
```




    school
    Bailey High School       628.0
    Cabrera High School      582.0
    Figueroa High School     639.0
    Ford High School         644.0
    Griffin High School      625.0
    Hernandez High School    652.0
    Holden High School       581.0
    Huang High School        655.0
    Johnson High School      650.0
    Pena High School         609.0
    Rodriguez High School    637.0
    Shelton High School      600.0
    Thomas High School       638.0
    Wilson High School       578.0
    Wright High School       583.0
    dtype: float64




```python
avg_math_score_per_school = data_complete.groupby('school')['math_score'].mean()
avg_math_score_per_school
```




    school
    Bailey High School       77.048432
    Cabrera High School      83.061895
    Figueroa High School     76.711767
    Ford High School         77.102592
    Griffin High School      83.351499
    Hernandez High School    77.289752
    Holden High School       83.803279
    Huang High School        76.629414
    Johnson High School      77.072464
    Pena High School         83.839917
    Rodriguez High School    76.842711
    Shelton High School      83.359455
    Thomas High School       83.418349
    Wilson High School       83.274201
    Wright High School       83.682222
    Name: math_score, dtype: float64




```python
avg_read_score_per_school = data_complete.groupby('school')['reading_score'].mean()
avg_read_score_per_school
```




    school
    Bailey High School       81.033963
    Cabrera High School      83.975780
    Figueroa High School     81.158020
    Ford High School         80.746258
    Griffin High School      83.816757
    Hernandez High School    80.934412
    Holden High School       83.814988
    Huang High School        81.182722
    Johnson High School      80.966394
    Pena High School         84.044699
    Rodriguez High School    80.744686
    Shelton High School      83.725724
    Thomas High School       83.848930
    Wilson High School       83.989488
    Wright High School       83.955000
    Name: reading_score, dtype: float64




```python
passing_math_per_school = data_complete[(data_complete["math_score"] >= 70)]
math_passing_per_school = passing_math_per_school.groupby(["school"]).count()["name"] / students_per_school * 100
math_passing_per_school
```




    school
    Bailey High School       66.680064
    Cabrera High School      94.133477
    Figueroa High School     65.988471
    Ford High School         68.309602
    Griffin High School      93.392371
    Hernandez High School    66.752967
    Holden High School       92.505855
    Huang High School        65.683922
    Johnson High School      66.057551
    Pena High School         94.594595
    Rodriguez High School    66.366592
    Shelton High School      93.867121
    Thomas High School       93.272171
    Wilson High School       93.867718
    Wright High School       93.333333
    Name: name, dtype: float64




```python
passing_read_per_school = data_complete[(data_complete["reading_score"] >= 70)]
read_passing_per_school = passing_read_per_school.groupby(["school"]).count()["name"] / students_per_school * 100
read_passing_per_school
```




    school
    Bailey High School       81.933280
    Cabrera High School      97.039828
    Figueroa High School     80.739234
    Ford High School         79.299014
    Griffin High School      97.138965
    Hernandez High School    80.862999
    Holden High School       96.252927
    Huang High School        81.316421
    Johnson High School      81.222432
    Pena High School         95.945946
    Rodriguez High School    80.220055
    Shelton High School      95.854628
    Thomas High School       97.308869
    Wilson High School       96.539641
    Wright High School       96.611111
    Name: name, dtype: float64




```python
math_read_passing_per_school = (read_passing_per_school + math_passing_per_school)/2
math_read_passing_per_school
```




    school
    Bailey High School       74.306672
    Cabrera High School      95.586652
    Figueroa High School     73.363852
    Ford High School         73.804308
    Griffin High School      95.265668
    Hernandez High School    73.807983
    Holden High School       94.379391
    Huang High School        73.500171
    Johnson High School      73.639992
    Pena High School         95.270270
    Rodriguez High School    73.293323
    Shelton High School      94.860875
    Thomas High School       95.290520
    Wilson High School       95.203679
    Wright High School       94.972222
    Name: name, dtype: float64




```python


schools_summary = pd.DataFrame({
    "School Type": school_type,
    "Total Students": students_per_school,
    "Total School Budget": total_budget_per_school,
    "Per Student Budget": total_budget_per_student,
    "Average Math Score": avg_math_score_per_school,
    "Average Reading Score": avg_read_score_per_school,
    "% Passing Math": math_passing_per_school,
    "% Passing Reading": read_passing_per_school,
    "Overall Passing Rate": math_read_passing_per_school
})
schools_summary


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
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Overall Passing Rate</th>
      <th>Per Student Budget</th>
      <th>School Type</th>
      <th>Total School Budget</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>74.306672</td>
      <td>628.0</td>
      <td>District</td>
      <td>3124928</td>
      <td>4976</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>95.586652</td>
      <td>582.0</td>
      <td>Charter</td>
      <td>1081356</td>
      <td>1858</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>73.363852</td>
      <td>639.0</td>
      <td>District</td>
      <td>1884411</td>
      <td>2949</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>73.804308</td>
      <td>644.0</td>
      <td>District</td>
      <td>1763916</td>
      <td>2739</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>95.265668</td>
      <td>625.0</td>
      <td>Charter</td>
      <td>917500</td>
      <td>1468</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>73.807983</td>
      <td>652.0</td>
      <td>District</td>
      <td>3022020</td>
      <td>4635</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>94.379391</td>
      <td>581.0</td>
      <td>Charter</td>
      <td>248087</td>
      <td>427</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>73.500171</td>
      <td>655.0</td>
      <td>District</td>
      <td>1910635</td>
      <td>2917</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>73.639992</td>
      <td>650.0</td>
      <td>District</td>
      <td>3094650</td>
      <td>4761</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.270270</td>
      <td>609.0</td>
      <td>Charter</td>
      <td>585858</td>
      <td>962</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>73.293323</td>
      <td>637.0</td>
      <td>District</td>
      <td>2547363</td>
      <td>3999</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.860875</td>
      <td>600.0</td>
      <td>Charter</td>
      <td>1056600</td>
      <td>1761</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>95.290520</td>
      <td>638.0</td>
      <td>Charter</td>
      <td>1043130</td>
      <td>1635</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>95.203679</td>
      <td>578.0</td>
      <td>Charter</td>
      <td>1319574</td>
      <td>2283</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>94.972222</td>
      <td>583.0</td>
      <td>Charter</td>
      <td>1049400</td>
      <td>1800</td>
    </tr>
  </tbody>
</table>
</div>




```python

schools_summary = schools_summary[['School Type', 'Total Students', 'Total School Budget', 'Per Student Budget', 
                                             'Average Math Score', 'Average Reading Score','% Passing Math', '% Passing Reading', 
                                             'Overall Passing Rate'
                                            ]]
schools_summary.head(30)


# #formatting
# schools_summary.style.format({'Total Students': '{:,}', 
#                           "Total School Budget": "${:,}", 
#                           "Per Student Budget": "${:.0f}",
#                           'Average Math Score': "{:.1f}", 
#                           'Average Reading Score': "{:.1f}", 
#                           "% Passing Math": "{:.1%}", 
#                           "% Passing Reading": "{:.1%}", 
#                           "Overall Passing Rate": "{:.1%}"})

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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>74.306672</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>73.807983</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>94.860875</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>94.972222</td>
    </tr>
  </tbody>
</table>
</div>




```python
schools_summary.nlargest(5, 'Overall Passing Rate')
        
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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
  </tbody>
</table>
</div>




```python
schools_summary.nsmallest(5, 'Overall Passing Rate')
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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
  </tbody>
</table>
</div>




```python
nineth_grade = data_complete[(data_complete["grade"] == "9th")]
tenth_grade = data_complete[(data_complete["grade"] == "10th")]
eleventh_grade = data_complete[(data_complete["grade"] == "11th")]
twelfth_grade = data_complete[(data_complete["grade"] == "12th")]

nineth_math = nineth_grade.groupby(["school"]).mean()["math_score"]
tenth_math = tenth_grade.groupby(["school"]).mean()["math_score"]
eleventh_math = eleventh_grade.groupby(["school"]).mean()["math_score"]
twelfth_math = twelfth_grade.groupby(["school"]).mean()["math_score"]

math_scores_by_grade = pd.DataFrame({"9th Grade": nineth_math, 
                                     "10th Grade": tenth_math,
                                     "11th Grade": eleventh_math,
                                     "12th Grade": twelfth_math})

math_scores_by_grade = math_scores_by_grade[["9th Grade", "10th Grade", "11th Grade", "12th Grade"]]

math_scores_by_grade
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
      <th>9th Grade</th>
      <th>10th Grade</th>
      <th>11th Grade</th>
      <th>12th Grade</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>




```python
nineth_read = nineth_grade.groupby(["school"]).mean()["reading_score"]
tenth_read = tenth_grade.groupby(["school"]).mean()["reading_score"]
eleventh_read = eleventh_grade.groupby(["school"]).mean()["reading_score"]
twelfth_read = twelfth_grade.groupby(["school"]).mean()["reading_score"]

reading_scores_by_grade = pd.DataFrame({"9th Grade": nineth_read, 
                                        "10th Grade": tenth_read,
                                        "11th Grade": eleventh_read,
                                        "12th Grade": twelfth_read})

reading_scores_by_grade = reading_scores_by_grade[["9th Grade", "10th Grade", "11th Grade", "12th Grade"]]

reading_scores_by_grade
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
      <th>9th Grade</th>
      <th>10th Grade</th>
      <th>11th Grade</th>
      <th>12th Grade</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Bins
spending_bins = [0, 585, 615, 645, 675]
group_names = ["<$585", "$585-615", "$615-645", "$645-675"]

schools_summary["Per Student Budget"] = pd.cut(total_budget_per_student, spending_bins, labels=group_names)

scores_spending_math = schools_summary.groupby(["Per Student Budget"]).mean()["Average Math Score"]
scores_spending_reading = schools_summary.groupby(["Per Student Budget"]).mean()["Average Reading Score"]
scores_spending_passing_math = schools_summary.groupby(["Per Student Budget"]).mean()["% Passing Math"]
scores_spending_passing_reading = schools_summary.groupby(["Per Student Budget"]).mean()["% Passing Reading"]
scores_spending_overall_passing_rate = (scores_spending_passing_math + scores_spending_passing_reading) / 2

scores_by_school_spending_summary = pd.DataFrame({"Average Math Score": scores_spending_math,
                                                  "Average Reading Score": scores_spending_reading,
                                                  "% Passing Math": scores_spending_passing_math,
                                                  "% Passing Reading": scores_spending_passing_reading, 
                                                  "Overall Passing Rate": scores_spending_overall_passing_rate})

scores_by_school_spending_summary = scores_by_school_spending_summary[["Average Math Score",
                                                                       "Average Reading Score", 
                                                                       "% Passing Math", 
                                                                       "% Passing Reading", 
                                                                       "Overall Passing Rate"]]

scores_by_school_spending_summary.fillna(0)
scores_by_school_spending_summary
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Per Student Budget</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;$585</th>
      <td>83.455399</td>
      <td>83.933814</td>
      <td>93.460096</td>
      <td>96.610877</td>
      <td>95.035486</td>
    </tr>
    <tr>
      <th>$585-615</th>
      <td>83.599686</td>
      <td>83.885211</td>
      <td>94.230858</td>
      <td>95.900287</td>
      <td>95.065572</td>
    </tr>
    <tr>
      <th>$615-645</th>
      <td>79.079225</td>
      <td>81.891436</td>
      <td>75.668212</td>
      <td>86.106569</td>
      <td>80.887391</td>
    </tr>
    <tr>
      <th>$645-675</th>
      <td>76.997210</td>
      <td>81.027843</td>
      <td>66.164813</td>
      <td>81.133951</td>
      <td>73.649382</td>
    </tr>
  </tbody>
</table>
</div>




```python
# grouping by school size
size_bins = [0, 1000, 2000, 5000]
group_names = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]

schools_summary["School Size"] = pd.cut(schools_summary["Total Students"], size_bins, labels=group_names)

scores_size_math = schools_summary.groupby(["School Size"]).mean()["Average Math Score"]
scores_size_reading = schools_summary.groupby(["School Size"]).mean()["Average Reading Score"]
scores_size_passing_math = schools_summary.groupby(["School Size"]).mean()["% Passing Math"]
scores_size_passing_reading = schools_summary.groupby(["School Size"]).mean()["% Passing Reading"]
scores_size_overall_passing_rate = (scores_size_passing_math + scores_size_passing_reading) / 2

scores_by_school_size_summary = pd.DataFrame({"Average Math Score": scores_size_math,
                                              "Average Reading Score": scores_size_reading,
                                              "% Passing Math": scores_size_passing_math,
                                              "% Passing Reading": scores_size_passing_reading,
                                              "Overall Passing Rate": scores_size_overall_passing_rate})

scores_by_school_size_summary = scores_by_school_size_summary[["Average Math Score",
                                                               "Average Reading Score", 
                                                               "% Passing Math", 
                                                               "% Passing Reading", 
                                                               "Overall Passing Rate"]]

scores_by_school_size_summary
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small (&lt;1000)</th>
      <td>83.821598</td>
      <td>83.929843</td>
      <td>93.550225</td>
      <td>96.099437</td>
      <td>94.824831</td>
    </tr>
    <tr>
      <th>Medium (1000-2000)</th>
      <td>83.374684</td>
      <td>83.864438</td>
      <td>93.599695</td>
      <td>96.790680</td>
      <td>95.195187</td>
    </tr>
    <tr>
      <th>Large (2000-5000)</th>
      <td>77.746417</td>
      <td>81.344493</td>
      <td>69.963361</td>
      <td>82.766634</td>
      <td>76.364998</td>
    </tr>
  </tbody>
</table>
</div>




```python
scores_type_avg_math = schools_summary.groupby(["School Type"]).mean()["Average Math Score"]
scores_type_avg_reading = schools_summary.groupby(["School Type"]).mean()["Average Reading Score"]
scores_type_passing_math = schools_summary.groupby(["School Type"]).mean()["% Passing Math"]
scores_type_passing_reading = schools_summary.groupby(["School Type"]).mean()["% Passing Reading"]
scores_overall_passing_rate = (scores_type_passing_math + scores_type_passing_reading) / 2 

scores_by_school_type_summary = pd.DataFrame({"Average Math Score": scores_type_avg_math, 
                                              "Average Reading Score": scores_type_avg_reading,
                                              "% Passing Math": scores_type_passing_math, 
                                              "% Passing Reading": scores_type_passing_reading,
                                              "Overall Passing Rate": scores_overall_passing_rate})

scores_by_school_type_summary = scores_by_school_type_summary[["Average Math Score", 
                                                               "Average Reading Score", 
                                                               "% Passing Math", 
                                                               "% Passing Reading", 
                                                               "Overall Passing Rate"]]

scores_by_school_type_summary

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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.473852</td>
      <td>83.896421</td>
      <td>93.620830</td>
      <td>96.586489</td>
      <td>95.103660</td>
    </tr>
    <tr>
      <th>District</th>
      <td>76.956733</td>
      <td>80.966636</td>
      <td>66.548453</td>
      <td>80.799062</td>
      <td>73.673757</td>
    </tr>
  </tbody>
</table>
</div>



Conclusion:
1. From data, charter schools perform better academically than district schools.
2. From data, the smaller school size correlate to better student performance.
