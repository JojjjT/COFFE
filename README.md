# Student Data Management with MongoDB & Jupyter Notebook

This repository demonstrates how to connect **MongoDB** with a **Jupyter Notebook** (`.ipynb`) to store, manage, and analyze a list of student data. It serves as a practical example of integrating a NoSQL database with an interactive Python environment for data processing and visualization.

## 📌 Overview

The project consists of:

- A **MongoDB** database that holds student records (e.g., name, age, grades, courses).
- A **Jupyter Notebook** that:

  - Connects to the MongoDB instance.
  - Performs CRUD operations (Insert, Query, Update, Delete).
  - Analyzes the data using **pandas** and **matplotlib**.
  - Visualizes trends (e.g., grade distributions, average scores).

This setup is ideal for educators, data analysts, or developers looking to learn how to bridge MongoDB with interactive Python notebooks.

## 🧰 Prerequisites

Before running the notebook, ensure you have the following installed:

- **Python** 3.7+
- **MongoDB** (local installation or cloud instance like [MongoDB Atlas](https://www.mongodb.com/atlas))
- **Jupyter** (via `pip install jupyter` or using Anaconda)
- Required Python libraries (see [`requirements.txt`](requirements.txt) if provided):

  ```bash
  pip install pymongo pandas matplotlib jupyter