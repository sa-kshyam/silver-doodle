# React To-Do List Application

A clean, responsive, and modern To-Do List application built with **React** and styled using **Tailwind CSS**. The application allows users to add, toggle completion status, and delete tasks, with persistent data storage using the browser's `localStorage`.
# LIVE LINK - https://illustrious-medovik-1e0ea1.netlify.app/

# Features

 **Create Tasks:** Add new tasks easily using an input field.
 **Toggle Status:** Click on a task to mark it as complete (with a checkmark and strike-through text) or incomplete.
 **Delete Tasks:** Remove individual tasks seamlessly.
 **Persistent Storage:** Tasks are automatically saved to `localStorage` and will persist even after refreshing the page.
 **Responsive UI:** Styled dynamically with Tailwind CSS for high readability on both mobile devices and desktops.

---

##  Component Structure

The application is split into two core functional components:

1.  **`Todo.jsx` (Parent Component):**
    * Manages the state array (`todoList`).
    * Handles local storage synchronization with `useEffect`.
    * Contains the business logic functions: `add()`, `deleteTodo()`, and `toggle()`.
    * Renders the layout wrapper, title, input bar, and maps through tasks.
2.  **`TodoItems.jsx` (Child Component):**
    * A presentation component for individual list items.
    * Receives props (`text`, `id`, `isComplete`, `deleteTodo`, `toggle`) from the parent.
    * Renders specific styling triggers dynamically based on the completion state.



##  Code Reference & Architecture

### State & Hooks Used
* `useState`: Initializes the `todoList` by checking if there is any pre-existing JSON string in `localStorage`. If not, it defaults to an empty array `[]`.
* `useRef`: Tied to the input element to fetch user input value directly without triggering unnecessary re-renders on every keystroke.
* `useEffect`: Watches the `todoList` array and stringifies its contents to update `localStorage` whenever a task is added, deleted, or toggled.

### Codebase Breakdowns

#### Add Task Logic
```javascript
const add = () => {
  const inputText = inputRef.current.value.trim();
  if (inputText === "") return null; // Prevents empty tasks

  const newTodo = {
    id: Date.now(), // Unique identifier based on time
    text: inputText,
    isComplete: false,
  }
  setTodoList((prev) => [...prev, newTodo]);
  inputRef.current.value = ""; // Resets input
}
