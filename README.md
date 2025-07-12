# Sports-Club-Management-System
# 🏆 Sports Club Management System

![C++](https://img.shields.io/badge/C++-17-blue?logo=c%2B%2B)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

A feature-rich **Sports Club Management System** developed in **C++17**, implementing clean **Object-Oriented Programming (OOP)** practices. This system streamlines management of club members, instructors, and administrative functions through a modular, secure, and scalable console-based interface.

---

## 🚀 Overview

This project simulates the operations of a sports or fitness club. It allows:

- 🔐 User registration and login with input-masked passwords
- 🧑‍🏫 Instructor management with schedules
- 🧑‍💼 Admin dashboard to view, update, and manage the entire system
- 🤖 A virtual fitness assistant that gives health recommendations
- 📊 Membership statistics and reporting features
- 🔄 Efficient use of C++ features like **classes, inheritance, polymorphism, encapsulation**, and **file handling**

---

## 🎯 Key Features

### 👤 Member Module
- Sign up / Sign in
- View and update profile
- Access fitness recommendations

### 🧑‍🏫 Instructor Module
- Schedule training sessions
- Assign members
- View availability

### 🛠️ Admin Module
- Full system access
- Add/delete instructors and users
- Generate activity reports
- Analyze membership data

### 🔐 Security
- Masked password input using `getch()`
- Role-based access (User, Instructor, Admin)

---

## 💻 Technologies Used

- **C++17**
- **OOP Principles**: Encapsulation, Inheritance, Polymorphism
- **File Handling**: Persistent user data via `.txt` files
- **Standard Library**: `fstream`, `iostream`, `vector`, `map`, etc.

---

## 🧱 Project Structure
SportsClubManagementSystem/
├── include/ # Header files (class declarations)
├── src/ # Source files (class definitions)
├── data/ # Stored data files (users, instructors, sessions)
├── main.cpp # Application entry point
├── CMakeLists.txt # CMake build configuration
├── .gitignore
├── LICENSE
└── README.md


## 📋 Requirements

- C++17 compatible compiler (e.g., `g++`, `MSVC`)
- CMake 3.15 or higher
- Windows OS (due to `strcpy_s` and `getch()` compatibility)

---

## ⚙️ Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/SportsClubManagementSystem.git
cd SportsClubManagementSystem

# Create a build directory
mkdir build && cd build

# Generate and build
cmake ..
cmake --build .
▶️ Running the Program

./SportsClubManagementSystem
The program will launch a terminal-based interface allowing access to user, instructor, and admin modules.

 📈 Future Enhancements
GUI version using Qt or ImGui

Database integration (SQLite or MySQL)

Encrypted login and authentication

REST API for mobile app support

Automated unit tests with Catch2

📄 License
This project is licensed under the MIT License.
See the LICENSE file for more information.

🙋‍♂️ Author
Muhammad Ozair Khalid
Cybersecurity 2nd semester 

Developed as a capstone project for an Object-Oriented Programming (OOP) course, demonstrating real-world application of C++ design patterns, encapsulation, inheritance, and polymorphis

