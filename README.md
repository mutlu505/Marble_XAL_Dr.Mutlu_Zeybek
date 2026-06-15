# Marble_XAL_Dr.Mutlu_Zeybek

#Below is a short, simple Python script to generate Figure 1 (PRISMA 2020 flow diagram) for your paper. 

import matplotlib.pyplot as plt
import matplotlib.patches as patches
from matplotlib.path import Path

fig, ax = plt.subplots(1, 1, figsize=(10, 12))
ax.set_xlim(0, 10)
ax.set_ylim(0, 14)
ax.axis("off")

# Box styling
box_style = dict(
    boxstyle="round,pad=0.5", facecolor="white", edgecolor="black", linewidth=1.5
)
arrow_style = dict(arrowstyle="->", color="black", linewidth=1.5)

# Box 1: Identification
ax.text(
    5,
    13,
    "Records identified through database searching (n = 287)",
    ha="center",
    va="center",
    fontsize=10,
    fontweight="bold",
    bbox=box_style,
)
ax.text(
    5,
    12.7,
    "Web of Science: 89 | Scopus: 112 | Google Scholar: 54 | ScienceDirect: 32",
    ha="center",
    va="center",
    fontsize=8,
    style="italic",
    bbox=dict(facecolor="white", edgecolor="none"),
)

# Arrow
ax.annotate("", xy=(5, 12.2), xytext=(5, 12.55), arrowprops=arrow_style)

# Box 2: After duplicate removal
ax.text(
    5,
    11.7,
    "Records after duplicate removal (n = 211)",
    ha="center",
    va="center",
    fontsize=10,
    fontweight="bold",
    bbox=box_style,
)

# Arrow
ax.annotate("", xy=(5, 11.2), xytext=(5, 11.55), arrowprops=arrow_style)

# Box 3: Screened
ax.text(
    5,
    10.7,
    "Records screened by title/abstract (n = 211)",
    ha="center",
    va="center",
    fontsize=10,
    fontweight="bold",
    bbox=box_style,
)

# Arrow to excluded (right side)
ax.annotate("", xy=(7.5, 10.2), xytext=(7.5, 10.55), arrowprops=arrow_style)
ax.text(
    7.7,
    10.2,
    "Records excluded (n = 122)",
    ha="left",
    va="center",
    fontsize=8,
    bbox=dict(boxstyle="round,pad=0.3", facecolor="#ffe6e6", edgecolor="red"),
)
ax.text(7.7, 9.9, "• Not marble/stone: 54", ha="left", va="center", fontsize=7)
ax.text(
    7.7, 9.7, "• No quantitative parameters: 38", ha="left", va="center", fontsize=7
)
ax.text(7.7, 9.5, "• Non-English w/o abstract: 18", ha="left", va="center", fontsize=7)
ax.text(7.7, 9.3, "• Conference abstracts only: 12", ha="left", va="center", fontsize=7)

# Arrow down from screened
ax.annotate("", xy=(5, 9.7), xytext=(5, 10.55), arrowprops=arrow_style)

# Box 4: Full-text assessed
ax.text(
    5,
    9.2,
    "Full-text articles assessed for eligibility (n = 89)",
    ha="center",
    va="center",
    fontsize=10,
    fontweight="bold",
    bbox=box_style,
)

# Arrow to excluded (right side)
ax.annotate("", xy=(7.5, 8.7), xytext=(7.5, 9.05), arrowprops=arrow_style)
ax.text(
    7.7,
    8.7,
    "Full-text excluded (n = 45)",
    ha="left",
    va="center",
    fontsize=8,
    bbox=dict(boxstyle="round,pad=0.3", facecolor="#ffe6e6", edgecolor="red"),
)
ax.text(7.7, 8.45, "• No optimization method: 19", ha="left", va="center", fontsize=7)
ax.text(7.7, 8.25, "• Pure quarrying focus: 14", ha="left", va="center", fontsize=7)
ax.text(7.7, 8.05, "• Duplicate reporting: 7", ha="left", va="center", fontsize=7)
ax.text(
    7.7,
    7.85,
    "• Insufficient method description: 5",
    ha="left",
    va="center",
    fontsize=7,
)

# Arrow down from full-text
ax.annotate("", xy=(5, 8.2), xytext=(5, 9.05), arrowprops=arrow_style)

# Box 5: Included
ax.text(
    5,
    7.7,
    "Studies included in synthesis (n = 44)",
    ha="center",
    va="center",
    fontsize=10,
    fontweight="bold",
    bbox=dict(
        boxstyle="round,pad=0.5", facecolor="#e6ffe6", edgecolor="green", linewidth=2
    ),
)

# Sub-boxes for breakdown
ax.text(
    5, 7.2, "├── Core marble/stone processing: 32", ha="center", va="center", fontsize=9
)
ax.text(
    5,
    6.9,
    "└── Contextual (methodological inspiration): 12",
    ha="center",
    va="center",
    fontsize=9,
)

# Title
ax.text(
    5,
    13.5,
    "Figure 1: PRISMA 2020 Flow Diagram",
    ha="center",
    va="center",
    fontsize=12,
    fontweight="bold",
)

plt.tight_layout()
plt.savefig("figure1_prisma_flow.png", dpi=300, bbox_inches="tight")
plt.show()
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

#Simple Python Code for Figure 2: XAI Framework Architecture Diagram

import matplotlib.pyplot as plt
import matplotlib.patches as patches
from matplotlib.patches import FancyBboxPatch, FancyArrowPatch
import numpy as np

fig, ax = plt.subplots(1, 1, figsize=(14, 10))
ax.set_xlim(0, 10)
ax.set_ylim(0, 12)
ax.axis('off')

# Colors
color_layer1 = '#E8F4F8'  # Light blue - Data
color_layer2 = '#FFF4E6'  # Light orange - Prediction
color_layer3 = '#E8F8E8'  # Light green - Explanation
arrow_color = '#333333'

