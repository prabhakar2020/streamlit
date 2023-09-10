# Streamlit reference
## What is Streamlit
Streamlit is an open-source Python library for creating web applications quickly and easily, especially for data science and machine learning projects. It simplifies web app development with its intuitive Python API, interactive widgets, and real-time updates.

## Why Streamlit
Streamlit is chosen for its simplicity and speed in creating interactive web applications for data science and machine learning projects, making it a popular choice among data professionals.

## Read CSV file content file uploading a file
```Python
import streamlit as st
import pandas as pd
def main():
    st.title("CSV File Read with Streamlit")
    uploaded_csv_file = st.file_uploader("Choose a required CSV file", type=["csv"])
    if uploaded_csv_file is not None:
        # Read the uploaded CSV file into a DataFrame.
        df = pd.read_csv(uploaded_csv_file)
        # Display the DataFrame in the Streamlit app
        st.write("Displaying the contents of the uploaded CSV file in the browser:")
        st.write(df)
if __name__ == "__main__":
    main()

```
![image](https://github.com/prabhakar2020/streamlit/assets/7165155/ae4aef5f-4882-4653-bad7-ba5149f8213c)

## Read CSV file content file specified a file in program
```Python
import streamlit as st
import pandas as pd
def main():
    st.title("CSV File Viewer")
    # Specify the CSV file 
    csv_file_path = "customers_list.csv"
    try:
        # Read the CSV file into a DataFrame
        df = pd.read_csv(csv_file_path)
        show_csv_data = st.checkbox("Show raw data")
        if show_csv_data:
            st.write("Raw data:", df)
  
        # Allow users to select specific rows & columns to render
        st.sidebar.header("Customize Display")
        selected_rows = st.sidebar.multiselect("Select Rows", df.index.tolist())
        selected_columns = st.sidebar.multiselect("Select Columns", df.columns.tolist())

        # Filter the DataFrame results based selection
        filtered_df = df.loc[selected_rows, selected_columns]
        # Render the filtered DataFrame result on browser
        st.write("Filtered Data:", filtered_df)
    except FileNotFoundError:
        st.error("File not found. Specified file path is not found")

if __name__ == "__main__":
    main()

```
![image](https://github.com/prabhakar2020/streamlit/assets/7165155/2065d633-2680-4a86-8117-d6db13da9d45)

