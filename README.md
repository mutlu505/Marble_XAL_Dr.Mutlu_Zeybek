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

"""
Marble Processing XAI Framework - Simulation and Validation
Based on: "Explainable Artificial Intelligence for Operational Optimization in Marble Processing Plants"
Authors: Mutlu Zeybek, et al.

This script implements:
1. Synthetic data generation based on Yilmazkaya & Ozcelik (2016) experimental design
2. XGBoost multi-task prediction (Energy, Wear, Surface Quality)
3. SHAP global and local explanations
4. Counterfactual optimization using DiCE
5. Validation metrics and visualization
"""

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import xgboost as xgb
import shap
import warnings
warnings.filterwarnings('ignore')

# Set random seed for reproducibility
np.random.seed(42)

# ============================================================================
# PART 1: SYNTHETIC DATA GENERATION
# Based on Yilmazkaya & Ozcelik (2016) parameter ranges and effect sizes
# ============================================================================

class MarbleDataGenerator:
    """
    Generates synthetic marble cutting data based on published experimental ranges.
    Physical relationships are encoded to reflect real-world interactions.
    """
    
    def __init__(self, n_samples=1000):
        self.n_samples = n_samples
        self._define_parameter_ranges()
        self._define_physical_relationships()
    
    def _define_parameter_ranges(self):
        """Define realistic parameter ranges from Table 3 in the paper"""
        self.ranges = {
            # Material properties
            'UCS': (30, 120),              # Uniaxial Compressive Strength (MPa)
            'mohs_hardness': (3, 5),       # Mohs hardness scale
            'youngs_modulus': (30, 80),    # GPa
            'abrasivity': (0.5, 3.0),      # F-Schimazek abrasivity factor
            
            # Machine parameters
            'wire_speed': (25, 40),        # Peripheral speed (m/s)
            'desc_speed': (10, 60),        # Descending speed (cm/min)
            'wire_tension': (1200, 1800),  # Tension (N)
            
            # Environmental
            'slurry_density': (100, 300),  # g/L
            'coolant_flow': (5, 15),       # L/min
        }
    
    def _define_physical_relationships(self):
        """
        Encode physical relationships from the literature:
        - Higher UCS increases energy consumption and wear
        - Higher desc_speed increases energy but decreases time
        - Optimal wire_speed exists around 32-35 m/s
        - Interaction: UCS amplifies the effect of desc_speed
        """
        self.effect_sizes = {
            'energy_UCS': 0.18,
            'energy_desc_speed': 0.25,
            'energy_wire_speed': -0.12,  # Negative: faster wire reduces specific energy
            'energy_interaction': 0.08,   # UCS × desc_speed interaction
            'wear_UCS': 0.22,
            'wear_desc_speed': 0.15,
            'wear_wire_speed': -0.18,
            'surface_UCS': 0.20,
            'surface_desc_speed': 0.10,
        }
    
    def generate(self):
        """Generate complete dataset with physical constraints"""
        np.random.seed(42)
        
        # Generate input features with realistic correlations
        data = {}
        
        # Material properties (correlated: higher UCS → higher mohs)
        data['UCS'] = np.random.uniform(self.ranges['UCS'][0], self.ranges['UCS'][1], self.n_samples)
        data['mohs_hardness'] = 3 + (data['UCS'] - 30) / 90 * 2 + np.random.normal(0, 0.2, self.n_samples)
        data['mohs_hardness'] = np.clip(data['mohs_hardness'], 3, 5)
        data['youngs_modulus'] = 30 + (data['UCS'] - 30) / 90 * 50 + np.random.normal(0, 5, self.n_samples)
        data['abrasivity'] = 0.5 + (data['UCS'] - 30) / 90 * 2.5 + np.random.normal(0, 0.3, self.n_samples)
        data['abrasivity'] = np.clip(data['abrasivity'], 0.5, 3.0)
        
        # Machine parameters (operators adjust desc_speed based on UCS)
        data['wire_speed'] = np.random.uniform(self.ranges['wire_speed'][0], self.ranges['wire_speed'][1], self.n_samples)
        
        # Descending speed is often reduced for harder marble (operator behavior)
        base_desc = np.random.uniform(self.ranges['desc_speed'][0], self.ranges['desc_speed'][1], self.n_samples)
        ucs_factor = (data['UCS'] - 30) / 90  # 0 to 1
        data['desc_speed'] = base_desc * (1 - 0.4 * ucs_factor)  # Slower for harder marble
        data['desc_speed'] = np.clip(data['desc_speed'], self.ranges['desc_speed'][0], self.ranges['desc_speed'][1])
        
        data['wire_tension'] = np.random.uniform(self.ranges['wire_tension'][0], self.ranges['wire_tension'][1], self.n_samples)
        data['slurry_density'] = np.random.uniform(self.ranges['slurry_density'][0], self.ranges['slurry_density'][1], self.n_samples)
        data['coolant_flow'] = np.random.uniform(self.ranges['coolant_flow'][0], self.ranges['coolant_flow'][1], self.n_samples)
        
        # Add some noise to features
        for key in data:
            data[key] = data[key] + np.random.normal(0, data[key].std() * 0.05, self.n_samples)
            data[key] = np.clip(data[key], self.ranges[key][0] if key in self.ranges else (-np.inf, np.inf), 
                               self.ranges[key][1] if key in self.ranges else (np.inf, np.inf))
        
        df = pd.DataFrame(data)
        
        # Generate target variables with physical interactions
        # Normalize features for consistent effect application
        df_norm = (df - df.min()) / (df.max() - df.min())
        
        # SPECIFIC ENERGY (kW·h/m²) - Target range: 5-20
        energy_base = 5
        energy_effects = (
            self.effect_sizes['energy_UCS'] * df_norm['UCS'] * 15 +
            self.effect_sizes['energy_desc_speed'] * df_norm['desc_speed'] * 12 +
            self.effect_sizes['energy_wire_speed'] * (1 - df_norm['wire_speed']) * 8 +
            self.effect_sizes['energy_interaction'] * df_norm['UCS'] * df_norm['desc_speed'] * 10 +
            0.05 * df_norm['abrasivity'] * 5 +
            -0.03 * df_norm['coolant_flow'] * 3
        )
        
        # Add quadratic effect for wire_speed (optimal at mid-range)
        wire_opt_effect = -0.15 * (df_norm['wire_speed'] - 0.5)**2 * 10
        
        noise_energy = np.random.normal(0, 0.8, self.n_samples)
        df['specific_energy'] = energy_base + energy_effects + wire_opt_effect + noise_energy
        df['specific_energy'] = np.clip(df['specific_energy'], 5, 20)
        
        # DIAMOND WIRE WEAR (mm/m²) - Target range: 0.1-0.5
        wear_base = 0.1
        wear_effects = (
            self.effect_sizes['wear_UCS'] * df_norm['UCS'] * 0.35 +
            self.effect_sizes['wear_desc_speed'] * df_norm['desc_speed'] * 0.2 +
            self.effect_sizes['wear_wire_speed'] * (1 - df_norm['wire_speed']) * 0.15 +
            0.08 * df_norm['abrasivity'] * 0.15 +
            0.03 * df_norm['slurry_density'] / 300 * 0.1
        )
        noise_wear = np.random.normal(0, 0.03, self.n_samples)
        df['wire_wear'] = wear_base + wear_effects + noise_wear
        df['wire_wear'] = np.clip(df['wire_wear'], 0.08, 0.55)
        
        # SURFACE QUALITY (Ra, μm) - Target range: 0.5-5
        surface_base = 0.5
        surface_effects = (
            self.effect_sizes['surface_UCS'] * df_norm['UCS'] * 4 +
            self.effect_sizes['surface_desc_speed'] * df_norm['desc_speed'] * 2.5 +
            -0.08 * df_norm['wire_speed'] * 2 +
            0.05 * df_norm['abrasivity'] * 1.5
        )
        noise_surface = np.random.normal(0, 0.2, self.n_samples)
        df['surface_quality'] = surface_base + surface_effects + noise_surface
        df['surface_quality'] = np.clip(df['surface_quality'], 0.3, 5.5)
        
        return df


# ============================================================================
# PART 2: XAI MODEL TRAINING
# Multi-task XGBoost with SHAP explanations
# ============================================================================

class MarbleXAI:
    """
    XAI Framework for Marble Processing Optimization
    Implements: Prediction + SHAP explanations + Counterfactuals
    """
    
    def __init__(self, feature_names=None, target_names=None):
        self.feature_names = feature_names or [
            'UCS', 'mohs_hardness', 'youngs_modulus', 'abrasivity',
            'wire_speed', 'desc_speed', 'wire_tension', 
            'slurry_density', 'coolant_flow'
        ]
        self.target_names = target_names or ['specific_energy', 'wire_wear', 'surface_quality']
        self.models = {}
        self.scaler = StandardScaler()
        self.explainers = {}
        
    def train(self, X, y_dict, verbose=True):
        """
        Train separate XGBoost models for each target (multi-task)
        
        Parameters:
        - X: feature DataFrame
        - y_dict: dict with keys as target names, values as Series
        """
        # Scale features
        X_scaled = self.scaler.fit_transform(X)
        
        for target_name in self.target_names:
            if verbose:
                print(f"Training model for: {target_name}")
            
            y = y_dict[target_name]
            
            # Split data
            X_train, X_test, y_train, y_test = train_test_split(
                X_scaled, y, test_size=0.2, random_state=42
            )
            
            # XGBoost with optimized hyperparameters
            model = xgb.XGBRegressor(
                n_estimators=200,
                max_depth=5,
                learning_rate=0.1,
                subsample=0.8,
                colsample_bytree=0.8,
                random_state=42,
                early_stopping_rounds=20,
                eval_metric='mae'
            )
            
            # Train with validation set
            eval_set = [(X_train, y_train), (X_test, y_test)]
            model.fit(
                X_train, y_train,
                eval_set=eval_set,
                verbose=False
            )
            
            # Evaluate
            y_pred = model.predict(X_test)
            mae = mean_absolute_error(y_test, y_pred)
            r2 = r2_score(y_test, y_pred)
            
            if verbose:
                print(f"  MAE: {mae:.3f}, R²: {r2:.3f}")
            
            self.models[target_name] = model
            
            # Store test data for later use
            self.X_test = X_test
            self.y_test_dict = {target_name: y_test for target_name in self.target_names}
            
        # Initialize SHAP explainers
        for target_name in self.target_names:
            self.explainers[target_name] = shap.TreeExplainer(self.models[target_name])
        
        return self
    
    def predict(self, X, target_name=None):
        """Make predictions for one or all targets"""
        X_scaled = self.scaler.transform(X)
        
        if target_name:
            return self.models[target_name].predict(X_scaled)
        else:
            predictions = {}
            for target_name in self.target_names:
                predictions[target_name] = self.models[target_name].predict(X_scaled)
            return predictions
    
    def explain_global(self, target_name, X_sample=None):
        """Generate global SHAP explanations"""
        if X_sample is None:
            X_sample = self.X_test
        
        shap_values = self.explainers[target_name].shap_values(X_sample)
        return shap_values
    
    def explain_local(self, target_name, instance_idx, X_sample=None):
        """Generate local explanation for a specific instance"""
        if X_sample is None:
            X_sample = self.X_test
        
        shap_values = self.explainers[target_name].shap_values(X_sample)
        
        # Get the instance's shap values
        instance_shap = shap_values[instance_idx]
        instance_features = X_sample[instance_idx]
        
        # Create explanation dictionary
        explanation = {
            'feature_names': self.feature_names,
            'feature_values': instance_features,
            'shap_values': instance_shap,
            'base_value': self.explainers[target_name].expected_value,
            'prediction': self.models[target_name].predict(X_sample[instance_idx:instance_idx+1])[0]
        }
        
        return explanation
    
    def generate_counterfactual(self, target_name, current_X, target_reduction=0.20, 
                                 feature_bounds=None):
        """
        Generate counterfactual recommendations using optimization
        
        Parameters:
        - target_name: which output to optimize (e.g., 'specific_energy')
        - current_X: current feature values (1D array or DataFrame row)
        - target_reduction: desired reduction fraction (e.g., 0.20 for 20% reduction)
        - feature_bounds: dict of (min, max) for each feature
        
        Returns:
        - recommended_X: counterfactual feature values
        - predicted_improvement: expected new prediction
        """
        from scipy.optimize import minimize
        
        # Convert input to numpy array
        if isinstance(current_X, pd.DataFrame):
            current_X = current_X.iloc[0].values
        elif isinstance(current_X, pd.Series):
            current_X = current_X.values
        
        # Scale current_X
        current_X_scaled = self.scaler.transform([current_X])[0]
        
        # Get current prediction
        current_pred = self.models[target_name].predict([current_X_scaled])[0]
        target_value = current_pred * (1 - target_reduction)
        
        # Define feature bounds (in original scale, will be scaled)
        if feature_bounds is None:
            feature_bounds = {
                'wire_speed': (25, 40),
                'desc_speed': (10, 60),
                'wire_tension': (1200, 1800),
                'coolant_flow': (5, 15),
            }
        
        # Identify which features are controllable
        controllable_indices = []
        for i, feat in enumerate(self.feature_names):
            if feat in feature_bounds:
                controllable_indices.append(i)
        
        def objective(delta):
            """Minimize L1 norm of changes + penalty for infeasibility"""
            x_new_scaled = current_X_scaled.copy()
            for idx in controllable_indices:
                x_new_scaled[idx] += delta[controllable_indices.index(idx)]
            
            # Predict new value
            pred_new = self.models[target_name].predict([x_new_scaled])[0]
            
            # Loss = distance to target + L1 penalty on changes
            target_loss = (pred_new - target_value) ** 2
            l1_penalty = np.sum(np.abs(delta)) * 0.1
            
            return target_loss + l1_penalty
        
        # Optimize
        n_controllable = len(controllable_indices)
        result = minimize(
            objective,
            x0=np.zeros(n_controllable),
            method='L-BFGS-B'
        )
        
        # Generate counterfactual
        recommended_X_scaled = current_X_scaled.copy()
        for i, idx in enumerate(controllable_indices):
            recommended_X_scaled[idx] += result.x[i]
        
        # Inverse transform to original scale
        recommended_X = self.scaler.inverse_transform([recommended_X_scaled])[0]
        new_pred = self.models[target_name].predict([recommended_X_scaled])[0]
        
        # Create recommendation dictionary
        recommendation = {
            'current_parameters': {feat: current_X[i] for i, feat in enumerate(self.feature_names)},
            'recommended_parameters': {feat: recommended_X[i] for i, feat in enumerate(self.feature_names)},
            'changes': {feat: recommended_X[i] - current_X[i] for i, feat in enumerate(self.feature_names)},
            'current_prediction': current_pred,
            'target_prediction': target_value,
            'recommended_prediction': new_pred,
            'improvement_percent': (current_pred - new_pred) / current_pred * 100,
            'feasible': result.success
        }
        
        return recommendation


# ============================================================================
# PART 3: VISUALIZATION AND VALIDATION
# ============================================================================

def plot_shap_summary(shap_values, features, feature_names, title="SHAP Feature Importance"):
    """Create SHAP summary plot"""
    plt.figure(figsize=(10, 6))
    shap.summary_plot(shap_values, features, feature_names=feature_names, show=False)
    plt.title(title)
    plt.tight_layout()
    plt.show()

def plot_shap_waterfall(explanation, target_name, figsize=(10, 4)):
    """Create waterfall plot for local explanation"""
    plt.figure(figsize=figsize)
    
    shap_values = explanation['shap_values']
    feature_values = explanation['feature_values']
    base_value = explanation['base_value']
    prediction = explanation['prediction']
    feature_names = explanation['feature_names']
    
    # Create waterfall values
    contributions = []
    for name, shap_val, feat_val in zip(feature_names, shap_values, feature_values):
        contributions.append({
            'feature': name,
            'shap_value': shap_val,
            'value': feat_val
        })
    
    # Sort by absolute SHAP value
    contributions.sort(key=lambda x: abs(x['shap_value']), reverse=True)
    
    # Plot
    y_pos = range(len(contributions))
    shap_vals = [c['shap_value'] for c in contributions]
    colors = ['red' if v > 0 else 'green' for v in shap_vals]
    
    plt.barh(y_pos, shap_vals, color=colors, alpha=0.7)
    plt.yticks(y_pos, [f"{c['feature']} ({c['value']:.1f})" for c in contributions])
    plt.axvline(x=0, color='black', linestyle='-', linewidth=0.5)
    plt.xlabel(f"SHAP Value (impact on {target_name})")
    plt.title(f"Local Explanation: {target_name}\nBase: {base_value:.2f} → Prediction: {prediction:.2f}")
    plt.tight_layout()
    plt.show()

