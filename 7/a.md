import pandas as pd

# Load the dataset
df = pd.read_csv("Walmart.csv")

# Use Store 1 data (single store time-series)
df = df[df["Store"] == 1]

# Convert Date column into datetime format (DD-MM-YYYY)
df["Date"] = pd.to_datetime(df["Date"], format="%d-%m-%Y")

# Set Date as index
df.set_index("Date", inplace=True)

# Down-Sampling (Weekly to Monthly)
monthly_data = df.resample("ME").sum(numeric_only=True)

print("Monthly Summary")
print(monthly_data)

<img width="717" height="253" alt="Screenshot 2026-09-07 200311" src="https://github.com/user-attachments/assets/a297f5f1-5a0d-41c8-aba7-929a2af99275" />