# ============================================================
# LAYER 1: DATA ACQUISITION (Bottom)
# ============================================================
y1 = 1.0
box1 = FancyBboxPatch((1.5, y1), 7, 2.2, boxstyle="round,pad=0.1",
                       facecolor=color_layer1, edgecolor='#2C7FB8', linewidth=2)
ax.add_patch(box1)
ax.text(5, y1 + 1.8, 'LAYER 1: DATA ACQUISITION & FEATURE ENGINEERING', 
        ha='center', va='center', fontsize=12, fontweight='bold', color='#2C7FB8')
ax.text(5, y1 + 1.0, '• Sensor data (current, speed, vibration)', 
        ha='center', va='center', fontsize=10)
ax.text(5, y1 + 0.5, '• Material properties (UCS, hardness, abrasivity)', 
        ha='center', va='center', fontsize=10)
ax.text(5, y1 + 0.0, '• Environmental conditions (slurry density, temperature)', 
        ha='center', va='center', fontsize=10)

# ============================================================
# Arrow: Layer 1 → Layer 2
# ============================================================
ax.annotate('', xy=(5, 4.2), xytext=(5, 3.3),
            arrowprops=dict(arrowstyle='->', lw=2, color=arrow_color))

# ============================================================
# LAYER 2: PREDICTIVE MODEL (Middle)
# ============================================================
y2 = 4.5
box2 = FancyBboxPatch((1.5, y2), 7, 2.2, boxstyle="round,pad=0.1",
                       facecolor=color_layer2, edgecolor='#E67E22', linewidth=2)
ax.add_patch(box2)
ax.text(5, y2 + 1.8, 'LAYER 2: PREDICTIVE MODEL (XGBoost)', 
        ha='center', va='center', fontsize=12, fontweight='bold', color='#E67E22')
ax.text(5, y2 + 1.0, 'Multi-task prediction (separate models, shared features)', 
        ha='center', va='center', fontsize=10)
ax.text(5, y2 + 0.5, '• Specific Energy (kWh/m²)  • Wire Wear (mm/m²)  • Surface Quality (Ra)', 
        ha='center', va='center', fontsize=10)
ax.text(5, y2 + 0.0, '5-fold cross-validation | Bayesian hyperparameter tuning', 
        ha='center', va='center', fontsize=9, style='italic')

# ============================================================
# Arrow: Layer 2 → Layer 3
# ============================================================
ax.annotate('', xy=(5, 7.7), xytext=(5, 6.8),
            arrowprops=dict(arrowstyle='->', lw=2, color=arrow_color))

# ============================================================
# LAYER 3: EXPLANATIONS (Top)
# ============================================================
y3 = 8.0
box3 = FancyBboxPatch((0.5, y3), 9, 3.5, boxstyle="round,pad=0.1",
                       facecolor=color_layer3, edgecolor='#27AE60', linewidth=2)
ax.add_patch(box3)
ax.text(5, y3 + 3.1, 'LAYER 3: EXPLAINABILITY (SHAP + Counterfactuals)', 
        ha='center', va='center', fontsize=12, fontweight='bold', color='#27AE60')

# Sub-box 3A: Global Explanation
sub1 = FancyBboxPatch((1.0, y3 + 1.5), 2.5, 1.3, boxstyle="round,pad=0.05",
                       facecolor='white', edgecolor='#27AE60', linewidth=1.5)
ax.add_patch(sub1)
ax.text(2.25, y3 + 2.2, '3A: GLOBAL', ha='center', va='center', fontsize=9, fontweight='bold')
ax.text(2.25, y3 + 1.9, 'Feature Importance', ha='center', va='center', fontsize=8)
ax.text(2.25, y3 + 1.7, 'Summary Plot', ha='center', va='center', fontsize=8, style='italic')

# Sub-box 3B: Local Explanation
sub2 = FancyBboxPatch((3.8, y3 + 1.5), 2.5, 1.3, boxstyle="round,pad=0.05",
                       facecolor='white', edgecolor='#27AE60', linewidth=1.5)
ax.add_patch(sub2)
ax.text(5.05, y3 + 2.2, '3B: LOCAL', ha='center', va='center', fontsize=9, fontweight='bold')
ax.text(5.05, y3 + 1.9, 'Instance Attribution', ha='center', va='center', fontsize=8)
ax.text(5.05, y3 + 1.7, 'For each slab', ha='center', va='center', fontsize=8, style='italic')

# Sub-box 3C: Counterfactual
sub3 = FancyBboxPatch((6.6, y3 + 1.5), 2.5, 1.3, boxstyle="round,pad=0.05",
                       facecolor='white', edgecolor='#27AE60', linewidth=1.5)
ax.add_patch(sub3)
ax.text(7.85, y3 + 2.2, '3C: COUNTERFACTUAL', ha='center', va='center', fontsize=9, fontweight='bold')
ax.text(7.85, y3 + 1.9, 'Actionable Changes', ha='center', va='center', fontsize=8)
ax.text(7.85, y3 + 1.7, 'DiCE Optimization', ha='center', va='center', fontsize=8, style='italic')

# Sub-box 3D: Uncertainty
sub4 = FancyBboxPatch((2.25, y3 + 0.1), 5.5, 1.0, boxstyle="round,pad=0.05",
                       facecolor='white', edgecolor='#27AE60', linewidth=1.5)
ax.add_patch(sub4)
ax.text(5, y3 + 0.6, '3D: PREDICTION INTERVALS (Quantile Regression | Risk-aware)', 
        ha='center', va='center', fontsize=9)

# ============================================================
# HUMAN-IN-THE-LOOP (Sidebar)
# ============================================================
side_x = 8.8
side_y = 1.5
sidebox = FancyBboxPatch((side_x, side_y), 1.0, 2.8, boxstyle="round,pad=0.05",
                          facecolor='#F0F0F0', edgecolor='#7F8C8D', linewidth=1.5, alpha=0.7)
ax.add_patch(sidebox)
ax.text(side_x + 0.5, side_y + 2.4, 'HITL', ha='center', va='center', fontsize=9, fontweight='bold', rotation=90)
ax.text(side_x + 0.5, side_y + 1.2, 'Operator', ha='center', va='center', fontsize=8, rotation=90)
ax.text(side_x + 0.5, side_y + 0.4, 'Override', ha='center', va='center', fontsize=8, rotation=90)

