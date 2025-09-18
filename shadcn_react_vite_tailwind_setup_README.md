
Installing Shadcn UI in a React project using Vite and JavaScript involves several steps:
1. Create a new Vite + React Project:
Code

npm create vite@latest
Follow the prompts: choose a project name, select "React" as the framework, and "JavaScript" as the variant.
Navigate into your new project directory:
Code

cd your-project-name
Install the project's dependencies.
Code

npm install
2. Add Tailwind CSS:
Code

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
This creates tailwind.config.js and postcss.config.js.
3. Configure Tailwind CSS:
Open tailwind.config.js and update the content array to include your source files:
JavaScript

// tailwind.config.js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
Add Tailwind directives to your index.css (or globals.css) file:
Code

/* src/index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
4. Configure Path Aliases (Optional but Recommended):
Create a jsconfig.json file in your project root:
Code

// jsconfig.json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
Update vite.config.js to resolve the alias:
JavaScript

// vite.config.js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import path from 'path';

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});
5. Initialize Shadcn UI:
Code

npx shadcn-ui@latest init
Follow the prompts:
Choose your desired style (e.g., "default").
Select a base color (e.g., "slate").
Confirm the global CSS file (e.g., src/index.css).
Choose whether to use CSS variables for theming (usually "no" for JavaScript projects unless you plan custom theming).
Confirm the import alias (e.g., "@/components/ui").
Do not enable React Server Components for a standard Vite setup.
6. Add Shadcn UI Components:
You can now add individual components as needed. For example, to add a button:
Code

npx shadcn-ui@latest add button
7. Use Components in your React App:
Import and use the components in your App.jsx or other component files:
JavaScript

// src/App.jsx
import { Button } from "@/components/ui/button";

function App() {
  return (
    <div className="p-4">
      <Button>Click me</Button>
    </div>
  );
}

export default App;
8. Run your Development Server:
Code

npm run dev
Your Shadcn UI components should now be visible in your application.
