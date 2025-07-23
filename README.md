# Vehicle Routing Problem (VRP) Optimization with Heuristics and Gurobi

This project tackles a real-world delivery routing challenge with 38 customers and a homogeneous vehicle fleet using both heuristics and Gurobi optimization.

## 🧠 Problem

- Depot (node 0) and 38 customers
- Vehicle capacity: 85 units
- Objective: Minimize total distance
- Constraints: Vehicle capacity, route feasibility, all customers visited

## 🧰 Algorithms Applied

### Part A - Cluster First, Route Second (CFRS)
- Clustering: K-means
- Routing: Nearest Neighbor
- Improvements: 2-opt, Relocation

### Part B - Route First, Cluster Second (RFCS)
- Routing: Christofides, Nearest Neighbor
- Improvements: Relocation, 2-opt

### Part C - Gurobi Solver
- Mathematical model implemented with MTZ constraints
- Solved for 15 minutes using Gurobi

## 📈 Results Summary

| Method                       | Cost          | % from Gurobi | Time (s) |
|-----------------------------|---------------|----------------|----------|
| Gurobi Optimal              | 86.5M         | 0%             | 900.0    |
| RFCS + NN + 2-opt           | 100.9M        | 14.3%          | 0.0039   |
| CFRS + NN + Relocation      | 106.2M        | 18.6%          | 0.4284   |

## ✅ Best Trade-off Solution
**RFCS + Nearest Neighbor + 2-opt**
- Closest to optimal (14.3%)
- Fastest runtime (~4 milliseconds)

## 🔍 Verification
Implemented a custom function to:
- Check if all customers are visited once
- Ensure depot is both start and end point
- Validate no vehicle exceeds capacity

## 📦 Requirements
```bash
pip install -r requirements.txt