def plot_predictions_vs_actual(y_true, y_pred, target_name):
    """Scatter plot of predictions vs actual values"""
    plt.figure(figsize=(8, 6))
    plt.scatter(y_true, y_pred, alpha=0.5, edgecolors='k', linewidth=0.5)
    
    # Add perfect prediction line
    min_val = min(y_true.min(), y_pred.min())
    max_val = max(y_true.max(), y_pred.max())
    plt.plot([min_val, max_val], [min_val, max_val], 'r--', lw=2, label='Perfect prediction')
    
    plt.xlabel(f'Actual {target_name}')
    plt.ylabel(f'Predicted {target_name}')
    plt.title(f'Predictions vs Actual: {target_name}')
    plt.legend()
    plt.tight_layout()
    plt.show()

def plot_counterfactual_comparison(recommendation, controllable_features=None):
    """Visualize counterfactual recommendations"""
    if controllable_features is None:
        controllable_features = ['wire_speed', 'desc_speed', 'wire_tension', 'coolant_flow']
    
    current = recommendation['current_parameters']
    recommended = recommendation['recommended_parameters']
    changes = recommendation['changes']
    
    # Filter to controllable features
    current_filtered = {k: v for k, v in current.items() if k in controllable_features}
    recommended_filtered = {k: v for k, v in recommended.items() if k in controllable_features}
    
    fig, axes = plt.subplots(1, 2, figsize=(12, 5))
    
    # Bar chart of changes
    features = list(current_filtered.keys())
    current_vals = [current_filtered[f] for f in features]
    recommended_vals = [recommended_filtered[f] for f in features]
    
    x = np.arange(len(features))
    width = 0.35
    
    axes[0].bar(x - width/2, current_vals, width, label='Current', alpha=0.7, color='red')
    axes[0].bar(x + width/2, recommended_vals, width, label='Recommended', alpha=0.7, color='green')
    axes[0].set_xlabel('Parameters')
    axes[0].set_ylabel('Value')
    axes[0].set_title('Parameter Changes')
    axes[0].set_xticks(x)
    axes[0].set_xticklabels(features, rotation=45)
    axes[0].legend()
    
    # Prediction comparison
    metrics = ['Current', 'Target', 'Recommended']
    values = [
        recommendation['current_prediction'],
        recommendation['target_prediction'],
        recommendation['recommended_prediction']
    ]
    colors = ['red', 'orange', 'green']
    
    axes[1].bar(metrics, values, color=colors, alpha=0.7)
    axes[1].set_ylabel('Specific Energy (kW·h/m²)')
    axes[1].set_title(f"Prediction Improvement: {recommendation['improvement_percent']:.1f}% reduction")
    
    # Add value labels on bars
    for i, v in enumerate(values):
        axes[1].text(i, v + 0.2, f'{v:.1f}', ha='center')
    
    plt.tight_layout()
    plt.show()
    
    # Print recommendation summary
    print("\n" + "="*60)
    print("COUNTERFACTUAL RECOMMENDATION SUMMARY")
    print("="*60)
    print(f"Current prediction: {recommendation['current_prediction']:.2f} kW·h/m²")
    print(f"Target prediction: {recommendation['target_prediction']:.2f} kW·h/m² ({recommendation['improvement_percent']:.1f}% reduction)")
    print(f"Recommended prediction: {recommendation['recommended_prediction']:.2f} kW·h/m²")
    print("\nRecommended changes:")
    for feat, change in changes.items():
        if feat in controllable_features and abs(change) > 0.01:
            direction = "↑" if change > 0 else "↓"
            print(f"  {direction} {feat}: {current[feat]:.1f} → {recommended[feat]:.1f} ({change:+.1f})")
    print("="*60)


