# Marble_XAL_Dr.Mutlu_Zeybek

Pseudo-code for Counterfactual Search
python
def find_counterfactual(model, x_current, target_reduction, feature_bounds):
    """
    Find minimal changes to achieve target energy reduction.
    
    Args:
        model: Trained XGBoost model
        x_current: Current feature vector (descending_speed, wire_speed, UCS, etc.)
        target_reduction: Desired percentage reduction (e.g., 0.20 for 20%)
        feature_bounds: Dict of (min, max) for controllable features
    
    Returns:
        counterfactual: Recommended feature changes
    """
    y_current = model.predict(x_current)
    y_target = y_current * (1 - target_reduction)
    
    # DiCE optimization
    cf = dice_generator.generate_counterfactuals(
        x_current, 
        total_CFs=3,
        desired_class=y_target,
        features_to_vary=['descending_speed', 'wire_speed']
    )
    return cf

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

import matplotlib.pyplot as plt
import matplotlib.patches as patches
from matplotlib.path import Path


def create_prisma_flow_diagram():
    """Create a PRISMA 2020 flow diagram for systematic review"""

    fig, ax = plt.subplots(1, 1, figsize=(10, 12))
    ax.set_xlim(0, 10)
    ax.set_ylim(0, 14)
    ax.axis("off")

    # Box styling
    box_style = dict(
        boxstyle="round,pad=0.3", facecolor="white", edgecolor="black", linewidth=1.5
    )
    arrow_style = dict(arrowstyle="->", color="black", lw=1.5)

    # ===== IDENTIFICATION =====
    # Title
    ax.text(
        5,
        13.5,
        "IDENTIFICATION",
        ha="center",
        fontsize=11,
        fontweight="bold",
        bbox=dict(boxstyle="round", facecolor="#E8F4F8", edgecolor="#333"),
    )

    # Box 1: Records identified
    ax.text(
        5,
        12.2,
        "Records identified from databases (n = 287)\n• Web of Science (n = 89)\n• Scopus (n = 94)\n• Google Scholar (n = 62)\n• ScienceDirect (n = 42)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=box_style,
    )

    # Box 2: Records after duplicates
    ax.text(
        5,
        10.5,
        "Records after duplicate removal (n = 211)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=box_style,
    )

    # Arrow 1→2
    ax.annotate("", xy=(5, 11.1), xytext=(5, 11.7), arrowprops=arrow_style)

    # ===== SCREENING =====
    # Title
    ax.text(
        5,
        9.8,
        "SCREENING",
        ha="center",
        fontsize=11,
        fontweight="bold",
        bbox=dict(boxstyle="round", facecolor="#FFF4E6", edgecolor="#333"),
    )

    # Box 3: Records screened
    ax.text(
        5,
        8.5,
        "Records screened (n = 211)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=box_style,
    )

    # Box 4: Records excluded
    ax.text(
        5,
        7.0,
        "Records excluded (n = 122)\n• Not marble processing (n = 64)\n• Non-English (n = 23)\n• Conference abstracts only (n = 18)\n• Duplicates missed (n = 17)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=dict(
            boxstyle="round", facecolor="#FFE6E6", edgecolor="black", linewidth=1.5
        ),
    )

    # Arrow 3→4
    ax.annotate("", xy=(5, 7.6), xytext=(5, 8.1), arrowprops=arrow_style)

    # Box 5: Reports sought
    ax.text(
        5,
        5.5,
        "Reports sought for retrieval (n = 89)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=box_style,
    )

    # Arrow 3→5 (continue screening)
    ax.annotate("", xy=(5, 5.8), xytext=(5, 6.3), arrowprops=arrow_style)

    # Box 6: Reports not retrieved
    ax.text(
        10.5,
        5.5,
        "Reports not retrieved (n = 0)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=dict(
            boxstyle="round", facecolor="#FFE6E6", edgecolor="black", linewidth=1.5
        ),
    )

    # Arrow 5→6
    ax.annotate("", xy=(10.5, 5.5), xytext=(7, 5.5), arrowprops=arrow_style)

    # ===== ELIGIBILITY =====
    # Title
    ax.text(
        5,
        4.8,
        "ELIGIBILITY",
        ha="center",
        fontsize=11,
        fontweight="bold",
        bbox=dict(boxstyle="round", facecolor="#E6FFE6", edgecolor="#333"),
    )

    # Box 7: Reports assessed
    ax.text(
        5,
        3.5,
        "Reports assessed for eligibility (n = 89)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=box_style,
    )

    # Arrow
    ax.annotate("", xy=(5, 4.1), xytext=(5, 4.5), arrowprops=arrow_style)

    # Box 8: Reports excluded (with reasons)
    ax.text(
        10.5,
        2.2,
        "Reports excluded (n = 45)\n• No ML/AI component (n = 21)\n• No quantitative parameters (n = 12)\n• Duplicate publication (n = 7)\n• Full text unavailable (n = 5)",
        ha="center",
        va="center",
        fontsize=9,
        bbox=dict(
            boxstyle="round", facecolor="#FFE6E6", edgecolor="black", linewidth=1.5
        ),
    )

    # Arrow 7→8
    ax.annotate("", xy=(10.5, 2.8), xytext=(5.5, 3.3), arrowprops=arrow_style)

    # ===== INCLUDED =====
    # Title
    ax.text(
        5,
        2.8,
        "INCLUDED",
        ha="center",
        fontsize=11,
        fontweight="bold",
        bbox=dict(boxstyle="round", facecolor="#E6E6FF", edgecolor="#333"),
    )

    # Box 9: Total included
    ax.text(
        5,
        0.5,
        "Total studies included in review (n = 44)\n\nCore marble processing studies: 32\nContextual/methodological studies: 12",
        ha="center",
        va="center",
        fontsize=10,
        bbox=dict(
            boxstyle="round", facecolor="#D4F1F9", edgecolor="black", linewidth=2
        ),
    )

    # Arrow 7→9
    ax.annotate("", xy=(5, 1.1), xytext=(5, 2.5), arrowprops=arrow_style)

    plt.tight_layout()
    plt.savefig("prisma_flow_diagram.png", dpi=300, bbox_inches="tight")
    plt.show()

    print("✓ PRISMA flow diagram saved as 'prisma_flow_diagram.png'")


# Run the function
create_prisma_flow_diagram()

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX


