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

## Steps to Run GitHub Code in Google Colab

### 1. **Upload the Code to GitHub**
   - First, ensure your code (e.g., the Jupyter Notebook `.ipynb` file) is uploaded to a GitHub repository.
   - For example, you can create a repository called `market-equilibrium` and upload the `market_equilibrium.ipynb` file.

---

### 2. **Open Google Colab**
   - Go to [Google Colab](https://colab.research.google.com/).
   - Sign in with your Google account if you haven't already.

---

### 3. **Load the Notebook from GitHub**
   - In Google Colab, click on **File** > **Open Notebook**.
   - Go to the **GitHub** tab.
   - Enter the URL of your GitHub repository (e.g., `https://github.com/your-username/market-equilibrium`).
   - Colab will list all the `.ipynb` files in the repository. Click on the one you want to open (e.g., `market_equilibrium.ipynb`).

---

### 4. **Run the Notebook**
   - Once the notebook is open, you can run each cell by clicking the **Play** button or pressing **Shift + Enter**.
   - If the notebook requires additional libraries (e.g., `numpy`, `matplotlib`, `scipy`), you can install them directly in Colab using `!pip install`.

   For example:
   ```python
   !pip install numpy matplotlib scipy
   ```

---

### 5. **Save a Copy to Google Drive (Optional)**
   - If you want to save your progress or make changes, you can save a copy of the notebook to your Google Drive.
   - Click **File** > **Save a copy in Drive**.

---

## Example: Running the Market Equilibrium Code in Colab

Here’s how you can directly load and run the `market_equilibrium.ipynb` file from GitHub in Colab:

### Step 1: Open Colab and Load the Notebook
1. Go to [Google Colab](https://colab.research.google.com/).
2. Click on **File** > **Open Notebook**.
3. Go to the **GitHub** tab.
4. Enter the URL of your GitHub repository (e.g., `https://github.com/your-username/market-equilibrium`).
5. Select the `market_equilibrium.ipynb` file.

---

### Step 2: Install Required Libraries
If the notebook requires libraries like `numpy`, `matplotlib`, or `scipy`, run the following command in a Colab cell:
```python
!pip install numpy matplotlib scipy
```

---

### Step 3: Run the Notebook
- Run each cell in the notebook sequentially by clicking the **Play** button or pressing **Shift + Enter**.
- The notebook will calculate the equilibrium price and quantity, compute the price elasticity of demand, and plot the demand and supply curves.

---

### Step 4: Save Your Work (Optional)
- If you make changes to the notebook, you can save it to your Google Drive by clicking **File** > **Save a copy in Drive**.

---

## Alternative: Directly Open a GitHub Notebook in Colab

If you want to open a GitHub notebook directly in Colab without going through the Colab interface, you can use the following URL format:
```
https://colab.research.google.com/github/<username>/<repository>/blob/<branch>/<path-to-notebook>
```

For example:
```
https://colab.research.google.com/github/your-username/market-equilibrium/blob/main/market_equilibrium.ipynb
```

Just replace:
- `your-username` with your GitHub username.
- `market-equilibrium` with your repository name.
- `main` with the branch name (if different).
- `market_equilibrium.ipynb` with the path to your notebook file.

---
