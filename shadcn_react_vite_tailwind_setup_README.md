# 🚀 Shadcn + React + Vite + Tailwind CSS Setup

## ✅ 1️⃣ Create React + Vite Project

``` bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
```

------------------------------------------------------------------------

## ✅ 2️⃣ Install Tailwind CSS

``` bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

👉 Configure `tailwind.config.js`:

``` js
export default {
  content: [
    './index.html',
    './src/**/*.{js,jsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

👉 Add to `src/index.css`:

``` css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

------------------------------------------------------------------------

## ✅ 3️⃣ Install Shadcn UI Dependencies

``` bash
npm install class-variance-authority clsx tailwind-merge lucide-react tw-animate-css
```

------------------------------------------------------------------------

## ✅ 4️⃣ Initialize Shadcn UI

``` bash
npx shadcn@latest init
```

👉 Follow prompts:\
✔️ Pick a base color (e.g., Neutral).

------------------------------------------------------------------------

## ✅ 5️⃣ Configure Import Alias

Create `tsconfig.json` in project root:

``` json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "include": ["src"]
}
```

------------------------------------------------------------------------

## ✅ 6️⃣ Update vite.config.js

``` js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'
import path from 'path'

export default defineConfig({
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src'),
    },
  },
  plugins: [react(), tailwindcss()],
})
```

------------------------------------------------------------------------

## ✅ 7️⃣ Example Utility Function

Create `src/lib/utils.ts`:

``` ts
export function cn(...classes) {
  return classes.filter(Boolean).join(' ')
}
```

------------------------------------------------------------------------

## ✅ 8️⃣ Example Button Component

Create `src/components/ui/button.jsx`:

``` jsx
import { cn } from '@/lib/utils'

export function Button({ className, variant = 'default', children, ...props }) {
  return (
    <button
      className={cn(
        'px-4 py-2 rounded border font-medium',
        variant === 'outline' ? 'border-gray-500' : 'bg-blue-500 text-white',
        className
      )}
      {...props}
    >
      {children}
    </button>
  )
}
```

------------------------------------------------------------------------

## ✅ 9️⃣ Example App.jsx

``` jsx
import { Button } from '@/components/ui/button'

function App() {
  return (
    <div className="p-8">
      <Button variant="outline">Hello Shadcn</Button>
    </div>
  )
}

export default App
```

------------------------------------------------------------------------

## ✅ 🔧 Start Development Server

``` bash
npm run dev
```

🌐 Open in browser → <http://localhost:5173>

✅ You should see a styled Button component.

------------------------------------------------------------------------

🎉 Your Shadcn + React + Vite + Tailwind CSS setup is now ready for
advanced UI development!
