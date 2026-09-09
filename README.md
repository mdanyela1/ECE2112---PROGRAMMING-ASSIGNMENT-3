# ECE2112---PROGRAMMING-ASSIGNMENT-3

EXP#3: Python Data Analysis (Pandas)

Name: Maria Daniela C. Sacaben
Section: 2ECE-A

Date Submitted: September 9, 2026

Overview
This repository contains the solution for Experiment 3: Python Data Analysis (Pandas). The objective of this activity is to demonstrate data manipulation techniques using the Python pandas library on the cars.csv dataset without modifying the underlying raw data.

Intended Learning Outcomes (ILOs)
Load a CSV dataset into a Pandas DataFrame.

Select rows and columns using positional (iloc) and label-based (loc / column indexing) methods.

Filter records dynamically using Boolean logic on DataFrame columns.

Extract well-defined data subsets while keeping the original DataFrame immutable.

Dataset Description
File Name: cars.csv

Contents: Contains vehicle specification metrics across standard automotive attributes (Model, mpg, cyl, hp, wt, gear, etc.).

Problem Breakdown & Code Structure
Part A: Positional and Label-Based Slicing
a. Dataset Properties: Displays cars.shape and cars.columns.

b. Positional Slicing: Extracts rows 6 through 10 (1-based index corresponding to zero-based index 5:10) using .iloc into cars_6_to_10.

c. Column Filtering: Subsets cars_6_to_10 to display only ['Model', 'mpg', 'cyl', 'hp', 'gear'] using explicit column labels.

Part B: Model Lookup
Uses Boolean indexing on the Model column without hardcoded integer indices.

a. Toyota Corolla: Filtered into variable toyota (all columns retained).

b. Pontiac Firebird: Filtered into variable pontiac (retaining Model, mpg, hp, wt).

Part C: Multi-Model Subsetting
Filters records where Model is in ['Datsun 710', 'Lotus Europa', 'Ferrari Dino'].

Restricts output columns to ['Model', 'mpg', 'cyl', 'hp', 'gear'].

Result stored in selected_cars.

Includes verification step ensuring selected_cars.shape equals (3, 5).

Quickstart Code snippet
Python
import pandas as pd

# Load Dataset
cars = pd.read_csv('cars.csv')

# --- Part A ---
print("Shape:", cars.shape)
print("Columns:", cars.columns.tolist())

# Rows 6 to 10 using iloc
cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10_subset = cars_6_to_10[['Model', 'mpg', 'cyl', 'hp', 'gear']]
display(cars_6_to_10_subset)

# --- Part B ---
toyota = cars[cars['Model'] == 'Toyota Corolla']
pontiac = cars[cars['Model'] == 'Pontiac Firebird'][['Model', 'mpg', 'hp', 'wt']]
display(toyota)
display(pontiac)

# --- Part C ---
target_models = ['Datsun 710', 'Lotus Europa', 'Ferrari Dino']
target_cols = ['Model', 'mpg', 'cyl', 'hp', 'gear']

selected_cars = cars[cars['Model'].isin(target_models)][target_cols]
display(selected_cars)
print("Shape check:", selected_cars.shape)  # Expected: (3, 5)
Submission Checklist
[x] Executed .ipynb Jupyter Notebook.

[x] Student metadata (Name, Section, Date) included at the top.

[x] All outputs displayed in sequential executed cells.

[x] Zero hardcoded row indexes used for Boolean operations.

[x] Immutable source data (cars DataFrame untouched).
