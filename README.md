# Predicting Interview Attendance

#### Aim
A candidate not showing up to a scheduled interview wastes HR time and resources. In this case study, we would like to predict whether or not a candidate will attend a job interview based on 20 categorical features. In this case, we are interested in precision because our aim is to reduce false positives.

#### Data Source:
**Kaggle:** [Interview Attendance Problem](https://www.kaggle.com/vishnusraghavan/the-interview-attendance-problem)

|    | Date of Interview   | Client name   | Industry        | Location   | Position to be closed   | Nature of Skillset   | Interview Type   | Name(Cand ID)   | Gender   | Candidate Current Location   | Candidate Job Location   | Interview Venue   | Candidate Native location   | Have you obtained the necessary permission to start at the required time   | Hope there will be no unscheduled meetings   | Can I Call you three hours before the interview and follow up on your attendance for the interview   | Can I have an alternative number/ desk number. I assure you that I will not trouble you too much   | Have you taken a printout of your updated resume. Have you read the JD and understood the same   | Are you clear with the venue details and the landmark.   | Has the call letter been shared   | Expected Attendance   | Observed Attendance   | Marital Status   |   Unnamed: 23 |   Unnamed: 24 |   Unnamed: 25 |   Unnamed: 26 |   Unnamed: 27 |
|---:|:--------------------|:--------------|:----------------|:-----------|:------------------------|:---------------------|:-----------------|:----------------|:---------|:-----------------------------|:-------------------------|:------------------|:----------------------------|:---------------------------------------------------------------------------|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------|:---------------------------------------------------------|:----------------------------------|:----------------------|:----------------------|:-----------------|--------------:|--------------:|--------------:|--------------:|--------------:|
|  0 | 13.02.2015          | Hospira       | Pharmaceuticals | Chennai    | Production- Sterile     | Routine              | Scheduled Walkin | Candidate 1     | Male     | Chennai                      | Hosur                    | Hosur             | Hosur                       | Yes                                                                        | Yes                                          | Yes                                                                                                  | Yes                                                                                                | Yes                                                                                              | Yes                                                      | Yes                               | Yes                   | No                    | Single           |           nan |           nan |           nan |           nan |           nan |
|  1 | 13.02.2015          | Hospira       | Pharmaceuticals | Chennai    | Production- Sterile     | Routine              | Scheduled Walkin | Candidate 2     | Male     | Chennai                      | Bangalore                | Hosur             | Trichy                      | Yes                                                                        | Yes                                          | Yes                                                                                                  | Yes                                                                                                | Yes                                                                                              | Yes                                                      | Yes                               | Yes                   | No                    | Single           |           nan |           nan |           nan |           nan |           nan |
|  2 | 13.02.2015          | Hospira       | Pharmaceuticals | Chennai    | Production- Sterile     | Routine              | Scheduled Walkin | Candidate 3     | Male     | Chennai                      | Chennai                  | Hosur             | Chennai                     | nan                                                                        | Na                                           | nan                                                                                                  | nan                                                                                                | nan                                                                                              | nan                                                      | nan                               | Uncertain             | No                    | Single           |           nan |           nan |           nan |           nan |           nan |
|  3 | 13.02.2015          | Hospira       | Pharmaceuticals | Chennai    | Production- Sterile     | Routine              | Scheduled Walkin | Candidate 4     | Male     | Chennai                      | Chennai                  | Hosur             | Chennai                     | Yes                                                                        | Yes                                          | No                                                                                                   | Yes                                                                                                | No                                                                                               | Yes                                                      | Yes                               | Uncertain             | No                    | Single           |           nan |           nan |           nan |           nan |           nan |
|  4 | 13.02.2015          | Hospira       | Pharmaceuticals | Chennai    | Production- Sterile     | Routine              | Scheduled Walkin | Candidate 5     | Male     | Chennai                      | Bangalore                | Hosur             | Chennai                     | Yes                                                                        | Yes                                          | Yes                                                                                                  | No                                                                                                 | Yes                                                                                              | Yes                                                      | Yes                               | Uncertain             | No                    | Married          |           nan |           nan |           nan |           nan |           nan |

### I. Data Cleaning
1. Removed irrelevant columns:
  - Name of candidate
  - Date of interview
2. Renamed column names
3. Imputed NaN with 0
  - e.g., assumed if "Are you clear with venue details?" == NaN --> False
4. Cleaned string values
  - e.g., "Walkin" == "Walk in"
5. Dummy coded variables


|    | permission_start_on_time   | hope_no_unsch_meets   | call_three_hrs_before   | alt_num_given   | come_prepared   | can_find_interview_loc   | call_letter_shared   | expected_attendance   | observed_attendance   |   client_name_ANZ |   client_name_Aon Hewitt |   client_name_Aon hewitt Gurgaon |   client_name_Astrazeneca |   client_name_Barclays |   client_name_Flextronics |   client_name_Hewitt |   client_name_Hospira |   client_name_Pfizer |   client_name_Prodapt |   client_name_Standard Chartered Bank |   client_name_Standard Chartered Bank Chennai |   client_name_UST |   client_name_Williams Lea |   client_name_Woori Bank |   industry_BFSI |   industry_Electronics |   industry_IT |   industry_Pharmaceuticals |   industry_Telecom |   location_Bangalore |   location_Chennai |   location_Cochin |   location_Delhi |   location_Gurgaon |   location_Hyderabad |   location_Noida |   position_to_be_closed_AML |   position_to_be_closed_Dot Net |   position_to_be_closed_Niche |   position_to_be_closed_Production- Sterile |   position_to_be_closed_Routine |   position_to_be_closed_Selenium testing |   position_to_be_closed_Trade Finance |   interview_type_Scheduled |   interview_type_Scheduled_Walkin |   interview_type_Walkin |   gender_Female |   gender_Male |   candidate_current_location_Bangalore |   candidate_current_location_Chennai |   candidate_current_location_Cochin |   candidate_current_location_Delhi |   candidate_current_location_Gurgaon |   candidate_current_location_Hyderabad |   candidate_current_location_Noida |   candidate_job_location_Bangalore |   candidate_job_location_Chennai |   candidate_job_location_Cochin |   candidate_job_location_Gurgaon |   candidate_job_location_Hosur |   candidate_job_location_Noida |   candidate_job_location_Visakapatinam |   interview_venue_Bangalore |   interview_venue_Chennai |   interview_venue_Cochin |   interview_venue_Gurgaon |   interview_venue_Hosur |   interview_venue_Hyderabad |   interview_venue_Noida |   candidate_native_location_Agra |   candidate_native_location_Ahmedabad |   candidate_native_location_Allahabad |   candidate_native_location_Ambur |   candidate_native_location_Anantapur |   candidate_native_location_Baddi |   candidate_native_location_Bangalore |   candidate_native_location_Belgaum |   candidate_native_location_Bhubaneshwar |   candidate_native_location_Chandigarh |   candidate_native_location_Chennai |   candidate_native_location_Chitoor |   candidate_native_location_Cochin |   candidate_native_location_Coimbatore |   candidate_native_location_Cuttack |   candidate_native_location_Delhi |   candidate_native_location_Faizabad |   candidate_native_location_Ghaziabad |   candidate_native_location_Gurgaon |   candidate_native_location_Hissar |   candidate_native_location_Hosur |   candidate_native_location_Hyderabad |   candidate_native_location_Kanpur |   candidate_native_location_Kolkata |   candidate_native_location_Kurnool |   candidate_native_location_Lucknow |   candidate_native_location_Mumbai |   candidate_native_location_Mysore |   candidate_native_location_Nagercoil |   candidate_native_location_Noida |   candidate_native_location_Panjim |   candidate_native_location_Patna |   candidate_native_location_Pondicherry |   candidate_native_location_Pune |   candidate_native_location_Salem |   candidate_native_location_Tanjore |   candidate_native_location_Tirupati |   candidate_native_location_TricVellorehy |   candidate_native_location_Trichy |   candidate_native_location_Trivandrum |   candidate_native_location_Tuticorin |   candidate_native_location_Vijayawada |   candidate_native_location_Visakapatinam |   candidate_native_location_Warangal |   marital_status_Married |   marital_status_Single |
|---:|:---------------------------|:----------------------|:------------------------|:----------------|:----------------|:-------------------------|:---------------------|:----------------------|:----------------------|------------------:|-------------------------:|---------------------------------:|--------------------------:|-----------------------:|--------------------------:|---------------------:|----------------------:|---------------------:|----------------------:|--------------------------------------:|----------------------------------------------:|------------------:|---------------------------:|-------------------------:|----------------:|-----------------------:|--------------:|---------------------------:|-------------------:|---------------------:|-------------------:|------------------:|-----------------:|-------------------:|---------------------:|-----------------:|----------------------------:|--------------------------------:|------------------------------:|--------------------------------------------:|--------------------------------:|-----------------------------------------:|--------------------------------------:|---------------------------:|----------------------------------:|------------------------:|----------------:|--------------:|---------------------------------------:|-------------------------------------:|------------------------------------:|-----------------------------------:|-------------------------------------:|---------------------------------------:|-----------------------------------:|-----------------------------------:|---------------------------------:|--------------------------------:|---------------------------------:|-------------------------------:|-------------------------------:|---------------------------------------:|----------------------------:|--------------------------:|-------------------------:|--------------------------:|------------------------:|----------------------------:|------------------------:|---------------------------------:|--------------------------------------:|--------------------------------------:|----------------------------------:|--------------------------------------:|----------------------------------:|--------------------------------------:|------------------------------------:|-----------------------------------------:|---------------------------------------:|------------------------------------:|------------------------------------:|-----------------------------------:|---------------------------------------:|------------------------------------:|----------------------------------:|-------------------------------------:|--------------------------------------:|------------------------------------:|-----------------------------------:|----------------------------------:|--------------------------------------:|-----------------------------------:|------------------------------------:|------------------------------------:|------------------------------------:|-----------------------------------:|-----------------------------------:|--------------------------------------:|----------------------------------:|-----------------------------------:|----------------------------------:|----------------------------------------:|---------------------------------:|----------------------------------:|------------------------------------:|-------------------------------------:|------------------------------------------:|-----------------------------------:|---------------------------------------:|--------------------------------------:|---------------------------------------:|------------------------------------------:|-------------------------------------:|-------------------------:|------------------------:|
|  0 | True                       | True                  | True                    | True            | True            | True                     | True                 | True                  | False                 |                 0 |                        0 |                                0 |                         0 |                      0 |                         0 |                    0 |                     1 |                    0 |                     0 |                                     0 |                                             0 |                 0 |                          0 |                        0 |               0 |                      0 |             0 |                          1 |                  0 |                    0 |                  1 |                 0 |                0 |                  0 |                    0 |                0 |                           0 |                               0 |                             0 |                                           1 |                               0 |                                        0 |                                     0 |                          0 |                                 1 |                       0 |               0 |             1 |                                      0 |                                    1 |                                   0 |                                  0 |                                    0 |                                      0 |                                  0 |                                  0 |                                0 |                               0 |                                0 |                              1 |                              0 |                                      0 |                           0 |                         0 |                        0 |                         0 |                       1 |                           0 |                       0 |                                0 |                                     0 |                                     0 |                                 0 |                                     0 |                                 0 |                                     0 |                                   0 |                                        0 |                                      0 |                                   0 |                                   0 |                                  0 |                                      0 |                                   0 |                                 0 |                                    0 |                                     0 |                                   0 |                                  0 |                                 1 |                                     0 |                                  0 |                                   0 |                                   0 |                                   0 |                                  0 |                                  0 |                                     0 |                                 0 |                                  0 |                                 0 |                                       0 |                                0 |                                 0 |                                   0 |                                    0 |                                         0 |                                  0 |                                      0 |                                     0 |                                      0 |                                         0 |                                    0 |                        0 |                       1 |
|  1 | True                       | True                  | True                    | True            | True            | True                     | True                 | True                  | False                 |                 0 |                        0 |                                0 |                         0 |                      0 |                         0 |                    0 |                     1 |                    0 |                     0 |                                     0 |                                             0 |                 0 |                          0 |                        0 |               0 |                      0 |             0 |                          1 |                  0 |                    0 |                  1 |                 0 |                0 |                  0 |                    0 |                0 |                           0 |                               0 |                             0 |                                           1 |                               0 |                                        0 |                                     0 |                          0 |                                 1 |                       0 |               0 |             1 |                                      0 |                                    1 |                                   0 |                                  0 |                                    0 |                                      0 |                                  0 |                                  1 |                                0 |                               0 |                                0 |                              0 |                              0 |                                      0 |                           0 |                         0 |                        0 |                         0 |                       1 |                           0 |                       0 |                                0 |                                     0 |                                     0 |                                 0 |                                     0 |                                 0 |                                     0 |                                   0 |                                        0 |                                      0 |                                   0 |                                   0 |                                  0 |                                      0 |                                   0 |                                 0 |                                    0 |                                     0 |                                   0 |                                  0 |                                 0 |                                     0 |                                  0 |                                   0 |                                   0 |                                   0 |                                  0 |                                  0 |                                     0 |                                 0 |                                  0 |                                 0 |                                       0 |                                0 |                                 0 |                                   0 |                                    0 |                                         0 |                                  1 |                                      0 |                                     0 |                                      0 |                                         0 |                                    0 |                        0 |                       1 |
|  2 | False                      | False                 | False                   | False           | False           | False                    | False                | False                 | False                 |                 0 |                        0 |                                0 |                         0 |                      0 |                         0 |                    0 |                     1 |                    0 |                     0 |                                     0 |                                             0 |                 0 |                          0 |                        0 |               0 |                      0 |             0 |                          1 |                  0 |                    0 |                  1 |                 0 |                0 |                  0 |                    0 |                0 |                           0 |                               0 |                             0 |                                           1 |                               0 |                                        0 |                                     0 |                          0 |                                 1 |                       0 |               0 |             1 |                                      0 |                                    1 |                                   0 |                                  0 |                                    0 |                                      0 |                                  0 |                                  0 |                                1 |                               0 |                                0 |                              0 |                              0 |                                      0 |                           0 |                         0 |                        0 |                         0 |                       1 |                           0 |                       0 |                                0 |                                     0 |                                     0 |                                 0 |                                     0 |                                 0 |                                     0 |                                   0 |                                        0 |                                      0 |                                   1 |                                   0 |                                  0 |                                      0 |                                   0 |                                 0 |                                    0 |                                     0 |                                   0 |                                  0 |                                 0 |                                     0 |                                  0 |                                   0 |                                   0 |                                   0 |                                  0 |                                  0 |                                     0 |                                 0 |                                  0 |                                 0 |                                       0 |                                0 |                                 0 |                                   0 |                                    0 |                                         0 |                                  0 |                                      0 |                                     0 |                                      0 |                                         0 |                                    0 |                        0 |                       1 |
|  3 | True                       | True                  | False                   | True            | False           | True                     | True                 | False                 | False                 |                 0 |                        0 |                                0 |                         0 |                      0 |                         0 |                    0 |                     1 |                    0 |                     0 |                                     0 |                                             0 |                 0 |                          0 |                        0 |               0 |                      0 |             0 |                          1 |                  0 |                    0 |                  1 |                 0 |                0 |                  0 |                    0 |                0 |                           0 |                               0 |                             0 |                                           1 |                               0 |                                        0 |                                     0 |                          0 |                                 1 |                       0 |               0 |             1 |                                      0 |                                    1 |                                   0 |                                  0 |                                    0 |                                      0 |                                  0 |                                  0 |                                1 |                               0 |                                0 |                              0 |                              0 |                                      0 |                           0 |                         0 |                        0 |                         0 |                       1 |                           0 |                       0 |                                0 |                                     0 |                                     0 |                                 0 |                                     0 |                                 0 |                                     0 |                                   0 |                                        0 |                                      0 |                                   1 |                                   0 |                                  0 |                                      0 |                                   0 |                                 0 |                                    0 |                                     0 |                                   0 |                                  0 |                                 0 |                                     0 |                                  0 |                                   0 |                                   0 |                                   0 |                                  0 |                                  0 |                                     0 |                                 0 |                                  0 |                                 0 |                                       0 |                                0 |                                 0 |                                   0 |                                    0 |                                         0 |                                  0 |                                      0 |                                     0 |                                      0 |                                         0 |                                    0 |                        0 |                       1 |
|  4 | True                       | True                  | True                    | False           | True            | True                     | True                 | False                 | False                 |                 0 |                        0 |                                0 |                         0 |                      0 |                         0 |                    0 |                     1 |                    0 |                     0 |                                     0 |                                             0 |                 0 |                          0 |                        0 |               0 |                      0 |             0 |                          1 |                  0 |                    0 |                  1 |                 0 |                0 |                  0 |                    0 |                0 |                           0 |                               0 |                             0 |                                           1 |                               0 |                                        0 |                                     0 |                          0 |                                 1 |                       0 |               0 |             1 |                                      0 |                                    1 |                                   0 |                                  0 |                                    0 |                                      0 |                                  0 |                                  1 |                                0 |                               0 |                                0 |                              0 |                              0 |                                      0 |                           0 |                         0 |                        0 |                         0 |                       1 |                           0 |                       0 |                                0 |                                     0 |                                     0 |                                 0 |                                     0 |                                 0 |                                     0 |                                   0 |                                        0 |                                      0 |                                   1 |                                   0 |                                  0 |                                      0 |                                   0 |                                 0 |                                    0 |                                     0 |                                   0 |                                  0 |                                 0 |                                     0 |                                  0 |                                   0 |                                   0 |                                   0 |                                  0 |                                  0 |                                     0 |                                 0 |                                  0 |                                 0 |                                       0 |                                0 |                                 0 |                                   0 |                                    0 |                                         0 |                                  0 |                                      0 |                                     0 |                                      0 |                                         0 |                                    0 |                        1 |                       0 |


### II. Build Models

##### We built the following models using sklearn:
1. DecisionTreeClassifier
2. RandomForestClassifier
3. BaggingClassifier
4. GradientBoostingClassifier
5. AdaBoostClassifier
6. "MegaUltraClassifier"

##### Cross-validation
```python
def k_folds_CV(model, n_splits):
    scores = []
    kf = KFold(n_splits)
    for train_index, test_index in kf.split(X):
        Xk_train, Xk_test = X[train_index], X[test_index]
        yk_train, yk_test = y[train_index], y[test_index]
        model.fit(Xk_train, yk_train)
        preds = model.predict(Xk_test)
        score = precision_score(preds, yk_test)
        scores.append(score)
    cv_score = np.mean(scores)
    return cv_score
```

### III. Model Selection
Calculated precision scores for each model:

| Model        |          |
| ------------- |:-------------:|
| Decision Tree      | .70 |
| Random Forest      | .74      |  
| Bagging | .73     |  
| kNN | .59    |  
| GradientBoost | .75    |  
| AdaBoost | .77  |  

##### Grid Search
We selected the AdaBoost model based on highest precision scores, then conducted grid search to find the best parameter settings. We built a new model with those parameters.
CV Best Ada Precision: 0.83

#### Feature Importance
![feature](https://github.com/jackiekirschner/interview_attendance/blob/master/features_importances.png)

1. Have you obtained the necessary permission to start on time? 0.36
2. Interview Type Scheduled 0.14
3. Position to be closed Niche: 0.08
(Niche refers to rare skill sets while routine refers to more common skill sets)
4. Position to be closed Production- Sterile .02
5. Client Name ANZ: 0.04
6. Candidate Native Location Ahmedabad 0.02
7. Candidate Native Location Vijayawada 0.02


### Conclusion
Our cross-validated AdaBoost model with optimized parameters predicts false positives with 83% precision.

### Future Steps
1. Find optimal parameters across all models and compare across models
2. Look at partial dependence plots
3. Add logistic regression
