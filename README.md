# Data-Science-Jobs-Analysis
This project provides insights into the Data Science job market, analyzing job descriptions, salary estimates, required skills, and location-based trends. It uses a cleaned dataset of job postings to create meaningful visualizations and uncover trends that can guide professionals in the field.

Project Overview
The goal of this project is to:

Clean and preprocess job data from an unstructured dataset.
Extract and analyze key features such as salaries, skills, and job locations.
Visualize trends to understand demand and compensation in the Data Science job market.
Dataset
The dataset used for this analysis includes job postings with information such as:

Job Titles
Company Names
Job Descriptions
Salary Estimates
Locations (state, city)
Company Ratings
Other metadata such as size, revenue, and competitors.
Key Features of the Project
Data Cleaning:

Removed duplicates and null values.
Extracted structured information like salary ranges and states from unstructured data.
Feature Engineering:

Created new columns for minimum, maximum, and average salaries.
Mapped state abbreviations to full names.
Extracted key skills (e.g., Python, SQL, Tableau) from job descriptions.
Analysis & Visualizations:

Salary distribution analysis and visualization.
Top 10 most common job titles and their frequency.
Average salary by state.
Top states by job count.
Insights:

Identified high-demand skills for Data Science roles.
Highlighted states offering higher average salaries.
Categorized jobs into salary ranges (Low, Mid, High, Very High).
Project Structure
bash
Copy code
.
├── Uncleaned_Ds_jobs.csv   # Dataset file
├── Final.ipynb          # Jupyter Notebook with full code and explanations
├── README.md               # Project documentation (this file)
Code Highlights
Extracting Salary Information:
python
Copy code
df['Salary Estimate'] = df['Salary Estimate'].str.replace(r'[^\d\-]', '', regex=True)
df['Average Salary'] = df['Salary Estimate'].apply(
    lambda x: (int(x.split('-')[0]) + int(x.split('-')[1])) // 2 if '-' in x else int(x)
)
df[['Min Salary', 'Max Salary']] = df['Salary Estimate'].str.split('-', expand=True)
Extracting Key Skills:
python
Copy code
def extract_keywords(description):
    keywords = ['Python', 'SQL', 'Machine Learning', 'Data Analysis', 'Tableau', 'Excel', 'Power BI']
    found = [kw for kw in keywords if isinstance(description, str) and kw in description]
    return ", ".join(found)

df['key_skills'] = df['Job Description'].apply(extract_keywords)
Visualizing Salary Distribution:
python
Copy code
plt.figure(figsize=(10, 6))
sns.histplot(df['Average Salary'], kde=True, color="skyblue", bins=20)
plt.title('Salary Distribution')
plt.xlabel('Average Salary')
plt.ylabel('Frequency')
plt.show()
Sample Visualizations
Salary Distribution:

Top States by Job Count:

Insights
High-Demand Skills:

Python and SQL are the most frequently required skills.
Machine Learning and Tableau are also in demand.
Salary Trends:

States like California and New York offer higher average salaries.
Most jobs fall in the "Mid" salary range.
Job Distribution:

California, Texas, and New York have the highest job counts.
Remote work is still prevalent but was excluded for focused analysis.
How to Run the Project
Clone the repository:
bash
Copy code
git clone https://github.com/yourusername/your-repo-name.git
Install dependencies:
bash
Copy code
pip install pandas matplotlib seaborn numpy
Run the analysis:
Open the analysis.ipynb file in Jupyter Notebook or any IDE supporting Python notebooks.
Execute the cells step-by-step to replicate the analysis.

Future Enhancements
Include predictions for job demand using machine learning.
Expand the analysis to other industries.
Create interactive dashboards for visual exploration.
Contributing
Feel free to fork this project, submit pull requests, or report issues. Collaboration is welcome! 😊

