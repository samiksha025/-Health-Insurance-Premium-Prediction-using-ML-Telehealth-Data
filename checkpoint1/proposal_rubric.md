# Rubric for Project Proposal

Your project proposal will follow the format of a standard research proposal, and will be written in markdown format.  It will be saved in the same directory as this rubric, and simply named "proposal.md."  It should not be longer than 2-3 pages max, and may be shorter.  It will have the following sections.

### Title

A nice short title for your project, helping me to understand roughly what it is you are trying to do.

### Team

Each project will have a team of 3-5 people, and one person will serve as the point of contact (POC) for the team who will own the repository. The POC will be responsible for managing the repository, and I will only grade submissions in this repository. Everyone will be granted access to this repository.  This section should include the full names of each team member, **along with their github ids**, and indicate the POC for the group.

### Introduction

This section will introduce your project.  It will _briefly_ answer the following questions from [Heilmeier's catechism](https://www.darpa.mil/work-with-us/heilmeier-catechism).

- What are you trying to do? Articulate your objectives using absolutely no jargon.
- What is new in your approach and why do you think it will be successful?  (be brief here, you can expand more later!)
- Who cares? If you are successful, what difference will it make?

### Literature Review

This section will answer the second question from Heilmeier's catechism:

- How is it done today, and what are the limits of current practice?

Here, you will review methods that have been attempted (use [Google Scholar](https://scholar.google.com) to find out), or cite literature to provide evidence that your method is novel.  You should include citations to reviewed material.  Use [github's markdown syntax for footnotes](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#footnotes)[^1].

Also use this section to establish _stakeholder needs_.  That is, for stakeholders that have specific but perhaps non-obvious needs (e.g., a city traffic planner will need to know about temporal variation in pedestrian traffic and the density of office buildings in order to determine the best placement of traffic signals).  You should list each of your stakeholders here, explain why they are stakeholders, and the clarify needs. Recall from our lecture that I do not expect you to do your own stakeholder interviews, but I do expect you to do a little research online.

### Data and Methods

This section will introduce your data and specify your modeling approach.

#### Data

You will include a link to your data, along with summary information (e.g., how many columns, rows, and the types of features).  Also include some discussion about the data's provenance - how do you know the data is reliable?  Does it have meta data, and if not, what else do you know about it?  If you anticipate needing more than one dataset, please indicate each dataset you anticipate needing and provide evidence that those datasets are available.

#### Methods

Describe your modeling approach.  What sorts of transformations / preprocessing are going to be necessary?  What sorts of modeling techniques will you apply? How are you going to evaluate your models (note that your evaluation should be consistent with stakeholder needs)?

### Project Plan

The project will be completed over the next two months, with key milestones and activities scheduled to ensure a structured workflow.  
 
>> From March 4 to March 11, the focus will be on conducting a stakeholder analysis and performing Exploratory Data Analysis (EDA). This will include identifying correlations between features, handling missing values and outliers, and understanding key trends in the dataset. By the end of this phase, we aim to have a clear understanding of how different variables contribute to insurance costs.  
 
>> Between March 11 and March 18, data preprocessing will take place. This involves encoding categorical variables, scaling numerical features, and preparing the dataset for modeling. The first baseline model, using Linear Regression, will be implemented to provide an initial benchmark for evaluating predictions. This phase will conclude with a clean and structured dataset, along with preliminary insights from the baseline model.  
 

>> From March 18 to March 25, advanced machine learning models such as Decision Trees, Random Forests, and Gradient Boosting will be trained. Hyperparameter tuning will be applied to optimize model performance. Feature selection techniques will be explored to improve prediction accuracy by identifying the most relevant features affecting insurance charges. The goal of this phase is to compare multiple models and determine the most promising approaches for further refinement.  
 
>> During March 25 to April 1, Artificial Neural Networks (ANNs) will be introduced to analyze deeper patterns within the data. The results from neural networks will be compared with those from traditional ML models to evaluate improvements in accuracy. Cross-validation will be performed to ensure that the models generalize well to unseen data. By the end of this phase, the best-performing models will be finalized for evaluation.  
 
>> From April 1 to April 8, model evaluation will take place using performance metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared scores. Feature importance analysis will be conducted using SHAP or LIME to enhance interpretability. This phase will focus on extracting key insights that can be used to explain the model’s predictions to stakeholders.  
 
>> Between April 8 and April 15, an interactive dashboard will be developed using Tableau or Streamlit. The dashboard will allow users to input personal attributes and receive an estimated insurance cost based on the trained models. This will enhance the project’s usability and provide a practical implementation of the findings.  
 
>> From April 15 to April 22, efforts will be directed toward refining the final report and creating visualizations for the presentation. Results will be validated, and necessary adjustments will be made to improve clarity and impact. The goal is to have a comprehensive draft ready for review.  
 
>> Finally, from April 22 to April 29, the project will undergo a final review. Presentation slides will be prepared, and the report will be finalized. By the end of this phase, the complete project, including all deliverables, will be ready for submission.  
 


### Risks

One of the primary risks in this project is data quality issues, including missing values, incorrect data, or biases that could affect model predictions. To mitigate this, thorough data cleaning and imputation techniques will be applied, and data balancing techniques will be explored if necessary.  
 
Another risk is model overfitting, where the model performs exceptionally well on training data but fails to generalize to unseen data. To address this, techniques such as cross-validation, regularization, and optimal hyperparameter selection will be implemented to ensure the model remains robust and reliable.  
 
Model interpretability is another potential challenge, especially with complex algorithms like Artificial Neural Networks. Since interpretability is crucial for stakeholders, SHAP or LIME will be used to provide explanations on feature importance and decision-making within the model.  
 
Computational constraints may arise, particularly when training resource-intensive models like XGBoost or deep learning networks. To manage this, feature selection techniques will be applied to reduce dataset dimensionality, and cloud-based computing solutions may be leveraged if needed.  
 
There is also a risk that stakeholder needs may evolve over time, requiring adjustments to the model or additional feature integration. To mitigate this, continuous feedback loops will be maintained, allowing for iterative improvements based on stakeholder inputs and findings.  
 
Lastly, time constraints pose a challenge, given the complexity of the tasks involved. To ensure smooth progress, the project will adhere to a structured timeline, with critical tasks prioritized, allowing flexibility for refinements while meeting deadlines.  
 
By proactively addressing these risks and maintaining a structured workflow, the project is expected to successfully deliver an accurate and interpretable machine learning model for predicting medical insurance costs.
has context menu


# Grading

- Does your proposal include all of the above mentioned sections? [1 point]
- Have you clearly identifed your stakeholders and their needs [1 point]
- Have you answered the 5 Heilmeier questions mentioned effectively [1 point]
- Is you proposal plan feasible, and do you have sufficient detail to give me confidence that you will succeed? [1 point]
- Did your presentation address all required points and follow the structure provided above [1 point] 

[^1]: Like this




