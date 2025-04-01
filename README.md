# **Python YAML Use Case**

## **Introduction**
This project demonstrates how to use Python to read and manipulate data stored in a YAML file. It loads student information from a YAML file and provides functionality to display and filter students based on GPA.

---

## **Step-by-Step Guide**

### **Step 1: Install Required Packages**
To handle YAML files in Python, install the **PyYAML** library using:
```sh
pip install pyyaml
```

### **Step 2: Create the YAML File**
Create a YAML file named `students.yaml` with the following structure:
```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

#### **YAML Structure Explanation:**
- **`students`**: A list of student dictionaries.
- Each student has attributes:
  - **`name`**: The student's name.
  - **`age`**: The student's age.
  - **`major`**: The student's field of study.
  - **`gpa`**: The student's Grade Point Average.

---

### **Step 3: Write the Python Application**
Create a new Python file named `app.py` and add the following code:
```python
import yaml

def load_data(file_path):
    """
    Load data from a YAML file.
    :param file_path: Path to the YAML file.
    :return: Data loaded from the YAML file.
    """
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    """
    Display information about all students.
    :param students: List of student dictionaries.
    """
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """
    Filter and display students with a GPA above the specified minimum.
    :param students: List of student dictionaries.
    :param min_gpa: Minimum GPA for filtering.
    """
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    # Load the data from the YAML file
    data = load_data('students.yaml')
    students = data['students']
    
    # Display all students
    display_students(students)
    
    # Filter students by GPA
    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
```

---

### **Code Explanation**
1. **Importing the Library:**
   ```python
   import yaml
   ```
   - Imports the **PyYAML** library for handling YAML files.

2. **Loading Data:**
   ```python
   def load_data(file_path):
       with open(file_path, 'r') as file:
           data = yaml.safe_load(file)
       return data
   ```
   - Reads the YAML file and converts its content into a Python dictionary.

3. **Displaying Students:**
   ```python
   def display_students(students):
   ```
   - Prints student details from the YAML file.

4. **Filtering Students by GPA:**
   ```python
   def filter_students_by_gpa(students, min_gpa):
   ```
   - Filters students based on a minimum GPA input by the user.

5. **Main Function:**
   ```python
   def main():
   ```
   - Loads data, displays students, and allows filtering.

6. **Execution Block:**
   ```python
   if __name__ == "__main__":
       main()
   ```
   - Ensures the script runs only when executed directly.

---

### **Step 4: Run the Application**
1. Ensure `app.py` and `students.yaml` are in the same directory.
2. Open the terminal and run:
   ```sh
   python app.py
   ```

### **Expected Output**
```sh
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6
Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

---

## **Conclusion**
This project demonstrates a practical example of using Python with YAML to manage structured data. Potential enhancements include:
- **Sorting students by GPA or major**
- **Adding student records dynamically**
- **Saving modifications back to the YAML file**

🚀 **Happy Coding!** 🚀

