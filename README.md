# Market Equilibrium and Price Elasticity of Demand

This Jupyter Notebook demonstrates how to find the **market equilibrium price and quantity** and calculate the **price elasticity of demand** at the equilibrium point using Python. The code uses the `numpy`, `matplotlib`, and `scipy` libraries to model and visualize the demand and supply curves, solve for the equilibrium, and compute the elasticity.

---

## Problem Statement

Given:
- **Demand Function**: \( Q_d = 100 - 2P \)
  - \( Q_d \) = Quantity demanded
  - \( P \) = Price
- **Supply Function**: \( Q_s = 20 + 3P \)
  - \( Q_s \) = Quantity supplied

We want to:
1. Find the **equilibrium price** and **equilibrium quantity** where \( Q_d = Q_s \).
2. Calculate the **price elasticity of demand** at the equilibrium point.
3. Visualize the demand and supply curves with the equilibrium point marked.

---

## Code Implementation

### Step 1: Import Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import fsolve
```

---

### Step 2: Define Demand and Supply Functions

```python
# Demand function: Qd = 100 - 2P
def demand_function(price):
    return 100 - 2 * price

# Supply function: Qs = 20 + 3P
def supply_function(price):
    return 20 + 3 * price
```

---

### Step 3: Find the Equilibrium Price and Quantity

The equilibrium occurs where the demand equals the supply (\( Q_d = Q_s \)). We use `fsolve` from `scipy.optimize` to solve for the equilibrium price.

```python
# Function to find equilibrium (where Qd = Qs)
def find_equilibrium(price):
    return demand_function(price) - supply_function(price)

# Solve for equilibrium price
equilibrium_price = fsolve(find_equilibrium, 10)[0]  # Initial guess of 10
equilibrium_quantity = demand_function(equilibrium_price)

print(f"Equilibrium Price: {equilibrium_price:.2f}")
print(f"Equilibrium Quantity: {equilibrium_quantity:.2f}")
```

**Output:**
```
Equilibrium Price: 16.00
Equilibrium Quantity: 68.00
```

---

### Step 4: Calculate Price Elasticity of Demand

The price elasticity of demand measures how sensitive the quantity demanded is to a change in price. It is calculated as:
\[
\text{Elasticity} = \left(\frac{dQ}{dP}\right) \times \left(\frac{P}{Q}\right)
\]

```python
# Calculate price elasticity of demand
def price_elasticity_of_demand(price, quantity):
    dQ_dP = -2  # Derivative of the demand function with respect to price
    return dQ_dP * (price / quantity)

elasticity = price_elasticity_of_demand(equilibrium_price, equilibrium_quantity)
print(f"Price Elasticity of Demand at Equilibrium: {elasticity:.2f}")
```

**Output:**
```
Price Elasticity of Demand at Equilibrium: -0.47
```

---

### Step 5: Visualize Demand and Supply Curves

We plot the demand and supply curves and mark the equilibrium point.

```python
# Generate price range for plotting
prices = np.linspace(0, 50, 100)
demand_curve = demand_function(prices)
supply_curve = supply_function(prices)

# Plot the curves
plt.figure(figsize=(10, 6))
plt.plot(prices, demand_curve, label='Demand Curve (Qd = 100 - 2P)', color='blue')
plt.plot(prices, supply_curve, label='Supply Curve (Qs = 20 + 3P)', color='red')
plt.axvline(x=equilibrium_price, color='gray', linestyle='--', label=f'Equilibrium Price: {equilibrium_price:.2f}')
plt.axhline(y=equilibrium_quantity, color='green', linestyle='--', label=f'Equilibrium Quantity: {equilibrium_quantity:.2f}')
plt.scatter(equilibrium_price, equilibrium_quantity, color='black', zorder=5)
plt.title('Market Equilibrium')
plt.xlabel('Price (P)')
plt.ylabel('Quantity (Q)')
plt.legend()
plt.grid(True)
plt.show()
```

**Output:**
- A graph showing the demand and supply curves with the equilibrium point marked.

---

## Explanation of Results

### 1. **Equilibrium Price: 16.00**
- This is the price at which the quantity demanded equals the quantity supplied.
- Calculated by solving \( Q_d = Q_s \):
  \[
  100 - 2P = 20 + 3P
  \]
  \[
  P = 16
  \]

### 2. **Equilibrium Quantity: 68.00**
- This is the quantity of goods bought and sold at the equilibrium price.
- Calculated using the demand function:
  \[
  Q_d = 100 - 2(16) = 68
  \]

### 3. **Price Elasticity of Demand: -0.47**
- Measures how sensitive the quantity demanded is to a change in price.
- Calculated as:
  \[
  \text{Elasticity} = \left(\frac{dQ}{dP}\right) \times \left(\frac{P}{Q}\right)
  \]
  \[
  \text{Elasticity} = (-2) \times \left(\frac{16}{68}\right) = -0.47
  \]
- The negative sign indicates an inverse relationship between price and quantity demanded.
- Since the absolute value is less than 1, demand is **inelastic** at the equilibrium point.

---

## How to Use Google Copilot

Google Copilot (or GitHub Copilot) can assist you in writing and improving this code. Here's how you can use it:

1. **Code Suggestions**:
   - As you type, Copilot will suggest code snippets. For example, when defining the demand and supply functions, Copilot might suggest the correct formula based on the problem statement.

2. **Documentation**:
   - Copilot can help generate comments and explanations for your code. For example, it can automatically add comments to explain the equilibrium calculation or the elasticity formula.

3. **Error Fixing**:
   - If you encounter errors, Copilot can suggest fixes. For example, if you forget to import a library, Copilot will prompt you to add it.

4. **Visualization**:
   - Copilot can help you customize the plot by suggesting additional features like labels, titles, or gridlines.

---

## How to Run This Notebook

1. **Prerequisites**:
   - Install Python 3.x.
   - Install Jupyter Notebook:
     ```bash
     pip install notebook
     ```
   - Install the required libraries:
     ```bash
     pip install numpy matplotlib scipy
     ```

2. **Run the Notebook**:
   - Open a terminal or command prompt.
   - Navigate to the directory where the notebook is located.
   - Start Jupyter Notebook:
     ```bash
     jupyter notebook
     ```
   - Open the `.ipynb` file and run the cells.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to contribute or report issues! 😊

---

### Folder Structure for GitHub
```
market-equilibrium/
│
├── market_equilibrium.ipynb   # Jupyter Notebook
├── README.md                  # Documentation (optional)
└── LICENSE                    # License file (optional)
```

You can now upload this to GitHub as a repository, and the Jupyter Notebook will serve as the interactive documentation for your project. With Copilot, you can further enhance the code and documentation! 🚀
