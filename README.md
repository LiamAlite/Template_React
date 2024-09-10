# React + TailwindCSS テンプレート

## コマンド記述履歴

### React プロジェクトの作成

`npx create-react-app app --template cra-template-pwa`

`cd app`

`npm start`

→ 起動するか確認する

### TailwindCSS の導入

`npm install -D tailwindcss postcss autoprefixer`

`npx tailwindcss init`

#### src/tailwind.config.js

```javascript
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

#### src/index.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

`npm audit fix --force`

### VSCode 設定の追加

#### .vscode/settings.json

```json
{
  "cSpell.words": ["tailwindcss"],

  // エディタの設定
  "editor.tabSize": 2,
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  // JSXやTSXでのEmmetサポート
  "emmet.includeLanguages": {
    "javascript": "javascriptreact",
    "typescript": "typescriptreact"
  },

  // ファイルパスの自動補完
  "path-intellisense.mappings": {
    "/src": "${workspaceFolder}/src"
  },

  // 拡張機能の推奨
  "extensions.ignoreRecommendations": false
}
```

#### .vscode/extensions.json

```json
{
  "recommendations": [
    "esbenp.prettier-vscode", // Prettier
    "dbaeumer.vscode-eslint", // ESLint
    "csstools.postcss", // PostCSS
    "bradlc.vscode-tailwindcss", // TailwindCSS IntelliSense
    "christian-kohler.path-intellisense", // Path IntelliSense
    "streetsidesoftware.code-spell-checker" // Spell checker
  ]
}
```