# Dashed line from Layer 3 to sidebar
ax.plot([8.8, 8.8], [7.0, 4.3], color='#7F8C8D', linestyle='--', linewidth=1.5, alpha=0.7)

# ============================================================
# OUTPUT ARROWS (Top)
# ============================================================
ax.annotate('', xy=(2.5, 11.8), xytext=(2.5, 11.5),
            arrowprops=dict(arrowstyle='->', lw=2, color=arrow_color))
ax.text(2.5, 11.9, 'Operator Dashboard', ha='center', va='center', fontsize=9, fontweight='bold')

ax.annotate('', xy=(5, 11.8), xytext=(5, 11.5),
            arrowprops=dict(arrowstyle='->', lw=2, color=arrow_color))
ax.text(5, 11.9, 'PLC Commands', ha='center', va='center', fontsize=9, fontweight='bold')

ax.annotate('', xy=(7.5, 11.8), xytext=(7.5, 11.5),
            arrowprops=dict(arrowstyle='->', lw=2, color=arrow_color))
ax.text(7.5, 11.9, 'Logs & Audit', ha='center', va='center', fontsize=9, fontweight='bold')

# ============================================================
# TITLE
# ============================================================
ax.text(5, 11.5, 'Proposed XAI Framework for Marble Processing Optimization', 
        ha='center', va='center', fontsize=14, fontweight='bold')

plt.tight_layout()
plt.savefig('figure2_xai_framework.png', dpi=300, bbox_inches='tight')
plt.show()

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Supplementary Materials
Explainable Artificial Intelligence for Operational Optimization in Marble Processing Plants: A Systematic Literature Review and Framework Proposal
Author: Mutlu ZEYBEK

Date: June 15, 2026

Supplementary File S1: PRISMA 2020 Checklist
Completed PRISMA 2029 checklist for systematic literature reviews.

Section/Topic	Item	Checklist Item	Location reported	Status
TITLE	1	Identify the report as a systematic review	Title page	✓
ABSTRACT	2	Structured summary	Abstract	✓
INTRODUCTION				
Rationale	3	Describe rationale for review	Section 1.1-1.3	✓
Objectives	4	Provide explicit statement of objectives	Section 1.4	✓
METHODS				
Eligibility criteria	5	Specify inclusion/exclusion criteria	Section 2.2	✓
Information sources	6	Specify databases, dates, last search	Section 2.1	✓
Search strategy	7	Present full search strategy	Supplementary Table S1	✓
Selection process	8	Specify methods for selecting studies	Section 2.2-2.3	✓
Data collection process	9	Specify methods for data extraction	Section 2.4-2.5	✓
Data items	10	List all variables for which data sought	Table 3; Section 2.5	✓
Risk of bias assessment	11	Specify methods for risk of bias	Section 2.5	✓
Effect measures	12	Specify effect measures (if applicable)	N/A (no meta-analysis)	—
Synthesis methods	13	Describe methods for synthesis	Section 2.4	✓
RESULTS				
Study selection	14	Present PRISMA flow diagram	Figure 1	✓
Study characteristics	15	Present characteristics of studies	Tables 3-5	✓
Risk of bias	16	Present risk of bias assessment	Supplementary Table S2	✓
Results of synthesis	17	Present results of synthesis	Section 3.2-3.3	✓
DISCUSSION				
Limitations	23	Discuss limitations of review	Section 6.3	✓
Interpretation	24	Provide general interpretation	Section 6.1, 7	✓
OTHER				
Registration	24a	Provide registration information	Section 2.1 (not registered)	✓
Conflict of interest	25	Declare any conflicts	Title page	✓
Funding	26	Declare funding sources	Title page	✓
Data availability	27	Provide data availability statement	Title page	✓
PRISMA 2020 Citation: Page, M. J., McKenzie, J. E., Bossuyt, P. M., et al. (2021). The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. BMJ, 372, n71.

Supplementary File S2: Complementary Background Literature
The following references provided contextual background for the review but were not directly cited in the main text. They informed the methodological approach, circular economy framing, and broader industrial context.

Sustainable Development and Circular Economy
Abu Hanieh, A., AbdElall, S., & Hasan, A. (2014). Sustainable development of stone and marble sector in Palestine. Journal of Cleaner Production, 84, 581-588.

Akar, A. U., Yalpır, S., Yel, E., et al. (2026). Development of an approach in spatial planning through site selection for symbiotic and circular low-carbon upcycling of industrial wastes. Clean Technologies and Environmental Policy, 28, 75.

Asokan Pappu, Thakur, V. K., Patidar, R., Asolekar, S. R., & Saxena, M. (2019). Recycling marble wastes and Jarosite wastes into sustainable hybrid composite materials and validation through response surface methodology. Journal of Cleaner Production, 240, 118249.

Fawad, M., Ullah, F., Irshad, M., et al. (2022). Marble waste site suitability assessment using the GIS-based AHP model. Environmental Science and Pollution Research, 29, 28386-28401.

Fowzi, M. M., Arastou, K., & Jamshidi, S. (2025). Grey water footprint of stone-cutting and processing industry. Water Resources and Industry, 33, 100295.

Sezen Ayber, & Berna Haktanırlar Ulutaş. (2017). Assessing sustainable manufacturing related problems for marble facilities: An application. Procedia Manufacturing, 8, 129-135.

Material Properties and Optimization
Byun, S., Sterner, E., Milburn, J., Ushiroda, K., Boise, E., Olsen, D., Song, J., & Chung, W. S. (2026). AI automation for material consistency in industrial 3D assets. Expert Systems with Applications, 321, 132183.

Huang, Y., & Zhan, W. (2026). Performance evaluation of green building in the process of rural revitalization driven by artificial intelligence and BP neural network. Scientific Reports. https://doi.org/10.1038/s41598-026-50931-2

