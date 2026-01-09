import os
import pandas as pd
import matplotlib.pyplot as plt

# Ensure CSV exists; if not, create a small sample dataset for demo/running
CSV_PATH = "StudentsPerformance.csv"
if not os.path.exists(CSV_PATH):
	print(f"Warning: '{CSV_PATH}' not found. Creating sample dataset for demo.")
	sample = pd.DataFrame({
		'math score': [78, 85, 62, 90, 55],
		'reading score': [72, 88, 70, 95, 60],
		'writing score': [70, 80, 68, 92, 58]
	})
	sample.to_csv(CSV_PATH, index=False)
	data = sample
else:
	data = pd.read_csv(CSV_PATH)

subjects = ['math score', 'reading score', 'writing score']

average_marks = data[subjects].mean()
maximum_marks = data[subjects].max()
minimum_marks = data[subjects].min()

print("Average Marks:")
print(average_marks)

print("\nMaximum Marks:")
print(maximum_marks)

print("\nMinimum Marks:")
print(minimum_marks)

student_data = data[subjects].head(5)

student_data.plot(kind='bar')
plt.title("Marks Comparison of First 5 Students")
plt.xlabel("Student Index")
plt.ylabel("Marks")
plt.xticks(rotation=0)
plt.legend(["Math", "Reading", "Writing"])
plt.tight_layout()
plt.show()
