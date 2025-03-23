# Trello-Style Todo Board

A Kanban-style task management application built with React that allows users to manage their tasks visually across different stages of completion.

## Features

- Kanban-style board with three columns (Pending, In Progress, Completed)
- Drag and drop functionality to move tasks between columns
- Create, read, update, and delete tasks
- Responsive design that works on both desktop and mobile devices
- Integration with DummyJSON API for backend operations

## Tech Stack

- React.js
- React DnD (for drag and drop functionality)
- Vite (for build and development)
- CSS (for styling)
- DummyJSON API (for mock backend)

## Installation

Clone the repository:

```bash
git clone https://github.com/MahiyaKhan/To-Do-App
cd my-app
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

## Building for Production

To build the application for production:

```bash
npm run build
```

## Deployment

The application is configured to be deployed on GitHub Pages. To deploy:

1. Update the `vite.config.js` file with your repository name:

```javascript
export default defineConfig({
  plugins: [react()],
  base: "/To-Do-App/",
});
```

2. Run the deploy script:

```bash
npm run deploy
```

## Project Structure

```
/src
  /components
    - TaskBoard.jsx     # Main component that manages the board layout
    - TaskColumn.jsx    # Column component that contains task cards
    - TaskCard.jsx      # Individual task card component
    - TaskModal.jsx     # Modal for editing tasks
    - AddTaskForm.jsx   # Form for adding new tasks
    - Header.jsx        # Application header
  - App.jsx             # Main application component
  - App.css             # Application styles
  - index.jsx            # Entry point
```

## Approach

### State Management

The application uses React's built-in useState hook for state management. The main state objects are:

- `tasks`: Array of all tasks fetched from the API
- `isLoading`: Boolean to track API loading state
- `error`: State for storing any API errors

### API Integration

The application interacts with the DummyJSON API for CRUD operations:

- `GET /todos`: Fetch all tasks
- `POST /todos/add`: Create a new task
- `PUT /todos/:id`: Update a task
- `DELETE /todos/:id`: Delete a task

### Drag and Drop

React DnD is used to implement the drag and drop functionality:

- TaskCard component is set up as a drag source
- TaskColumn component is set up as a drop target
- When a card is dropped in a different column, the status is updated via API

## Trade-offs and Improvements

### Trade-offs

1. **Local State vs. Global State**: For simplicity, the application uses local state management. For larger applications, a global state management solution like Redux or Context API would be more appropriate.

2. **Real-time Updates**: The application doesn't implement real-time updates. In a production environment, WebSockets or polling might be used to keep the board in sync across multiple users.

3. **Error Handling**: Basic error handling is implemented, but a more robust solution with retry logic and detailed user feedback would be valuable in production.

### Potential Improvements

1. **Authentication**: Add user authentication to allow multiple users with their own boards.

2. **Advanced Filtering**: Implement filtering and searching capabilities for tasks.

3. **Persistence**: Add local storage support to persist the board state between page reloads.

4. **Custom Lanes**: Allow users to create and customize their own lanes/columns.

5. **Task Details**: Expand task properties to include due dates, priorities, attachments, etc.

6. **Optimistic UI Updates**: Implement optimistic updates to improve perceived performance.

7. **Unit and Integration Tests**: Add comprehensive test coverage.

8. **Accessibility**: Enhance keyboard navigation and screen reader support.

## License

MIT