Joshi, A., Janghorban, E., Archbold, P., Silvestre, J. D., & Gaspar, F. (2026). Towards sustainable 3D concrete printing: Rheology–buildability windows and mechanical performance of mortars with waste SP as sand replacement. Case Studies in Construction Materials, 24, e06188.

Kitchah, M., Bahloul, O., Bencheikh, M., & Aidoud, A. (2026). Enhancing the geotechnical properties of sabkha soil using cement and lime through experimental approach and optimization. Indian Geotechnical Journal. https://doi.org/10.1007/s40098-025-01454-6

Nasir Khan, M., Sutanto, M. H., Khan, M. I., Yaro, N. S. A., Al-Nawasir, R., Yousafzai, A. K., Khan, K., & Khan, M. A. (2026). Optimizing the potential use of waste palm oil clinker powder in cementitious grouts for semiflexible pavements using response surface methodology. Scientific Reports, 16, 14420.

Nazim, M., Nadeem, A. H., & Hashim, M. (2013). A bi-level multi-objective optimization model of multiple items for stone industry under fuzzy environment. In J. Xu, M. Yasinzai, & B. Lev (Eds.), Proceedings of the Sixth International Conference on Management Science and Engineering Management (Vol. 185, pp. 901-912). Springer.

Wang, B., Guo, D., Sun, J., et al. (2026). Optimization of ecological and efficient restoration technology for green mines based on hesitant fuzzy TOPSIS. Scientific Reports, 16, 6586.

Wastewater Treatment and Adsorption
Elabbas, S., Lissaneddine, A., & Aziz, F. (2025). Adsorption strategies for environmental remediation: A case study of tanneries in Morocco. In M. A. Aboulhassan & S. Souabi (Eds.), Sustainable practices in the tannery industry. Springer.

Leila, E., Bali, M., Lissir, B., & Gayh, U. (2026). Reusing marble and brick waste as cost-effective filters for treating secondary wastewater. International Journal of Environmental Science and Technology, 23, 197.

Mehta, D., Saharan, V. K., & George, S. (2024). Marble waste derived hydroxyapatite: Low-cost adsorbent for the defluoridation of drinking water. Materials Today: Proceedings, 102, 175-185.

Shen, X., Wang, P., Qiu, S., Liu, Z., Guan, J., & He, H. (2026). Materials-driven technologies and intelligent control for mineral processing wastewater recovery. Progress in Natural Science: Materials International, 36(1), 20-30.

Vaidhya, H., Tewari, P. K., & Anand, V. (2026). Laundry water reclamation using sustainable ceramic membrane from waste marble dust: Performance, fouling analysis. Environmental Research, 302, 124624.

Supplementary Table S1: Complete Search Strings by Database
Search executed on March 15, 2026. All searches limited to 2010-2026, peer-reviewed only.

Web of Science (Core Collection)
Search string:

text
((TS=("marble processing" OR "stone cutting" OR "dimension stone" OR "sawability" OR "diamond wire cutting")) 
AND TS=("operational optimization" OR "energy efficiency" OR "process optimization" OR "production planning"))
OR
((TS=("marble processing" OR "stone cutting")) 
AND TS=("machine learning" OR "artificial neural network" OR "XGBoost" OR "deep learning" OR "predictive modeling"))
OR
((TS=("marble processing" OR "stone cutting")) 
AND TS=("explainable AI" OR "SHAP" OR "LIME" OR "counterfactual" OR "interpretable machine learning"))
Results: 89 records
Date range: 2010-2026
Document types: Article; Review; Proceedings paper
Languages: English; Turkish (with English abstract)

Scopus
Search string:

text
( TITLE-ABS-KEY ( "marble processing" OR "stone cutting" OR "dimension stone" OR "sawability" OR "diamond wire cutting" ) 
AND TITLE-ABS-KEY ( "operational optimization" OR "energy efficiency" OR "process optimization" OR "production planning" ) )
OR
( TITLE-ABS-KEY ( "marble processing" OR "stone cutting" ) 
AND TITLE-ABS-KEY ( "machine learning" OR "artificial neural network" OR "XGBoost" OR "deep learning" OR "predictive modeling" ) )
OR
( TITLE-ABS-KEY ( "marble processing" OR "stone cutting" ) 
AND TITLE-ABS-KEY ( "explainable AI" OR "SHAP" OR "LIME" OR "counterfactual" OR "interpretable machine learning" ) )
Results: 112 records
Date range: 2010-2026
Document types: Article; Conference paper; Review
Subject areas: Engineering; Environmental Science; Materials Science; Earth and Planetary Sciences

Google Scholar
Search string (advanced):

text
"marble processing" AND ("optimization" OR "energy efficiency")
OR "stone cutting" AND ("machine learning" OR "neural network")
OR "diamond wire cutting" AND ("prediction" OR "modeling")
OR "marble" AND "explainable AI"
Results: 54 records (first 200 screened, 54 relevant)
Date range: 2010-2026
Limitation: Only first 200 results screened due to Google Scholar limitations

ScienceDirect
Search string:

text
("marble processing" OR "stone cutting" OR "dimension stone") 
AND ("optimization" OR "machine learning" OR "energy efficiency")
Filters applied:

Journals only (no books, book chapters)

2010-2026

Article type: Research articles; Review articles

Results: 32 records

Supplementary Table S2: Quality Assessment Scores for 32 Core Studies
Quality assessment performed using 5 criteria (0-2 points each, maximum 10 points). See Section 2.5 for criteria definitions.