# ============================================================================
# PART 4: MAIN EXECUTION
# ============================================================================

def main():
    """Run complete XAI simulation and validation"""
    
    print("="*70)
    print("MARBLE PROCESSING XAI FRAMEWORK - SIMULATION")
    print("Based on: Yilmazkaya & Ozcelik (2016) + XAI methodology")
    print("="*70)
    
    # ------------------------------------------------------------------------
    # Step 1: Generate synthetic data
    # ------------------------------------------------------------------------
    print("\n[1/6] Generating synthetic marble cutting data...")
    generator = MarbleDataGenerator(n_samples=2000)  # Exceeds SME minimum (500-1000)
    df = generator.generate()
    print(f"    Generated {len(df)} samples with {len(df.columns)} features/targets")
    print(f"    Features: {[c for c in df.columns if c not in ['specific_energy', 'wire_wear', 'surface_quality']]}")
    print(f"    Targets: specific_energy, wire_wear, surface_quality")
    
    # Display summary statistics
    print("\n    Target Statistics:")
    for target in ['specific_energy', 'wire_wear', 'surface_quality']:
        print(f"      {target}: mean={df[target].mean():.2f}, std={df[target].std():.2f}, "
              f"min={df[target].min():.2f}, max={df[target].max():.2f}")
    
    # ------------------------------------------------------------------------
    # Step 2: Prepare features and targets
    # ------------------------------------------------------------------------
    print("\n[2/6] Preparing features and targets...")
    feature_cols = [c for c in df.columns if c not in ['specific_energy', 'wire_wear', 'surface_quality']]
    target_cols = ['specific_energy', 'wire_wear', 'surface_quality']
    
    X = df[feature_cols]
    y_dict = {target: df[target] for target in target_cols}
    
    print(f"    Feature matrix shape: {X.shape}")
    print(f"    Features: {feature_cols}")
    
    # ------------------------------------------------------------------------
    # Step 3: Train XAI models
    # ------------------------------------------------------------------------
    print("\n[3/6] Training XGBoost models with SHAP explainability...")
    xai = MarbleXAI(feature_names=feature_cols, target_names=target_cols)
    xai.train(X, y_dict, verbose=True)
    
    # ------------------------------------------------------------------------
    # Step 4: Model evaluation (Figure 3-style plots)
    # ------------------------------------------------------------------------
    print("\n[4/6] Evaluating model performance...")
    
    # Get predictions on test set
    X_scaled = xai.scaler.transform(xai.X_test)
    for target_name in target_cols:
        y_true = xai.y_test_dict[target_name]
        y_pred = xai.models[target_name].predict(X_scaled)
        
        mae = mean_absolute_error(y_true, y_pred)
        rmse = np.sqrt(mean_squared_error(y_true, y_pred))
        r2 = r2_score(y_true, y_pred)
        
        print(f"\n    {target_name.upper()}:")
        print(f"      MAE: {mae:.3f}")
        print(f"      RMSE: {rmse:.3f}")
        print(f"      R²: {r2:.3f}")
        
        # Plot predictions vs actual
        plot_predictions_vs_actual(y_true, y_pred, target_name)
    
    # ------------------------------------------------------------------------
    # Step 5: SHAP Global Explanations (Figure 4-style)
    # ------------------------------------------------------------------------
    print("\n[5/6] Generating SHAP global explanations...")
    
    # Calculate SHAP values for energy model
    shap_values_energy = xai.explainers['specific_energy'].shap_values(X_scaled)
    
    # Plot SHAP summary (feature importance)
    plt.figure(figsize=(10, 6))
    shap.summary_plot(shap_values_energy, X_scaled, feature_names=feature_cols, show=False)
    plt.title("SHAP Feature Importance - Specific Energy Prediction")
    plt.tight_layout()
    plt.show()
    
    # SHAP dependence plot for top feature
    # Find top feature by mean |SHAP|
    mean_shap = np.abs(shap_values_energy).mean(axis=0)
    top_feature_idx = np.argmax(mean_shap)
    top_feature_name = feature_cols[top_feature_idx]
    
    plt.figure(figsize=(8, 5))
    shap.dependence_plot(top_feature_idx, shap_values_energy, X_scaled, 
                         feature_names=feature_cols, show=False)
    plt.title(f"SHAP Dependence: {top_feature_name} → Specific Energy")
    plt.tight_layout()
    plt.show()
    
    # ------------------------------------------------------------------------
    # Step 6: Local Explanation (Figure 5-style - Anomaly detection)
    # ------------------------------------------------------------------------
    print("\n[6/6] Generating local explanations (anomaly detection)...")
    
    # Find a high-energy anomaly (top 5% energy)
    energy_preds = xai.models['specific_energy'].predict(X_scaled)
    threshold = np.percentile(energy_preds, 95)
    anomaly_indices = np.where(energy_preds > threshold)[0]
    
    if len(anomaly_indices) > 0:
        anomaly_idx = anomaly_indices[0]
        print(f"    Found anomaly: Instance #{anomaly_idx} with predicted energy = {energy_preds[anomaly_idx]:.2f} kW·h/m²")
        
        # Get local explanation
        local_exp = xai.explain_local('specific_energy', anomaly_idx, X_scaled)
        
        # Print operator-facing explanation
        print("\n    OPERATOR-FACING EXPLANATION:")
        print("    " + "-"*50)
        print(f"    ⚠ ALERT: High energy consumption detected ({local_exp['prediction']:.1f} kW·h/m²)")
        print("    CONTRIBUTION ANALYSIS:")
        
        # Sort contributions by absolute SHAP
        contributions = list(zip(feature_cols, local_exp['shap_values'], 
                                 xai.scaler.inverse_transform([local_exp['feature_values']])[0]))
        contributions.sort(key=lambda x: abs(x[1]), reverse=True)
        
        for feat, shap_val, orig_val in contributions[:5]:
            if abs(shap_val) > 0.1:
                direction = "↑" if shap_val > 0 else "↓"
                print(f"      {direction} {feat}: {orig_val:.1f} (contribution: {shap_val:+.1f})")
        
        print("    " + "-"*50)
        print(f"    RECOMMENDATION: Consider reducing descending speed for this marble type.")
        
        # Plot waterfall
        plot_shap_waterfall(local_exp, 'Specific Energy (kW·h/m²)')
    
    # ------------------------------------------------------------------------
    # Step 7: Counterfactual Optimization (Table 9-style)
    # ------------------------------------------------------------------------
    print("\n[7/6] Generating counterfactual recommendations...")
    
    # Use a random instance from the dataset
    sample_idx = 100
    sample_X = X.iloc[sample_idx:sample_idx+1]
    sample_energy = df['specific_energy'].iloc[sample_idx]
    
    print(f"    Original instance #{sample_idx}: Energy = {sample_energy:.2f} kW·h/m²")
    
    # Generate counterfactual
    counterfactual = xai.generate_counterfactual(
        'specific_energy', 
        sample_X, 
        target_reduction=0.20,  # 20% reduction target
        feature_bounds={
            'wire_speed': (25, 40),
            'desc_speed': (10, 60),
            'wire_tension': (1200, 1800),
            'coolant_flow': (5, 15),
        }
    )
    
    # Visualize
    plot_counterfactual_comparison(counterfactual)
    
    # ------------------------------------------------------------------------
    # Summary Report
    # ------------------------------------------------------------------------
    print("\n" + "="*70)
    print("SIMULATION SUMMARY - XAI Framework Validation")
    print("="*70)
    print(f"Dataset size: {len(df)} samples (exceeds SME minimum of 500-1000)")
    print(f"Features: {len(feature_cols)} parameters")
    print(f"Models: 3 XGBoost regressors (energy, wear, surface quality)")
    print(f"Explainability: SHAP TreeExplainer (global + local)")
    print(f"Counterfactuals: DiCE-inspired optimization")
    print("\nKey findings:")
    print(f"  ✓ Energy prediction R² > 0.90 achieved? {r2_score(xai.y_test_dict['specific_energy'], xai.models['specific_energy'].predict(X_scaled)):.3f}")
    print(f"  ✓ Local explanations generated for anomaly detection")
    print(f"  ✓ Actionable counterfactuals with {counterfactual['improvement_percent']:.1f}% predicted improvement")
    print("\nNext steps for industry pilot:")
    print("  1. Deploy sensor suite ($1,000-1,500 per machine)")
    print("  2. Collect 500-1,000 cutting events (1-3 months)")
    print("  3. Retrain XGBoost models on plant-specific data")
    print("  4. Conduct A/B test (baseline vs XAI recommendations)")
    print("  5. Measure operator trust (Likert scale > 3.5/5)")
    print("="*70)
    
    return xai, df, counterfactual


if __name__ == "__main__":
    xai_model, data, cf_recommendation = main()
    

