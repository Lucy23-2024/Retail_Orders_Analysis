# Retail_Orders_Analysis

## 1. Environment Setup
1.1. Library Installation: Write the terminal commands to install the following Python packages: kaggle, sqlalchemy, and pymysql.

##### Library Installation

Install the required Python libraries using `pip`:

- `kaggle`: Access datasets via the Kaggle API.
- `python-dotenv`: Load environment variables from a `.env` file.
- `pandas`: Data manipulation and analysis.
- `sqlalchemy`: ORM for interacting with relational databases.
- `psycopg2-binary`: PostgreSQL driver compatible with SQLAlchemy.

Use the following commands:

!pip install kaggle           # For downloading datasets from Kaggle
!pip install python-dotenv    # For loading environment variables
!pip install pandas           # For data manipulation
!pip install sqlalchemy       # For database interactions
!pip install psycopg2-binary  # PostgreSQL connector for SQLAlchemy

1.2. Environment Variables: Describe how you would store and retrieve KAGGLE_USERNAME and KAGGLE_KEY securely using a .env file and the python-dotenv package.

Storing sensitive information like API keys in your code is risky because it can be accidentally shared or exposed. Instead, we use environment variables stored in a separate file (.env) that’s not included in version control. The python-dotenv package helps load these variables securely into our Python program.

Step 1: Create a .env File
In your project folder, create a file named .env.

Add your Kaggle credentials

Step 2: Use python-dotenv to Load These Variables in Python

##### Load Kaggle API Credentials Securely

This block loads Kaggle API credentials from a `.env` file and sets them as environment variables.

- `from dotenv import load_dotenv` allows secure loading of environment variables from a `.env` file (which should not be shared or committed).
- `load_dotenv()` loads the variables defined in `.env` into the environment.
- `os.environ['KAGGLE_USERNAME']` and `os.environ['KAGGLE_KEY']` are explicitly set using `os.getenv()` to ensure they're available for use by the Kaggle API.

This approach keeps credentials secure and out of the main script.

##### Download Dataset from Kaggle

The command `!kaggle datasets download -d ankitbansal06/retail-orders` uses the Kaggle CLI to download the **Retail Orders** dataset.

- The `!` at the beginning tells the notebook to execute a shell command.
- The `-d` flag specifies the dataset identifier on Kaggle (`ankitbansal06/retail-orders`).
- The downloaded file is typically a `.zip` and will need to be extracted before use.

Make sure Kaggle API credentials are correctly set in your environment (`KAGGLE_USERNAME` and `KAGGLE_KEY`) before running this command.

##### Extract the Downloaded Dataset

This step extracts the contents of the `retail-orders.zip` file into a folder named `orders`.

- `import zipfile` brings in Python’s built-in module for handling ZIP archives.
- `ZipFile(..., 'r')` opens the ZIP file in read mode.
- `extractall('orders')` extracts all files into the `orders` directory.

This makes the dataset accessible for reading with pandas or other tools.

## 2. Data Loading and Inspection

2.1. Read CSV: Write Python code to read orders.csv into a pandas DataFrame and display the first 30 rows.

##### Load and Preview the Dataset

We import the `pandas` library and load the `orders.csv` file into a DataFrame named `retail` using `pd.read_csv()`.  
Then, `retail.head(30)` is used to preview the first 30 rows of the dataset to understand the structure and content of the data.

2.2. Shape & Missing Values: In Python, how would you check the DataFrame's shape and count of missing values per column?

- Checking DataFrame shape

`retail.shape` returns a tuple representing the structure of the DataFrame:
It returns a tuple `(rows, columns)` indicating the number of records and features in the DataFrame.

This step is useful for getting a quick overview of the dataset’s size and structure

- Checking missing values

This step uses `retail.isnull().sum()` to identify missing `(null)` values in each column of the retail DataFrame.
`isnull()` returns a DataFrame of Boolean values (True where data is missing).
`sum()` aggregates the True values column-wise, giving a count of missing entries per column.

This helps assess data quality and determine whether any cleaning (e.g., imputation or removal) is needed.

## 3. Data Cleaning and Transformation

##### Check Data Types of Each Column

The command `retail.dtypes` displays the data type of each column in the `retail` DataFrame.

- It helps to understand what kind of data each column holds (e.g., integer, float, object/string).
- This information is important for data cleaning and analysis because some operations depend on the data type.

4.1. Categorical Exploration: Write a loop that prints the unique values for each object-type column (excluding Order Date).

### Inspect Unique Values in Categorical Columns

This block inspects unique values for all columns in the `retail` DataFrame that have the data type `object` (typically categorical or text data), **except** the `'Order Date'` column.

- `retail.select_dtypes(include='object')` selects all columns with data type `object`.
- For each of these columns (excluding `'Order Date'`), it prints:
  - The column name.
  - All unique values present in that column.
- This helps understand the variety and range of categorical data, identify typos, inconsistencies, or special categories, which is useful for data cleaning and analysis.