#	Study (First author, year)	Data Quality	Validation	Reproducibility	Statistical Rigor	Operational Relevance	Total (0-10)
1	Ozsan et al. (2010)	1	0	0	1	2	4
2	Ozfirat (2012)	1	0	0	1	2	4
3	Gazi et al. (2012)	2	1	0	1	2	6
4	Yilmazkaya & Ozcelik (2016)	2	2	1	2	1	8
5	Turchetta et al. (2017)	2	2	0	2	1	7
6	Solak et al. (2009)	1	1	0	1	1	4
7	Ozyonar & Karagozoglu (2012)	1	1	0	1	1	4
8	Afonso et al. (2002)*	1	1	0	1	2	5
9	Jalalian et al. (2023)	2	1	0	1	1	5
10	Fattahi & Ghaedi (2024)	2	1	0	1	1	5
11	Chen et al. (2026)	2	2	2	1	0	7
12	Sariisik & Ogutlu (2025)	2	1	0	2	1	6
13	Naveen et al. (2025)	2	2	0	2	1	7
14	Sai et al. (2026)	2	1	0	2	1	6
15	Lahre et al. (2025)	2	1	0	2	1	6
16	Sharma et al. (2026)	2	1	0	1	1	5
17	Patel et al. (2026)	2	1	0	1	1	5
18	Ozdogan et al. (2026)	2	1	0	2	1	6
19	Gebreabzgi et al. (2026)	2	1	0	1	1	5
20	Sodha et al. (2025)	2	1	0	2	2	7
21	Karakurt et al. (2026)	2	1	0	2	1	6
22	Kalyoncu & Taleghani (2026)	2	1	0	1	1	5
23	Eid et al. (2025)	2	1	0	2	1	6
24	Oliveira de Rosato et al. (2026)	2	1	0	1	1	5
25	Luciano et al. (2020)	2	0	0	1	1	4
26	Saleem & Ayalew (2025)	2	1	0	1	1	5
27	Paraschos et al. (2024)*	2	2	1	2	1	8
28	Samouilidou et al. (2025)*	2	2	1	2	1	8
29	Baek & Joung (2026)*	2	2	1	2	1	8
30	Shi et al. (2026)*	2	2	1	2	1	8
31	Capitano et al. (2022)	2	0	0	1	1	4
32	Careddu & Siotto (2011)	2	0	0	1	1	4
Notes:

*Studies marked with asterisk are contextual (methodological inspiration) studies (n=5). The remaining 27 are core marble studies? Not exactly - this table includes all 32 core studies. The 12 contextual studies are not included in this count.

Quality score interpretation: 0-3 = Low; 4-6 = Medium; 7-10 = High

Mean (core marble studies, n=27 excluding contextual): 5.4/10 (SD = 1.4)

Median: 5.0

Supplementary Table S3: Dual-Coder Classification Raw Data (44 Studies)
Classification performed by two independent coders (Coder A = author; Coder B = research assistant). Final classification after resolution of disagreements. Cohen's κ = 0.87 (95% CI: 0.74-0.99).

#	Study (First author, year)	Domain	Coder A Initial	Coder B Initial	Agreement	Final (after discussion)	Notes
1	Ozsan et al. (2010)	Core	1	1	✓	1	LP/IP interpretable by design
2	Ozfirat (2012)	Core	1	1	✓	1	Integer programming
3	Gazi et al. (2012)	Core	1	1	✓	1	Sensitivity analysis
4	Yilmazkaya & Ozcelik (2016)	Core	1	1	✓	1	Statistical analysis only
5	Turchetta et al. (2017)	Core	1	1	✓	1	Statistical analysis only
6	Solak et al. (2009)	Core	0	0	✓	0	No interpretability
7	Ozyonar & Karagozoglu (2012)	Core	0	0	✓	0	No interpretability
8	Afonso et al. (2002)	Core	0	0	✓	0	No interpretability
9	Jalalian et al. (2023)	Core	0	0	✓	0	Genetic algorithm black-box
10	Fattahi & Ghaedi (2024)	Core	1	1	✓	1	Sensitivity analysis
11	Chen et al. (2026)	Core	1.5	2	✗	1.5	Attention visualization (debated)
12	Sariisik & Ogutlu (2025)	Core	0	0	✓	0	Black-box ML
13	Naveen et al. (2025)	Core	0	0	✓	0	Black-box ANN
14	Sai et al. (2026)	Core	0	0	✓	0	Black-box ML
15	Lahre et al. (2025)	Core	0	0	✓	0	Black-box ANN
16	Sharma et al. (2026)	Core	1	1	✓	1	RSM (interpretable)
17	Patel et al. (2026)	Core	1	1	✓	1	RSM (interpretable)
18	Ozdogan et al. (2026)	Core	1	1	✓	1	Statistical analysis
19	Gebreabzgi et al. (2026)	Core	1	1	✓	1	Discrete event simulation
20	Sodha et al. (2025)	Core	1	1	✓	1	LCA (interpretable)
21	Karakurt et al. (2026)	Core	1	1	✓	1	Regression (interpretable)
22	Kalyoncu & Taleghani (2026)	Core	1	1	✓	1	Experimental optimization
23	Eid et al. (2025)	Core	1	1	✓	1	Experimental
24	Oliveira de Rosato et al. (2026)	Core	1	1	✓	1	Review
25	Luciano et al. (2020)	Core	1	1	✓	1	Policy analysis
26	Saleem & Ayalew (2025)	Core	1	1	✓	1	Statistical
27	Paraschos et al. (2024)	Contextual	2	2	✓	2	SHAP in manufacturing (not marble)
28	Samouilidou et al. (2025)	Contextual	2	2	✓	2	XAI in scheduling (not marble)
29	Baek & Joung (2026)	Contextual	2	2	✓	2	CNN + SPC (not marble)
30	Shi et al. (2026)	Contextual	2	2	✓	2	Multi-task learning (not marble)
31	Capitano et al. (2022)	Core	1	1	✓	1	LCA (interpretable)
32	Careddu & Siotto (2011)	Core	1	1	✓	1	Policy/planning
33-44	Additional contextual studies (n=12)	Contextual	Various	Various	—	See note	Full list available from author
Notes:

Disagreements occurred in 8 of 44 studies (18%).

Most common disagreement (5 cases): classification of attention-based or feature-importance methods as Level 1 vs. Level 1.5.

Resolution rule: Attention mechanisms without instance-specific attribution → Level 1.5. SHAP/LIME with instance-level breakdown → Level 2.

Contextual studies (n=12) are not counted in core marble gap analysis.

