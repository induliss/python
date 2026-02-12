# University KPI calculation (simplified)
from dataclasses import dataclass
from typing import List

@dataclass
class KPI:
    name: str
    value: float
    target: float
    weight: float

kpi_names = ["Graduation rate", "Publications per staff", "International students"]
values = [78, 1.9, 11]
targets = [85, 2.5, 15]
weights = [0.4, 0.35, 0.25]

total_score = 0
total_weight = 0

for i in range(len(values)):
    ratio = values[i] / targets[i]

    if ratio >= 1:
        score = 1
    elif ratio >= 0.7:
        score = ratio
    else:
        score = ratio * 0.8

    total_score += score * weights[i]
    total_weight += weights[i]

overall_kpi = total_score / total_weight

if overall_kpi >= 0.85:
    level = "Excellent"
elif overall_kpi >= 0.70:
    level = "Good"
else:
    level = "Needs improvement"

print("Overall KPI:", round(overall_kpi, 3))
print("Performance level:", level)
