import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle

# Define the stages and details for each stage
stages = [
    {"title": "Identification", "details": [
        "Records identified through database searching (n = 450)",
        "Additional records identified through other sources (n = 50)"]},
    {"title": "Screening", "details": [
        "Records after duplicates removed (n = 400)",
        "Records screened (n = 400)",
        "Records excluded (n = 250)"]},
    {"title": "Eligibility", "details": [
        "Full-text articles assessed for eligibility (n = 150)",
        "Full-text articles excluded (n = 100)"]},
    {"title": "Included", "details": [
        "Studies included in qualitative synthesis (n = 50)",
        "Studies included in quantitative synthesis (meta-analysis) (n = 50)"]}
]

# Plotting setup
fig, ax = plt.subplots(figsize=(10, 8))
ax.axis('off')

# Draw the flowchart
y_start = 1.0
box_height = 0.1
gap = 0.05

for stage in stages:
    # Draw stage title box
    ax.add_patch(Rectangle((0.1, y_start), 0.8, box_height, edgecolor='black', facecolor='lightgray'))
    ax.text(0.5, y_start + box_height / 2, stage["title"], horizontalalignment='center', verticalalignment='center', fontsize=12, fontweight='bold')
    
    # Draw details for each stage
    y_text = y_start - gap
    for detail in stage["details"]:
        ax.text(0.2, y_text, detail, verticalalignment='top', fontsize=10)
        y_text -= (gap + box_height / 2)
    
    # Update y_start for the next stage
    y_start = y_text - (gap * 2)

plt.show()