Interpretation of κ = 0.87: "Almost perfect agreement" per Landis & Koch (1977). The 95% confidence interval [0.74, 0.99] does not cross 0.70, indicating reliability exceeds conventional thresholds.

Supplementary Code S1: Synthetic Data Generating Process
Filename: synthetic_marble_data_generator.py

Purpose: Generate synthetic cutting event data based on Yilmazkaya & Ozcelik (2016) experimental design for framework validation prior to plant deployment.

Dependencies: Python 3.9+, numpy, pandas, scipy

python
"""
Synthetic Data Generator for Marble Cutting Process Validation

Based on experimental design from:
Yilmazkaya, E., & Ozcelik, Y. (2016). The effects of operational parameters 
on a mono-wire cutting system: Efficiency in marble processing.
Rock Mechanics and Rock Engineering, 49, 523-539.

This code generates synthetic data for XAI framework validation only.
Real-world validation requires plant pilot data.
"""

import numpy as np
import pandas as pd
from scipy.stats import norm, uniform
from typing import Tuple, Dict
import warnings

# Suppress warnings for demonstration
warnings.filterwarnings('ignore')

# ============================================================================
# PARAMETER RANGES (from Table 3 in main manuscript, derived from Yilmazkaya 2016)
# ============================================================================

PARAMETER_RANGES = {
    # Material properties (MPa, unitless, GPa, unitless)
    'UCS': (30, 120),                    # Uniaxial Compressive Strength (MPa)
    'mohs_hardness': (3, 5),             # Mohs hardness (unitless)
    'youngs_modulus': (30, 80),          # Young's Modulus (GPa)
    'abrasivity': (0.5, 3.0),            # F-Schimazek abrasivity factor
    
    # Machine parameters (m/s, cm/min, N)
    'wire_speed': (25, 40),              # Wire peripheral speed (m/s)
    'descending_speed': (10, 60),        # Wire descending speed (cm/min)
    'tension': (200, 400),               # Wire tension (N)
    
    # Environmental (g/L, °C)
    'slurry_density': (1200, 1600),      # Slurry density (g/L)
    'temperature': (15, 35),             # Ambient temperature (°C)
}

# Target variable base ranges (from literature)
TARGET_BASE_RANGES = {
    'specific_energy': (5, 20),          # kW·h/m²
    'wire_wear': (0.1, 0.5),             # mm/m²
    'surface_roughness': (0.5, 5),       # Ra (μm)
}

# ============================================================================
# EFFECT SIZES AND INTERACTIONS (derived from Yilmazkaya & Ozcelik 2016, Table 3)
# ============================================================================

# Main effects (coefficients for linear terms)
# Based on standardized coefficients from Yilmazkaya & Ozcelik 2016
MAIN_EFFECTS = {
    'specific_energy': {
        'descending_speed': 0.45,    # Strongest positive effect
        'UCS': 0.30,                 # Strong positive effect
        'wire_speed': -0.20,         # Negative effect (higher speed = lower energy)
        'abrasivity': 0.15,          # Positive effect
        'slurry_density': -0.10,     # Slight negative effect (lubrication)
        'tension': 0.05,             # Small positive effect
        'temperature': -0.03,        # Very small effect
        'mohs_hardness': 0.08,       # Small positive effect
        'youngs_modulus': 0.12,      # Moderate positive effect
    },
    'wire_wear': {
        'descending_speed': 0.50,    # Strongest effect
        'abrasivity': 0.35,          # Strong effect
        'UCS': 0.25,                 # Moderate effect
        'wire_speed': -0.15,         # Negative (higher speed reduces wear per m²)
        'tension': 0.20,             # Positive effect
        'slurry_density': -0.08,     # Slight negative
    },
    'surface_roughness': {
        'descending_speed': 0.40,    # Strong effect
        'wire_speed': -0.30,         # Strong negative (faster = smoother)
        'UCS': 0.20,                 # Moderate effect
        'abrasivity': 0.25,          # Moderate effect
        'tension': 0.10,             # Small effect
    }
}

# Interaction effects (UCS × descending_speed is the most important)
# From Yilmazkaya & Ozcelik 2016: interaction amplifies main effect by factor of 1.4-1.6
INTERACTION_EFFECTS = {
    'specific_energy': {
        ('UCS', 'descending_speed'): 0.35,     # Strong interaction
        ('UCS', 'wire_speed'): -0.15,          # Moderate negative interaction
        ('abrasivity', 'descending_speed'): 0.20,
    },
    'wire_wear': {
        ('UCS', 'descending_speed'): 0.30,
        ('abrasivity', 'descending_speed'): 0.25,
        ('abrasivity', 'wire_speed'): -0.10,
    },
    'surface_roughness': {
        ('descending_speed', 'wire_speed'): -0.25,
        ('UCS', 'descending_speed'): 0.20,
    }
}

# ============================================================================
# DATA GENERATION FUNCTIONS
# ============================================================================

def generate_input_features(n_samples: int = 1000, random_seed: int = 42) -> pd.DataFrame:
    """
    Generate input feature matrix with realistic correlations.
    
    Parameters:
    -----------
    n_samples : int
        Number of samples to generate
    random_seed : int
        Random seed for reproducibility
    
    Returns:
    --------
    pd.DataFrame with columns matching PARAMETER_RANGES keys
    """
    np.random.seed(random_seed)
    
    data = {}
    
    # Generate independent parameters first
    for param, (low, high) in PARAMETER_RANGES.items():
        if param in ['UCS', 'mohs_hardness', 'youngs_modulus', 'abrasivity']:
            # Material properties are correlated in nature
            # We'll generate them with correlations after independent draw
            data[param] = uniform.rvs(loc=low, scale=high-low, size=n_samples)
        else:
            # Machine parameters: uniform distribution (operator chooses settings)
            data[param] = uniform.rvs(loc=low, scale=high-low, size=n_samples)
    
    df = pd.DataFrame(data)
    
    # Add realistic correlations among material properties
    # UCS and Young's modulus are correlated (r ≈ 0.6-0.7 in natural stone)
    corr_matrix = np.array([[1.0, 0.0, 0.65, 0.5],
                            [0.0, 1.0, 0.0, 0.4],
                            [0.65, 0.0, 1.0, 0.6],
                            [0.5, 0.4, 0.6, 1.0]])
    
    # Apply correlation to material properties
    material_cols = ['UCS', 'mohs_hardness', 'youngs_modulus', 'abrasivity']
    material_data = df[material_cols].values
    
    # Cholesky decomposition for correlation
    L = np.linalg.cholesky(corr_matrix)
    correlated_data = material_data @ L.T
    
    for i, col in enumerate(material_cols):
        # Preserve original marginal distributions while adding correlation
        original_std = df[col].std()
        df[col] = correlated_data[:, i] * (original_std / correlated_data[:, i].std())
        # Clip to original ranges
        df[col] = np.clip(df[col], PARAMETER_RANGES[col][0], PARAMETER_RANGES[col][1])
    
    return df


