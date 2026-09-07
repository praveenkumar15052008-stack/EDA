import pandas as pd

# Load dataset
df = pd.read_csv("Rolling_Dataset.csv")

# Convert Date column into datetime format
df["Date"] = pd.to_datetime(df["Date"], dayfirst=True)

# Set Date as index
df.set_index("Date", inplace=True)

# Calculate Rolling Mean
df["Rolling_Mean"] = df["Sales"].rolling(window=7).mean()

# Calculate Rolling Standard Deviation
df["Rolling_SD"] = df["Sales"].rolling(window=7).std()

# Display result
print(df[["Sales", "Rolling_Mean", "Rolling_SD"]])

<img width="314" height="433" alt="Screenshot 2026-09-07 200841" src="https://github.com/user-attachments/assets/5768d3d2-9736-48ff-ac20-11144b9081c4" />
