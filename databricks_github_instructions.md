# Running ClimateInsight Singapore on Databricks with GitHub Integration

This guide provides step-by-step instructions for executing the ClimateInsight Singapore project on the Databricks platform and integrating it with GitHub for version control and collaboration.

## Table of Contents
1. [Setting Up Databricks Environment](#setting-up-databricks-environment)
2. [GitHub Integration](#github-integration)
3. [Importing and Running Notebooks](#importing-and-running-notebooks)
4. [Creating Dashboards](#creating-dashboards)
5. [Setting Up Genie Spaces](#setting-up-genie-spaces)
6. [Deploying the Solution](#deploying-the-solution)
7. [Troubleshooting](#troubleshooting)

## Setting Up Databricks Environment

### 1. Create a Databricks Account

If you don't already have a Databricks account:

1. Go to [Databricks](https://databricks.com/) and sign up for a free trial or use your organization's account
2. Choose the appropriate cloud provider (AWS, Azure, or Google Cloud)
3. Complete the registration process

### 2. Create a Workspace

1. Log in to your Databricks account
2. Create a new workspace:
   - For AWS: Navigate to "Workspaces" and click "Create Workspace"
   - For Azure: Use Azure Portal to create a Databricks workspace
   - For Google Cloud: Use Google Cloud Console to create a Databricks workspace
3. Name your workspace (e.g., "ClimateInsight-Singapore")
4. Select the appropriate region (preferably one close to your location)
5. Choose other settings based on your requirements
6. Create the workspace

### 3. Set Up a Cluster

1. In your Databricks workspace, click on "Compute" in the left sidebar
2. Click "Create Cluster"
3. Configure your cluster:
   - **Cluster Name**: ClimateInsight-Cluster
   - **Cluster Mode**: Single Node or Standard (based on your needs)
   - **Databricks Runtime Version**: Select the latest runtime with ML (e.g., 13.3 ML)
   - **Node Type**: Select an appropriate instance type (e.g., Standard_DS3_v2 on Azure)
   - **Autoscaling**: Enable if needed
   - **Auto-termination**: Enable and set to 120 minutes (recommended)
4. Click "Create Cluster"
5. Wait for the cluster to start (this may take a few minutes)

### 4. Create Storage Directories

1. In your Databricks workspace, click on "Data" in the left sidebar
2. Click on "DBFS" to access the Databricks File System
3. Create the following directory structure:
   - `/FileStore/climate_resilience/datasets`
   - `/FileStore/climate_resilience/processed`
   - `/FileStore/climate_resilience/analytics`
   - `/FileStore/climate_resilience/visualization`
   - `/FileStore/climate_resilience/genie_spaces`

You can create these directories using the Databricks UI or by running the following code in a notebook:

```python
dbutils.fs.mkdirs("/FileStore/climate_resilience/datasets")
dbutils.fs.mkdirs("/FileStore/climate_resilience/processed")
dbutils.fs.mkdirs("/FileStore/climate_resilience/analytics")
dbutils.fs.mkdirs("/FileStore/climate_resilience/visualization")
dbutils.fs.mkdirs("/FileStore/climate_resilience/genie_spaces")
```

## GitHub Integration

### 1. Create a GitHub Repository

1. Log in to your GitHub account
2. Click on the "+" icon in the top-right corner and select "New repository"
3. Name your repository (e.g., "climate-insight-singapore")
4. Add a description: "AI/BI solution for climate change resilience in Singapore"
5. Choose "Public" visibility
6. Initialize with a README file
7. Add a .gitignore file for Python
8. Choose an open-source license (e.g., MIT License)
9. Click "Create repository"

### 2. Upload Project Files to GitHub

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/your-username/climate-insight-singapore.git
   cd climate-insight-singapore
   ```

2. Create a directory structure in your local repository:
   ```bash
   mkdir -p notebooks data docs images
   ```

3. Copy the notebook files to the notebooks directory
4. Add a README.md file with project information
5. Commit and push the changes:
   ```bash
   git add .
   git commit -m "Initial commit with project structure and notebooks"
   git push origin main
   ```

### 3. Connect Databricks to GitHub

1. In your Databricks workspace, click on "Repos" in the left sidebar
2. Click "Add Repo"
3. Select "Git repository"
4. Enter your GitHub repository URL (e.g., https://github.com/your-username/climate-insight-singapore.git)
5. Click "Create"

This will clone your GitHub repository to your Databricks workspace, allowing you to work with the notebooks directly in Databricks while maintaining version control.

## Importing and Running Notebooks

### 1. Access the Notebooks

If you've connected your GitHub repository to Databricks:
1. Navigate to "Repos" in the left sidebar
2. Open your repository
3. Navigate to the "notebooks" directory
4. The notebooks should be visible and ready to use

Alternatively, you can import the notebooks manually:
1. Click on "Workspace" in the left sidebar
2. Navigate to your desired location
3. Click the dropdown arrow next to your username or workspace name
4. Select "Import"
5. Upload each notebook file (.ipynb)

### 2. Attach Notebooks to Cluster

Before running any notebook:
1. Open the notebook
2. Click on the "Detached" dropdown at the top
3. Select your cluster ("ClimateInsight-Cluster")
4. Wait for the notebook to connect to the cluster

### 3. Run the Notebooks in Sequence

Execute the notebooks in the following order:

1. **01_climate_data_ingestion.ipynb**
   - This notebook downloads and prepares the climate data
   - Make sure to check the output paths match your DBFS structure

2. **02_climate_data_processing.ipynb**
   - This notebook cleans and transforms the data
   - Verify that it can access the data from the previous step

3. **03_climate_analytics.ipynb**
   - This notebook performs trend analysis, correlation studies, and predictive modeling
   - Check that visualizations are generated correctly

4. **04_climate_visualization.ipynb**
   - This notebook creates various visualizations for dashboards
   - Ensure all HTML files are saved to the visualization directory

5. **05_genie_integration.ipynb**
   - This notebook sets up the Genie Spaces integration
   - Verify that the knowledge base and interface are created successfully

You can run each notebook by:
- Clicking "Run All" at the top to execute all cells
- Or running cells individually by clicking the play button next to each cell

### 4. Monitor Execution

1. Check the execution status of each cell (indicated by a number in brackets when complete)
2. Review any error messages and fix issues as needed
3. Verify that output files are created in the expected locations

## Creating Dashboards

### 1. Set Up AI/BI Dashboard

1. In your Databricks workspace, click on "SQL" in the left sidebar
2. Click "Create" and select "Dashboard"
3. Name your dashboard (e.g., "Climate Resilience Executive Dashboard")
4. Click "Create"

### 2. Add Visualizations to Dashboard

1. Click "Add" and select "Visualization"
2. Choose "Upload HTML"
3. Navigate to the visualization files created by the notebooks:
   - For executive dashboard: Upload files from `/FileStore/climate_resilience/visualization/executive_*.html`
   - For trend dashboard: Upload files from `/FileStore/climate_resilience/visualization/*_trend*.html`
   - For predictive dashboard: Upload files from `/FileStore/climate_resilience/visualization/*_prediction*.html`
   - For vulnerability dashboard: Upload files from `/FileStore/climate_resilience/visualization/vulnerability_*.html`
4. Arrange the visualizations on the dashboard by dragging and resizing
5. Click "Save" to update the dashboard

### 3. Create Multiple Dashboards

Repeat the process to create separate dashboards for:
- Executive Summary
- Trend Analysis
- Predictive Analysis
- Vulnerability Assessment

## Setting Up Genie Spaces

### 1. Enable Genie Spaces

Note: Genie Spaces is a newer Databricks feature. If it's not available in your workspace, you can use the simulated interface created in the notebook.

1. In your Databricks workspace, check if Genie Spaces is available in the left sidebar
2. If available, click on "Genie Spaces"
3. Click "Create Space"
4. Name your space (e.g., "Climate Resilience Assistant")
5. Click "Create"

### 2. Configure Genie with Knowledge Base

1. In your Genie Space, click on "Settings" or "Configure"
2. Under "Knowledge Base", click "Add"
3. Select "Upload JSON"
4. Upload the knowledge base file created by the notebook: `/FileStore/climate_resilience/genie_spaces/knowledge_base.json`
5. Click "Save" or "Apply"

### 3. Test Genie Spaces

1. In your Genie Space, type a test query (e.g., "What is the current temperature in Singapore?")
2. Verify that Genie responds with information from your knowledge base
3. Try different types of queries to test the full functionality

If Genie Spaces is not available, you can use the simulated interface:
1. Navigate to `/FileStore/climate_resilience/genie_spaces/genie_interface.html`
2. Download this file
3. Open it in a web browser to interact with the simulated Genie interface

## Deploying the Solution

### 1. Schedule Notebook Runs

To keep your data and insights up-to-date:

1. In your Databricks workspace, click on "Workflows" in the left sidebar
2. Click "Create Job"
3. Configure your job:
   - **Name**: ClimateInsight-DataUpdate
   - **Task 1**: Select the data ingestion notebook
   - **Task 2**: Select the data processing notebook (dependent on Task 1)
   - **Task 3**: Select the analytics notebook (dependent on Task 2)
   - **Task 4**: Select the visualization notebook (dependent on Task 3)
   - **Task 5**: Select the Genie integration notebook (dependent on Task 4)
4. Set a schedule (e.g., monthly)
5. Click "Create"

### 2. Share Dashboards

To share your insights with stakeholders:

1. Open each dashboard
2. Click "Share" in the top-right corner
3. Enter email addresses of users or groups
4. Set appropriate permissions (View, Edit, Manage)
5. Click "Share"

### 3. Export for Presentation

For the hackathon submission:

1. Take screenshots of each dashboard for inclusion in your presentation
2. Record a demonstration video showing the dashboards and Genie interaction
3. Export any key visualizations as images for your presentation slides

## Troubleshooting

### Common Issues and Solutions

1. **Data Not Found**
   - Check that file paths match the DBFS structure
   - Verify that previous notebooks completed successfully
   - Check for permission issues on DBFS directories

2. **Cluster Connection Issues**
   - Ensure your cluster is running
   - Try detaching and reattaching the notebook to the cluster
   - Restart the cluster if necessary

3. **Package Import Errors**
   - Install missing packages using `%pip install package_name`
   - Restart the Python interpreter after installing packages

4. **Visualization Not Rendering**
   - Check that HTML files were created successfully
   - Verify file paths when uploading to dashboards
   - Try using a different browser if visualizations don't appear

5. **GitHub Integration Issues**
   - Ensure you have the correct repository URL
   - Check your GitHub credentials in Databricks
   - Try using a personal access token if password authentication fails

### Getting Help

- Databricks Documentation: [https://docs.databricks.com/](https://docs.databricks.com/)
- Databricks Community Forums: [https://community.databricks.com/](https://community.databricks.com/)
- GitHub Documentation: [https://docs.github.com/](https://docs.github.com/)

---

This guide provides a comprehensive walkthrough for setting up and running the ClimateInsight Singapore project on Databricks with GitHub integration. Follow these steps to successfully implement the solution and prepare your hackathon submission.