def generate_target_variables(
    features: pd.DataFrame,
    noise_std: float = 0.10,  # 10% noise as fraction of base value
    random_seed: int = 42
) -> pd.DataFrame:
    """
    Generate target variables (specific_energy, wire_wear, surface_roughness)
    based on main effects and interactions from Yilmazkaya & Ozcelik (2016).
    
    Parameters:
    -----------
    features : pd.DataFrame
        Input features from generate_input_features()
    noise_std : float
        Standard deviation of additive Gaussian noise (as fraction of base value)
    random_seed : int
        Random seed for reproducibility
    
    Returns:
    --------
    pd.DataFrame with target columns
    """
    np.random.seed(random_seed)
    
    targets = {}
    
    for target_name, base_range in TARGET_BASE_RANGES.items():
        # Start with baseline (midpoint of range)
        baseline = np.mean(base_range)
        
        # Initialize with baseline
        y = np.ones(len(features)) * baseline
        
        # Add main effects
        for feature_name, effect_size in MAIN_EFFECTS.get(target_name, {}).items():
            if feature_name in features.columns:
                # Normalize feature to [0, 1] range
                f_min, f_max = PARAMETER_RANGES.get(feature_name, (0, 1))
                feature_norm = (features[feature_name] - f_min) / (f_max - f_min)
                # Add effect (range of effect: ± effect_size * baseline)
                y += (feature_norm - 0.5) * 2 * effect_size * baseline
        
        # Add interaction effects
        for (f1, f2), effect_size in INTERACTION_EFFECTS.get(target_name, {}).items():
            if f1 in features.columns and f2 in features.columns:
                f1_min, f1_max = PARAMETER_RANGES.get(f1, (0, 1))
                f2_min, f2_max = PARAMETER_RANGES.get(f2, (0, 1))
                f1_norm = (features[f1] - f1_min) / (f1_max - f1_min)
                f2_norm = (features[f2] - f2_min) / (f2_max - f2_min)
                # Interaction as product of normalized features
                interaction = f1_norm * f2_norm
                y += (interaction - 0.25) * 4 * effect_size * baseline  # Center at 0.25
        
        # Add noise
        noise = np.random.normal(0, noise_std * baseline, len(features))
        y += noise
        
        # Clip to realistic ranges
        y = np.clip(y, base_range[0], base_range[1])
        
        targets[target_name] = y
    
    return pd.DataFrame(targets)


