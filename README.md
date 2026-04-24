# MongoDB & Jupyter Notebook Integration – Student Data Management

This repository demonstrates how to connect **MongoDB** (Atlas or local) with a **Jupyter Notebook** to perform **CRUD operations** on student data.  
The notebook `mongodb_for_all.ipynb` contains all the code to insert, list, update, and delete student records using **PyMongo**.

## 📌 Overview

- **MongoDB**: NoSQL database used to store student information (name, age, career).
- **Jupyter Notebook**: Interactive Python environment that connects to MongoDB and executes database operations.
- **PyMongo**: Official MongoDB driver for Python.

The goal is to provide a simple, reusable template for anyone who wants to learn how to integrate MongoDB with Python notebooks, especially for managing small datasets like student lists.

## 🧰 Prerequisites

Before using the notebook, make sure you have:

- **Python 3.7+** installed
- **MongoDB** – either:
  - A local MongoDB instance (download from [MongoDB Community Server](https://www.mongodb.com/try/download/community))
  - A cloud cluster on [MongoDB Atlas](https://www.mongodb.com/atlas) (free tier available)
- **Jupyter Notebook** (or JupyterLab / Google Colab)
- Required Python libraries: `pymongo`, `dnspython` (for Atlas)

## ⚙️ Setup

### 1. Clone the repository

```bash
git clone https://github.com/JojjjT/COFFE.git
cd COFFE
```

2. Install dependencies

```bash
pip install pymongo dnspython jupyter
```

3. Configure MongoDB connection

Option A: Use MongoDB Atlas (cloud)

1. Create a cluster on MongoDB Atlas.
2. Under Database Access, create a database user with read/write permissions.
3. Under Network Access, add your IP address (or allow access from anywhere for testing).
4. Get your connection string (e.g., mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/).
5. Open mongodb_for_all.ipynb and replace the connection string in this line:

```python
cliente = MongoClient("mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/")
```

Option B: Use local MongoDB

1. Start MongoDB locally (usually on localhost:27017).
2. In the notebook, replace the connection line with:

```python
cliente = MongoClient("mongodb://localhost:27017/")
```

4. Launch the notebook

```bash
jupyter notebook mongodb_for_all.ipynb
```

If using Google Colab, upload the notebook and run the cells.

📓 Notebook Content & Functions

The notebook defines four basic CRUD functions:

Function Description
insertar_estudiante(nombre, edad, carrera) Inserts a new student document.
listar_estudiantes() Displays all students in the collection.
actualizar_edad(nombre, nueva_edad) Updates the age of a specific student.
eliminar_estudiante(nombre) Deletes a student by name.

After defining the functions, the notebook suggests creating an interactive menu using input() to let users choose operations. You can extend the notebook by adding a loop like:

```python
while True:
    print("\n--- MENÚ DE ESTUDIANTES ---")
    print("1. Insertar estudiante")
    print("2. Listar estudiantes")
    print("3. Actualizar edad")
    print("4. Eliminar estudiante")
    print("5. Salir")
    opcion = input("Seleccione una opción: ")
    
    if opcion == "1":
        nombre = input("Nombre: ")
        edad = int(input("Edad: "))
        carrera = input("Carrera: ")
        insertar_estudiante(nombre, edad, carrera)
    elif opcion == "2":
        listar_estudiantes()
    # ... (complete for other options)
```

🚀 Usage Example

After running the notebook cells, you can manually call the functions:

```python
insertar_estudiante("Ana López", 22, "Ingeniería de Sistemas")
listar_estudiantes()
actualizar_edad("Ana López", 23)
eliminar_estudiante("Ana López")
```

All changes are persisted in the MongoDB database. You can also verify them using MongoDB Compass or the Atlas web UI.

📁 Repository Structure

```
.
├── mongodb_for_all.ipynb   # Main Jupyter notebook with CRUD functions
├── README.md               # This file
└── requirements.txt        # (Optional) List of dependencies
```

🔧 Customization

· Add more fields – Modify the document structure to include email, grades, semester, etc.
· Add error handling – Wrap database operations in try/except blocks.
· Use pandas – Load query results into a DataFrame for analysis.
· Switch to async – Use motor for asynchronous operations (advanced).

❗ Troubleshooting

DNS error when connecting to Atlas

If you see:

```
ConfigurationError: The DNS query name does not exist: _mongodb._tcp.cluster1.xxxxx.mongodb.net.
```

Solution:

· Verify your connection string is exactly as provided by Atlas (including the +srv part).
· Check that your cluster name is correct (e.g., cluster0 not cluster1).
· Make sure you have installed dnspython: pip install dnspython.
· If using Google Colab, restart the runtime after installing packages.

Authentication failed

· Ensure the username and password in the connection string are URL‑encoded (special characters like @, #, % must be percent-encoded).
· Verify that the database user has the correct permissions (at least readWrite on the target database).

Cannot connect to local MongoDB

· Start the MongoDB service: sudo systemctl start mongod (Linux) or run mongod in a terminal.
· Check that no firewall is blocking port 27017.

🤝 Contributing

Feel free to open issues or submit pull requests to improve the notebook or documentation.
Possible enhancements:

· Add a data visualization section.
· Implement aggregation queries (e.g., average age per career).
· Add support for exporting data to CSV/JSON.

📄 License

This project is licensed under the MIT License – see the LICENSE file for details.
