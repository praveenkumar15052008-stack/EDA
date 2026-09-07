import pandas as pd

# Load the dataset
df = pd.read_csv("Walmart.csv")

# Use Store 1 data (single store time-series)
df = df[df["Store"] == 1]

# Convert Date column into datetime format
df["Date"] = pd.to_datetime(df["Date"], dayfirst=True)

# Set Date column as index
df.set_index("Date", inplace=True)

# Down-Sampling (Weekly to Monthly)
monthly_data = df.resample("ME").mean(numeric_only=True)

# Up-Sampling (Monthly to Daily)
daily_data = monthly_data.resample("D").ffill()

# Display the result
print("Up-Sampled Daily Data")
print(daily_data.head(15))

<img width="710" height="246" alt="Screenshot 2026-09-07 200446" src="https://github.com/user-attachments/assets/ce5f10a8-5f5d-4247-a355-d37dff902e47" />