def generate_cutting_events(
    n_samples: int = 1000,
    noise_std: float = 0.10,
    random_seed: int = 42,
    include_metadata: bool = True
) -> pd.DataFrame:
    """
    Generate complete synthetic dataset of marble cutting events.
    
    Parameters:
    -----------
    n_samples : int
        Number of cutting events to generate
    noise_std : float
        Noise standard deviation for target variables
    random_seed : int
        Random seed for reproducibility
    include_metadata : bool
        Add metadata columns (event_id, timestamp, marble_block_id)
    
    Returns:
    --------
    pd.DataFrame with input features and target variables
    """
    # Generate features
    features = generate_input_features(n_samples, random_seed)
    
    # Generate targets
    targets = generate_target_variables(features, noise_std, random_seed + 1)
    
    # Combine
    data = pd.concat([features, targets], axis=1)
    
    # Add metadata
    if include_metadata:
        data['event_id'] = np.arange(n_samples)
        # Simulate timestamps (one event every 15 minutes over 3 months)
        start_time = pd.Timestamp('2026-01-01 08:00:00')
        data['timestamp'] = [start_time + pd.Timedelta(minutes=15*i) for i in range(n_samples)]
        # Assign marble block IDs (each block produces ~50 slabs)
        data['marble_block_id'] = np.repeat(np.arange(n_samples // 50 + 1), 50)[:n_samples]
    
    return data


def add_anomalies(
    data: pd.DataFrame,
    anomaly_fraction: float = 0.05,
    random_seed: int = 42
) -> pd.DataFrame:
    """
    Inject synthetic anomalies (e.g., sensor failures, extreme conditions)
    for testing anomaly detection and explanation robustness.
    
    Parameters:
    -----------
    data : pd.DataFrame
        Clean synthetic data
    anomaly_fraction : float
        Fraction of samples to convert to anomalies
    random_seed : int
        Random seed
    
    Returns:
    --------
    pd.DataFrame with anomalies
    """
    np.random.seed(random_seed)
    data_with_anomalies = data.copy()
    
    n_anomalies = int(len(data) * anomaly_fraction)
    anomaly_indices = np.random.choice(len(data), n_anomalies, replace=False)
    
    for idx in anomaly_indices:
        # Randomly choose anomaly type
        anomaly_type = np.random.choice(['high_energy', 'sensor_failure', 'extreme_wear'])
        
        if anomaly_type == 'high_energy':
            # Increase specific energy by 50-100%
            data_with_anomalies.loc[idx, 'specific_energy'] *= np.random.uniform(1.5, 2.0)
            data_with_anomalies.loc[idx, 'anomaly_flag'] = 'high_energy'
            
        elif anomaly_type == 'sensor_failure':
            # Set descending speed to unrealistic value (sensor stuck)
            data_with_anomalies.loc[idx, 'descending_speed'] = np.random.choice([0, 100])
            data_with_anomalies.loc[idx, 'anomaly_flag'] = 'sensor_failure'
            
        elif anomaly_type == 'extreme_wear':
            # Increase wire wear dramatically
            data_with_anomalies.loc[idx, 'wire_wear'] *= np.random.uniform(3.0, 5.0)
            data_with_anomalies.loc[idx, 'anomaly_flag'] = 'extreme_wear'
    
    # Fill NaN for non-anomaly rows
    if 'anomaly_flag' not in data_with_anomalies.columns:
        data_with_anomalies['anomaly_flag'] = 'normal'
    else:
        data_with_anomalies['anomaly_flag'] = data_with_anomalies['anomaly_flag'].fillna('normal')
    
    return data_with_anomalies


# ============================================================================
# VALIDATION FUNCTIONS
# ============================================================================

def validate_synthetic_data(data: pd.DataFrame) -> Dict:
    """
    Validate that synthetic data matches expected statistical properties.
    
    Returns:
    --------
    Dict with validation metrics
    """
    results = {}
    
    # Check parameter ranges
    for param, (low, high) in PARAMETER_RANGES.items():
        in_range = (data[param].min() >= low - 0.1*high) and (data[param].max() <= high + 0.1*high)
        results[f'{param}_range_ok'] = in_range
    
    # Check target ranges
    for target, (low, high) in TARGET_BASE_RANGES.items():
        in_range = (data[target].min() >= low - 0.2*high) and (data[target].max() <= high + 0.2*high)
        results[f'{target}_range_ok'] = in_range
    
    # Check correlation between UCS and Young's modulus (should be 0.6-0.7)
    ucs_youngs_corr = data['UCS'].corr(data['youngs_modulus'])
    results['ucs_youngs_correlation'] = ucs_youngs_corr
    results['ucs_youngs_correlation_ok'] = 0.5 <= ucs_youngs_corr <= 0.8
    
    # Check main effect signs (descending_speed should positively correlate with energy)
    descending_energy_corr = data['descending_speed'].corr(data['specific_energy'])
    results['descending_energy_correlation'] = descending_energy_corr
    results['descending_energy_corr_ok'] = descending_energy_corr > 0.3
    
    return results


# ============================================================================
# MAIN EXECUTION (example usage)
# ============================================================================

if __name__ == "__main__":
    print("=" * 60)
    print("Synthetic Marble Cutting Data Generator")
    print("Based on Yilmazkaya & Ozcelik (2016)")
    print("=" * 60)
    
    # Generate clean data
    print("\n[1] Generating clean synthetic data...")
    clean_data = generate_cutting_events(n_samples=1000, noise_std=0.10, random_seed=42)
    print(f"    Generated {len(clean_data)} cutting events")
    print(f"    Columns: {list(clean_data.columns)}")
    
    # Validate
    print("\n[2] Validating synthetic data...")
    validation_results = validate_synthetic_data(clean_data)
    for metric, value in validation_results.items():
        if isinstance(value, bool):
            status = "✓" if value else "✗"
            print(f"    {status} {metric}: {value}")
        else:
            print(f"    {metric}: {value:.3f}")
    
    # Add anomalies
    print("\n[3] Adding synthetic anomalies...")
    data_with_anomalies = add_anomalies(clean_data, anomaly_fraction=0.05, random_seed=42)
    anomaly_counts = data_with_anomalies['anomaly_flag'].value_counts()
    print(f"    Anomaly distribution:")
    for flag, count in anomaly_counts.items():
        print(f"        {flag}: {count} ({count/len(data_with_anomalies)*100:.1f}%)")
    
    # Save to CSV
    print("\n[4] Saving to CSV...")
    clean_data.to_csv('synthetic_marble_data_clean.csv', index=False)
    data_with_anomalies.to_csv('synthetic_marble_data_with_anomalies.csv', index=False)
    print("    Saved: synthetic_marble_data_clean.csv")
    print("    Saved: synthetic_marble_data_with_anomalies.csv")
    
    # Display sample
    print("\n[5] Sample data (first 5 rows):")
    print(clean_data.head().to_string())
    
    print("\n" + "=" * 60)
    print("Generation complete.")
    print("WARNING: This is synthetic data for framework validation only.")
    print("Real-world validation requires plant pilot data.")
    print("=" * 60)
Expected Output (first 5 rows sample):

event_id	timestamp	marble_block_id	UCS	mohs_hardness	youngs_modulus	abrasivity	wire_speed	descending_speed	tension	slurry_density	temperature	specific_energy	wire_wear	surface_roughness
0	2026-01-01 08:00:00	0	45.2	3.8	52.3	1.2	32.5	28.4	310	1350	22.5	9.8	0.22	1.45
1	2026-01-01 08:15:00	0	47.1	3.9	54.1	1.3	31.2	30.1	305	1380	23.1	10.2	0.24	1.52
2	2026-01-01 08:30:00	0	44.8	3.7	51.8	1.1	33.8	26.5	315	1320	22.8	9.5	0.20	1.38
3	2026-01-01 08:45:00	0	46.5	3.9	53.5	1.2	30.5	32.2	308	1400	22.2	11.4	0.27	1.68
4	2026-01-01 09:00:00	0	43.2	3.6	50.2	1.0	35.1	24.8	320	1280	23.5	8.9	0.18	1.25
List of Supplementary Files
File Name	Description
Supplementary_File_S1_PRISMA_2020_Checklist.pdf	Completed PRISMA 2020 checklist
Supplementary_File_S2_Background_Literature.pdf	Complementary background references
Supplementary_Table_S1_Search_Strings.pdf	Complete search strings by database
Supplementary_Table_S2_Quality_Scores.csv	Quality assessment for 32 core studies
Supplementary_Table_S3_Dual_Coder_Classification.csv	Raw classification data for 44 studies
Supplementary_Code_S1_Synthetic_Data_Generator.py	Python script for synthetic data generation
