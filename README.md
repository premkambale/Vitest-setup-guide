![Vitest Setup Guide](vitest-setup-guide.png)
# 🌟⚡ Vitest Setup Guide ⚡🌟

Easily set up **Vitest** for your React + TypeScript project with Testing Library, JSDOM, and coverage reports.  
Let’s make your tests run like 🚀 **Lightning Fast** and look 💎 **Professional**.

---

## 🎯 STEP 1 — Install Dependencies 📦
```bash
npm install --save-dev vitest @vitest/ui jsdom @testing-library/react @testing-library/jest-dom @testing-library/user-event vitest c8
````

📌 *This installs Vitest, UI mode, JSDOM for browser-like testing, Testing Library helpers, and coverage tool.*

---

## 📝 STEP 2 — Create `vitest.setup.ts` 🛠

Add the following lines so Testing Library works perfectly:

```typescript
import '@testing-library/jest-dom';
import '@testing-library/jest-dom/vitest';
```

✨ *This ensures you can use matchers like `toBeInTheDocument()` in your tests.*

---

## ⚙ STEP 3 — Create `vitest.config.ts` 🧩

Here’s the **magic config** that powers your tests:

```typescript
// vitest.config.ts
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    environment: 'jsdom',
    // setupFiles: ['./vitest.setup.ts'],
    coverage: {
      provider: 'v8', // or 'v8' if you're using Node 20+
      reporter: ['text', 'html'], // 📊 Console + HTML coverage reports
      exclude: [
        '**/*.test.tsx',              // 🚫 Exclude test files
        '**/*.types.ts',             // 🚫 Exclude type definitions
        '**/vite-env.d.ts',         // 🚫 Exclude Vite env types
        '**/*.d.ts',               // 🚫 Exclude files with .d.ts
        '**/*.config.ts',         // 🚫 Exclude config files
        '**/*.config.js',        // 🚫 Exclude config files
        '**/*.setup.ts',        // 🚫 Exclude setup files
        '**/index.ts',         // 🚫 Exclude barrel files
        '**/environments.ts', // 🚫 Exclude environment files
      ],
    },
  },
});
```

💡 *Change `setupFiles` comment if you want to load `vitest.setup.ts` automatically.*

---

## 📜 STEP 4 — Add Scripts to `package.json` 📂

```json
"scripts": {
  "test": "vitest",
  "test:coverage": "vitest run --coverage"
}
```

✅ *Now you can run tests and coverage with simple commands.*

---

## ▶ STEP 5 — Run Tests 🚀

```bash
npm run test
```

🖥 *Runs Vitest in your terminal.*

---

## 📊 STEP 6 — Generate Coverage Report 🖼

```bash
npx vitest run --coverage
```

📌 *Opens a coverage report you can view in your browser.*

---

> ⚠ **Note:** If any test fails ❌, the coverage report won’t be generated.

---

## 🎉 You’re Ready!

You can now:

* 🧪 Write unit tests with **Vitest + Testing Library**
* 🔄 Run them in watch mode
* 📈 See **beautiful HTML coverage reports**

💖 *Happy Testing!* 🎯

---
