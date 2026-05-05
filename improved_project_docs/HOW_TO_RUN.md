# How to Run the Analysis

This guide provides step-by-step instructions on how to set up your environment and run the main analysis notebook (`SL_UQ_Analysis_V2_RealData.ipynb`).

## 1. Open your Terminal or Command Prompt
Navigate to the project directory where all the files are located.
```bash
cd /path/to/improved_project_docs
```

## 2. Set up a Virtual Environment (Recommended)
A virtual environment keeps your project dependencies isolated from the rest of your system. 

**For Linux/Mac:**
```bash
python3 -m venv venv
source venv/bin/activate
```

**For Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```
*(You should see `(venv)` appear at the beginning of your command prompt line.)*

## 3. Install the Required Packages
Now that your virtual environment is active, install all the exact library versions needed to run the project. We use the `requirements.txt` file for this.
```bash
pip install -r requirements.txt
```

## 4. Launch Jupyter Notebook
Once the installation finishes, you can start Jupyter to view the notebook:
```bash
jupyter notebook
```
This will open a new tab in your web browser.

## 5. Open and Run the Notebook
1. In the browser tab that opens, click on `SL_UQ_Analysis_V2_RealData.ipynb`.
2. Once the notebook opens, you can read through the cells.
3. To execute the code, you can run it cell-by-cell by clicking the **"Run"** button (or pressing `Shift + Enter`).
4. To run everything at once, click **"Kernel" -> "Restart & Run All"** in the top menu.

## 6. What to Expect
- **Data Download:** The first few code cells will connect to the NASA POWER API and download 22 years of historical solar and wind data for the 5 locations in Sierra Leone. This may take a minute or two.
- **Figures:** As you run the cells, the graphs and plots will be generated inside the notebook and also saved as high-quality PNG images into the `figures/` folder.
- **Deactivation:** When you are completely finished, you can stop the Jupyter server (press `Ctrl + C` in the terminal) and type `deactivate` to exit your virtual environment.
