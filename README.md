# Hierarchical Task Management System

A Java desktop application for assigning tasks to employees, where tasks can be nested into hierarchies of any depth. Built with the **Composite design pattern** and a Swing GUI.

## Tech Stack
- **Language:** Java (Maven)
- **GUI:** Java Swing (`JTabbedPane`, `JTable`)
- **Persistence:** Java Object Serialization
- **Key concepts:** Composite pattern, sealed classes, polymorphism, recursion

## Features
- **Employee management:** add employees, with input validation using regular expressions.
- **Simple and complex tasks:** a simple task has a start and end hour; a complex task contains other tasks (simple or complex), forming a tree.
- **Task assignment:** assign tasks to employees and mark them as completed or uncompleted directly from the interface.
- **Work duration:** total working hours per employee are computed recursively, counting only completed tasks.
- **Reports:** employees with more than 40 completed work hours, sorted by duration, and the number of completed vs. uncompleted tasks per employee.
- **Persistence:** all data is serialized to a file on exit and loaded on startup.

## Design
- `Task` is a **sealed** abstract class that permits only `SimpleTask` and `ComplexTask`.
- `estimateDuration()` is polymorphic: a simple task returns its own duration, a complex task returns the sum of its subtasks (Composite pattern).
- Employees and their tasks are stored in a `Map<Employee, List<Task>>`.

## Architecture
```
src/main/java
├── data_model/                Task, SimpleTask, ComplexTask, Employee
├── business_logic/            TaskManagement, Utility (reports)
├── data_access/               Serialization
└── graphical_user_interface/  MainFrame
```
A UML class diagram is included (`DiagramDrawIO.drawio`).

## How to Run
**Prerequisites:** Java (JDK 25), Maven, IntelliJ IDEA (the GUI uses an IntelliJ `.form` file)

1. Clone the repository and open it as a Maven project in IntelliJ IDEA.
2. Run `graphical_user_interface.MainFrame`.
