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

### GitHub Pages公開設定

#### gh-pagesパッケージの追加
`npm install gh-pages --save-dev`

#### .github/workflows/gh-pages.yml
```yaml
name: Deploy React App to GitHub Pages

on:
  push:
    branches:
      - main # デプロイをトリガーするブランチを指定

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: "14" # Node.jsのバージョンを指定

      - name: Install dependencies
        run: npm install

      - name: Build the React app
        run: npm run build

      - name: Deploy to GitHub Pages
        run: npm run deploy
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```