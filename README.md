# An application for storing, creating, deleting, and searching notes. React + TypeScript + Vite

## 📂 Project structure

           05-notehub/
           ├── 📁public         # Static assets copied directly to the final build
           ├── 📁src/           # Main source directory for all application logic
           │ ├── 📁assets       # Icons, images, fonts
           │ ├── 📁components/  # Reusable UI components grouped by feature
           │ │ ├── 📁App/
           │ │ │ ├── 📄App.tsx      # Main app container that ties components together
           │ │ │ └── 📄App.module.css    # Styling for App component
           │ │ ├── 📁ErrorMessage/
           │ │ │ ├── 📄ErrorMessage.tsx           # Component to display user-facing error messages
           │ │ │ └── 📄ErrorMessage.module.css    # Styles specific to ErrorMessage.
           │ │ ├── 📁NoteForm/
           │ │ │ ├── 📄NoteForm.tsx   # Form inside modal to create new note (uses Formik & Yup)
           │ │ │ └── NoteForm.module.css # Scoped styles for form fields and buttons
           │ │ ├── 📁NoteList/
           │ │ │ ├── 📄NoteList.tsx   # Renders a list of notes fetched from the backend
           │ │ │ └── 📄NoteList.module.css # Card layout and button styles for individual notes
           │ │ └── 📁NoteModal/
           │ │ │ ├── 📄NoteModal.tsx  # Modal container that wraps NoteForm and uses createPortal
           │ │ │ └── 📄NoteModal.module.css # Modal positioning and backdrop styles
           │ │ ├── 📁Pagination/
           │ │ │ ├── 📄Pagination.tsx  # Handles page navigation using ReactPaginate
           │ │ │ └── 📄Pagination.module.css # Pagination component styles (active, disabled, etc.)
           │ │ ├── 📁SearchBox/
           │ │ │ ├── 📄SearchBox.tsx # Input component for filtering notes (with debounce)
           │ │ │ └── 📄SearchBox.module.css  # Styles for search input
           │ ├── 📁services/
           │ │ └── 📄noteService.ts # Axios-based API handlers: fetchNotes, createNote, deleteNote
           │ ├── 📁types/
           │ │ └── 📄note.ts # TypeScript interface Note and related types
           │ ├── 📄declarations.d.ts    # Custom TS declarations (e.g., for CSS modules)
           │ ├── 📄global.css           Global styles applied throughout the app.
           │ ├── 📄main.tsx             # Entry point: ReactDOM.createRoot + React Query provider
           │ └── 📄vite-env.d.ts Environment type declarations for Vite's special variables like
           ├── 📄.gitignore          Lists files/folders that Git should ignore
           ├── 📄README.md           Project documentation and setup instructions.
           ├── 📄eslint.config.js    ESLint configuration for code linting and formatting rules.
           └── 📄index.html Main HTML template used by Vite to inject the app during build and dev.
           └── 📄package-lock.json   Lockfile that ensures consistent npm install behavior.
           └── 📄package.json        Lists project dependencies, scripts, and metadata.
           └── 📄tsconfig.app.json   TypeScript configuration specific to the application code.
           └── 📄tsconfig.json       Root TypeScript config file.
           └── 📄tsconfig.node.json  TypeScript config for Node.js-specific tooling or scripts.
           └── 📄vite.config.ts      Vite configuration file for build and development settings.

### This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config({
  extends: [
    // Remove ...tseslint.configs.recommended and replace with this
    ...tseslint.configs.recommendedTypeChecked,
    // Alternatively, use this for stricter rules
    ...tseslint.configs.strictTypeChecked,
    // Optionally, add this for stylistic rules
    ...tseslint.configs.stylisticTypeChecked,
  ],
  languageOptions: {
    // other options...
    parserOptions: {
      project: ["./tsconfig.node.json", "./tsconfig.app.json"],
      tsconfigRootDir: import.meta.dirname,
    },
  },
});
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default tseslint.config({
  plugins: {
    // Add the react-x and react-dom plugins
    "react-x": reactX,
    "react-dom": reactDom,
  },
  rules: {
    // other rules...
    // Enable its recommended typescript rules
    ...reactX.configs["recommended-typescript"].rules,
    ...reactDom.configs.recommended.rules,
  },
});
```
