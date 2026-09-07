import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("Rolling_Dataset.csv")

# Convert Date column
df["Date"] = pd.to_datetime(df["Date"], dayfirst=True)

# Set index
df.set_index("Date", inplace=True)

# Rolling Standard Deviation
df["Rolling_SD"] = df["Sales"].rolling(window=7).std()

# Plot
plt.figure(figsize=(10, 5))
plt.plot(df.index, df["Rolling_SD"], linewidth=3)
plt.title("7-Day Rolling Standard Deviation")
plt.xlabel("Date")
plt.ylabel("Standard Deviation")
plt.show()

<img width="656" height="303" alt="Screenshot 2026-09-07 202147" src="https://github.com/user-attachments/assets/aea4130c-bb65-4799-97a9-842a34822ec1" />
