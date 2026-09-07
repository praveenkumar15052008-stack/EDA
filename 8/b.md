import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("Rolling_Dataset.csv")

# Convert Date column
df["Date"] = pd.to_datetime(df["Date"], dayfirst=True)

# Set index
df.set_index("Date", inplace=True)

# Rolling Mean
df["Rolling_Mean"] = df["Sales"].rolling(window=7).mean()

# Plot
plt.figure(figsize=(10, 5))
plt.plot(df.index, df["Sales"], label="Original Sales")
plt.plot(df.index, df["Rolling_Mean"], linewidth=3, label="7-Day Rolling Mean")
plt.title("Sales vs 7-Day Rolling Mean")
plt.xlabel("Date")
plt.ylabel("Sales")
plt.legend()
plt.show()

<img width="725" height="297" alt="Screenshot 2026-09-07 201256" src="https://github.com/user-attachments/assets/2bc9e1b3-19d3-489e-9c90-512d5120b26b" />
