markdown
# shadcn/ui Installation with Vite and JavaScript

This guide provides step-by-step instructions for setting up `shadcn/ui` in a new React project using Vite and JavaScript.

### Prerequisites
*   [Node.js](https://nodejs.org/) installed on your machine.
*   A code editor like [VS Code](https://code.visualstudio.com/).

---

### Step 1: Create a new React project with Vite
1.  Run the following command in your terminal.
    ```sh
    npm create vite@latest
    ```
2.  Follow the prompts to set up a new project:
    *   **Project name**: `<your-project-name>`
    *   **Select a framework**: `React`
    *   **Select a variant**: `JavaScript`
3.  Navigate into your project folder and install the dependencies.
    ```sh
    cd <your-project-name>
    npm install
    ```

### Step 2: Install and configure Tailwind CSS
`shadcn/ui` relies on Tailwind CSS, so you need to set it up first.

1.  **Install the necessary packages**:
    ```sh
    npm install -D tailwindcss postcss autoprefixer
    ```
2.  **Generate configuration files**:
    ```sh
    npx tailwindcss init -p
    ```
    This command will create `tailwind.config.js` and `postcss.config.js` files.
3.  **Configure Tailwind template paths**:
    Open `tailwind.config.js` and update the `content` array.
    ```js
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
    ```
4.  **Add Tailwind directives to your CSS**:
    Open `./src/index.css` and add the following directives at the top.
    ```css
    /* ./src/index.css */
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```

### Step 3: Configure path aliases
To enable clean imports (e.g., `@/components/ui/button`), configure path aliases for JavaScript.

1.  **Create `jsconfig.json`**:
    Create a `jsconfig.json` file in your project's root directory.
2.  **Add alias configuration**:
    ```json
    // jsconfig.json
    {
      "compilerOptions": {
        "baseUrl": ".",
        "paths": {
          "@/*": ["./src/*"]
        }
      }
    }
    ```

### Step 4: Initialize `shadcn/ui`
Run the initialization command and answer the prompts.

1.  **Run the init command**:
    ```sh
    npx shadcn@latest init
    ```
2.  **Answer the prompts** for a typical JavaScript setup:
    *   **Which style would you like to use?**: `Default`
    *   **Which color would you like to use as base color?**: `Slate` (or your preference)
    *   **Do you want to use CSS variables for colors?**: `No`
    *   **Where is your global CSS file?**: `src/index.css`
    *   **Configure the import alias for components**: `@/components`
    *   **Configure the import alias for utils**: `@/lib/utils`
    *   **Are you using React Server Components?**: `No`
    *   **Write components.json**: `yes`

### Step 5: Add your first component
To verify the setup, add a `Button` component.

1.  **Add a button component**:
    ```sh
    npx shadcn@latest add button
    ```
2.  **Import and use the component**:
    Update `src/App.jsx` to use the new `Button` component.
    ```jsx
    // src/App.jsx
    import { Button } from "@/components/ui/button";

    export default function App() {
      return (
        <div className="flex justify-center items-center h-screen">
          <Button>Click me</Button>
        </div>
      );
    }
    ```
3.  **Run the dev server**:
    ```sh
    npm run dev
    ```
You should now see a `shadcn/ui` button in your browser.

---

### Adding more components
To add more components, simply use the `shadcn-ui add` command followed by the component name. You can find a list of available components on the [shadcn/ui website](https://ui.shadcn.com/docs/components).

```sh
npx shadcn-ui@latest add <component-name>
