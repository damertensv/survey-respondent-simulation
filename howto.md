# How-To Guide: GSS Respondent Simulation

This guide provides instructions on how to set up the environment, run the survey respondent simulation, and visualize the results.

### 1. Install Dependencies

To ensure all required packages are installed, create a Conda environment from the provided `env.yml` file.

1.  Open a terminal or Anaconda Prompt.
2.  Navigate to the project directory.
3.  Run the following command to create the environment:
    ```bash
    conda env create -f env.yml
    ```
4.  Activate the new environment:
    ```bash
    conda activate itf
    ```
    You will need to have this environment active to run the notebooks. In VS Code, select this environment as the kernel for the Jupyter notebooks.

Though less preferred (and untested), if you do not have Conda installed, you may use Pip.

```bash
pip install -r requirements.txt
```

### 2. Run the Simulation

The `itf_gss_run.ipynb` notebook runs the simulation by generating personas from the GSS dataset and using a generative model to predict their answers to survey questions.

1.  Open `itf_gss_run.ipynb` in VS Code.
2.  Ensure the `itf` conda environment is selected as the notebook kernel.
3.  Run all cells in the notebook. You can do this by clicking the "Run All" button at the top of the notebook. This process may take a significant amount of time depending on the parameters set.

### 3. Configure Simulation Parameters

Before running the simulation, you can adjust the parameters in the third cell of `itf_gss_run.ipynb`.

*   `num_people`: The number of respondents to sample from the GSS dataset for the simulation.
*   `num_workers`: The number of parallel threads to use for generating responses. A higher number will run faster but consume more resources.

For example:
```python
num_people = 2
num_workers = 4
```

### 4. Visualize the Results

After the simulation notebook (`itf_gss_run.ipynb`) completes, it saves the results to files. You can then use `itf_gss_viz.ipynb` to analyze and visualize the performance.

1.  Open `itf_gss_viz.ipynb` in VS Code.
2.  In the third cell, set the `num_people` variable to match the value you used in `itf_gss_run.ipynb`. This ensures the correct result files are loaded.
    ```python
    num_people = 10
    ```
3.  Run all cells in the notebook to view the analysis. The notebook provides interactive widgets to inspect individual variable performance and summary tables comparing the predicted responses to the actual GSS data.

### Sidenote on Future Enhancements

The visualizations will be enhanced to better align with the methodology from the original paper. Specifically, for nominal categorical variables, we will calculate accuracy based on one-hot encoded representations rather than single-label accuracy. This change will be implemented in the `itf_gss_viz.ipynb` notebook and will **not** require re-running the simulation.