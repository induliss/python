from dataclasses import dataclass
from typing import List

class KPI:
    name: str
    value: float
    target: float
    weight: float

KPI_name = ["Graduation rate", "Publications per staff", "International students"]
value = list(78, 85, 0.4)
target = list(82, 90, 0.3)
weight = list(0.2, 0.4, 0.1)

kpi_data = []

n = int(input("Number of KPIs: "))

for i in range(n):
    name = input("KPI name: ")
    value = float(input("Value: "))
    target = float(input("Target: "))
    weight = float(input("Weight: "))
    kpi_data.append([name, value, target, weight])

total_score = 0
total_weight = 0

for i in range(len(value)):
    ratio = value[i] / target[i]

    if ratio >= 1:
        score = 1
    elif ratio >= 0.7:
        score = ratio
    else:
        score = ratio * 0.8

    total_score += score * weight[i]
    total_weight += weight[i]

overall_kpi = total_score / total_weight

if overall_kpi >= 0.85:
    level = "Excellent"
elif overall_kpi >= 0.70:
    level = "Good"
else:
    level = "Needs improvement"

print("Overall KPI:", round(overall_kpi, 3))
print("Performance level:", level)
