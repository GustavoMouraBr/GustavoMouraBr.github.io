**TaskHive App Showcase**
# TaskHive – Multi-List Task Manager

TaskHive is a Java desktop application that helps you manage **multiple task lists** with due dates, priorities, and categories. It was built as a semester project for **COP 4331 – Object Oriented Software Engineering** at Florida Atlantic University.

> Tech stack: **Java 17, Swing GUI, MVC architecture, local file persistence.**

---

## What TaskHive Does

TaskHive was created for students and busy people who need several lists at once instead of one giant to-do list where things get easily lost. You can keep separate lists for:

- Personal goals (self-care, workouts, habits)
- Academic work (homework, projects, exams)
- Professional tasks (meetings, deliverables) 

Each list contains tasks with their own due dates and priorities.

### Core Features

-  **Create lists** with optional description, category, due date, and priority  
-  **Add tasks** to a list with:
  - name
  - description
  - due date (optional)
  - priority
-  **Delete tasks and lists**
-  **Due dates**
  - per task
  - optional due date for the whole list (such as a project deadline)
-  **Priority & color coding**
  - visual indicators for urgency
  - tasks can show **overdue/late/completed** states
-  **Search**
  - search lists and tasks by keywords
-  **Filter & sort**
  - filter by category, creation date, due date, or priority
  - sort by due date and urgency
-  **Local persistence**
  - data is saved to disk and re-loaded when you reopen the app

---

## App Showcase


<video controls width="800">
  <source src="https://github.com/user-attachments/assets/aad3f799-5a4e-4f1b-93fa-4face371b2ab" type="video/mp4">
  Your browser does not support the video tag.
</video>


### Dashboard – All Task Lists



> The dashboard shows all saved task lists with their title, description, created/due dates, priority, and category. From here you can search, filter, and open an individual list.

---

### Inside a List – Tasks View



> This view displays all tasks inside a specific list. Tasks show their description, created/due dates, completion status, and buttons to mark complete or delete.

---

### Creating a New List



> Dialog where the user enters the list name, description, optional due date, category, and priority before it gets added to the dashboard.

---

### Adding a New Task



> Dialog to add a new task to the current list, including title, description, optional due date, and priority.

---

## Architecture & Design Patterns

TaskHive was designed with **Model–View–Controller (MVC)** and several GoF patterns to keep the code modular and maintainable.  

### MVC

- **Model**
  - `Task` – represents a single task
  - `TaskListModel` – represents a list of tasks
  - `TaskRepository` – stores and loads all task lists from disk
- **View**
  - `DashboardView` – main window with all lists
  - `TaskListView` – window showing tasks for a single list
  - `TaskRowPanel`, `TaskListRowPanel` – reusable row components
- **Controller**
  - `DashboardController`
  - `TaskListController`

### Main Patterns Used

- **Repository Pattern**  
  - `TaskRepository` handles loading/saving all `TaskListModel` objects and hides file I/O from the rest of the app. 

- **Composite Pattern**  
  - `TaskListModel` behaves as a composite that owns many `Task` entities. The UI can treat a list as a single object while it internally manages a collection of tasks. 

- **Strategy Pattern (Filtering/Search)**  
  - Different filter strategies (by category, due date, priority, or none) can be swapped at runtime via a context class, without changing controller code. 

- **Factory/Dialog Factory**  
  - `NewListDialog` and `NewTaskDialog` act as factories that create `TaskListModel` and `Task` objects from user input. In the full design, dialogs can be created through a `DialogFactory` to keep controllers clean. 

---

## How to Run TaskHive Locally

1. **Clone the TaskHive source repository**.
2. Open the project in an IDE such as **IntelliJ IDEA**, **Eclipse**, or **NetBeans**.
3. Ensure you’re using **Java 17+**.
4. Build/compile the project.
5. Run the main class.
