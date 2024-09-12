# VS-CODE\_\_ReactJs-ESLint-configuration-in-Vite

---

## Один из самых простых способов улучшить свой код — использовать линтер!

Не только улучшить💪, но и унифицировать код вашей команды.
У каждого разработчика свой стиль, поэтому линтер может помочь вам сделать код вашей команды понятным и понятным для всех.

### Но сначала, что такое Lint или Linter❓

**Lint** — это процесс проверки кода на ошибки, несоответствия стилю и плохие практики.

**Linter** — это инструмент для синтаксического анализа, который проверяет код и выявляет ошибки, опечатки или любые потенциальные проблемы в коде программиста. Он помогает поддерживать качество и стандарты в проекте.

![errorImage](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/errorImage.png?raw=true)

> ---
>
> Предварительное условие: у вас должны быть установлены [Visual Studio Code](https://code.visualstudio.com/) и [NodeJS](https://nodejs.org/en/).
>
> ---

## И так Начнем

## Но сначала необходимо установить расширения для VS Code: Prettier и ESLint

**Прежде чем приступить к настройке, убедитесь, что в вашем VS Code установлены расширения Prettier и ESLint. Эти инструменты помогут вам автоматически форматировать код и проверять его на наличие ошибок, что обеспечит единообразие и чистоту проекта.**

> ![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/prettierImg.png?raw=true)
>
> ![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/eslintImg.png?raw=true)

### 1. Создать приложение ReactJS

Давайте создадим приложение ReactJS и назовем его «eslint-app-vite». Мы создадим приложение с помощью терминала.

```npm
npm create vite eslint-app-vite
```

Дальше нужно открыть наш проект через Vs Code. Чтобы в дальнейшем с ним работать.

---

Когда мы создаём новый проект с помощью Vite, файл конфигурации ESLint `.eslintrc.cjs` автоматически создаётся в проекте.

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/eslint.csj.png?raw=true)

---

**Мы этот файл удаляем. Однако этот файл является устаревшей версией конфигурации.**
![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/delete-eslintrc.cjs.png?raw=true)

---

**Для более современной и гибкой настройки мы рекомендуем перейти на новый формат конфигурации ESLint — создаём новый файл `eslint.config.js.`**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/create-eslint.config.js.png?raw=true)

---

потом установливаем различные плагины для react'а вот таким образом в терминале:

```npm
npm i -D eslint-plugin-prettier eslint-config-prettier eslint-plugin-import
```

---

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/imgTerminal.png?raw=true)

---

наш `package.json` должен выглядеть вот так

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/eslint-setting.png?raw=true)

**После того как мы обновляем конфигурацию до нового формата eslint.config.js, и установили дополнительные плагины, следующим шагом будет установка последней версии ESLint. Это можно сделать с помощью следующей команды в терминале :**

```npm
npm install -D eslint@latest --force
```

---

**Нам должен установливатся последняя версия eslint'a**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/latest-eslint.png?raw=true)

---

**Для полноценной поддержки мы должны добавить ключ `overrides` и указать ESLint, что независимо от того, в каком приложении pre-dependencies не видят ESLint, мы хотим использовать ту же версию, которая указана выше. Таким образом, мы перезаписываем зависимость для всех пакетов, если вдруг что-то идет некорректно.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/ovverrides.png?raw=true)

---

**Кроме того, нам понадобится еще одна зависимость — `globals`. Соответственно, `globals` — это дополнительный пакет, который нам пригодится. Мы будем использовать его как один из импортов.**

```npm
npm i -D globals
```

---

наш `globals` должен выглядеть вот так

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/globals.png?raw=true)

---

**Потом мы должны написать весь набор импортов в `eslint.config.js`, который нам понадобится, чтобы их использовать.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/importsEslintFile.png?raw=true)

---

**Сам по себе `eslint.config` будет возвращаться по умолчанию из этого файла, но возвращаться он будет как массив. Это будет массив с объектами, содержащими настройки. Здесь возможны разные сценарии: мы можем разделить настройки по объектам. В одном месте укажем, какие файлы мы хотим отслеживать, какие — игнорировать, в другом — настроим плагины и так далее.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/defaultExpConfig.png?raw=true)

---

**И начнем с того, что настроим просто набор плагинов, которые будем использовать.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/addPlug.png?raw=true)

---

### Далее мы будем отдельно указывать файлы, которые хотим отслеживать, и файлы, которые не хотим отслеживать.

---

**Опять же, мы разделим их на разные объекты и укажем, какие файлы нам не нужны.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/ignoreImg.png?raw=true)

---

**Дальше добавляем js.configs.recommended, чтобы подключить стандартные рекомендованные правила для JavaScript. Это позволит автоматически применять базовые правила ESLint для предотвращения распространенных ошибок и упростит настройку, обеспечивая совместимость с другими плагинами, такими как React и Prettier.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/recConfigImg.png?raw=true)

---

**Дальше добавляем блок languageOptions, чтобы настроить глобальные переменные для окружений node, browser, и es2024. Это позволит ESLint понимать доступные глобальные объекты. Также указываем parserOptions из рекомендованных настроек React, чтобы корректно обрабатывать JSX и другие особенности React.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/language-setting.png?raw=true)

---

**Дальше добавляем `files: ['**/\*.{js,jsx}']`, чтобы указать ESLint, какие файлы нужно проверять. В данном случае ESLint будет обрабатывать все файлы с расширениями .js и .jsx во всех директориях проекта.\*\*

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/files.png?raw=true)

---

> ### 1. ...eslintConfigPrettier.rules
>
> **Чтобы включить правила форматирования из eslint-config-prettier. Это обеспечивает автоматическое применение настроек форматирования, таких как использование одинарных кавычек и управление пробелами, при проверке кода ESLint.**

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/rules.png?raw=true)

---

> ### 2. "no-console": "warn"
>
> **Чтобы включить дополнительные правила для проверки кода. Например, правило `'no-console': 'warn'` используется для предупреждения о наличии вызовов console.log в коде, что помогает избежать забытых отладочных сообщений в финальной версии приложения.**

> ---

```diff
rules: {
     ...eslintConfigPrettier.rules,
+    "no-console": "warn",
},
```

> ---

> ### 3. "react/jsx-no-target-blank": "off",
>
> **Для повышения безопасности и улучшения качества кода в вашем проекте рекомендуется использовать дополнительные правила ESLint. Например, правило react/jsx-no-target-blank помогает предотвратить уязвимости, связанные с открытием ссылок в новой вкладке или окне. Когда правило включено и установлено как 'error', оно требует, чтобы все ссылки с атрибутом target="\_blank" также содержали атрибут rel="noopener noreferrer". Это предотвращает возможные атаки через объект window.opener, обеспечивая дополнительную защиту вашего приложения.**

### Пример

**Без защиты (уязвимо)**

```jsx
<a href="https://example.com" target="_blank">
  Visit Example
</a>
```

**С защитой (безопасно)**

```jsx
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
  Visit Example
</a>
```

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
+    "react/jsx-no-target-blank": "off",
},
```

> ---

> ### 4. "react-refresh/only-export-components"
>
> **Правило `react-refresh/only-export-components` проверяет, что модули экспортируют только React-компоненты, что улучшает поддержку Fast Refresh. Настройка `"warn"` позволяет получать предупреждения, если в модуле экспортируются что-то помимо компонентов. Опция `{ allowConstantExport: true }` позволяет экспортировать константы без предупреждений.\***

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
+    "react-refresh/only-export-components": [
+       "warn",
+       { allowConstantExport: true },
+     ],
},
```

---

> **5. Дальше будем убирать из `package.json` опцию `--ext js,jsx` из команды линтинга, так как расширения файлов уже указаны в конфигурации ESLint. Теперь настройка в конфигурационном файле определяет, какие файлы проверять, и команда линтинга будет использовать эту конфигурацию.**

![delete gif](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/gifff.gif?raw=true)

---

**6. Когда вы выполняете команду npm run lint в терминале, ESLint проверяет ваш код на наличие проблем и выводит результаты в консоль. Эти же ошибки и предупреждения отображаются в VS Code, если у вас установлен и настроен ESLint плагин. Обычно вывод в терминале и в VS Code выглядит так:**

```npm
npm run lint
```

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/parser.png?raw=true)

---

Если после выполнения команды npm run lint результаты не обновляются, попробуйте следующее:

1. Нажмите на MacOS `Cmd + Shift + P`
2. На Windows: `Ctrl + Shift + P` в VS Code.

Введите `Reload Window` и выберите эту команду.
Это перезагрузит ваш VS Code, что может помочь обновить отображение ошибок и предупреждений.

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/commands.png?raw=true)

---

> ---

> ### 7. "prettier/prettier"
>
> **Чтобы ESLint использовал `Prettier` для форматирования кода и обрабатывал несоответствия как ошибки.**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
+    "prettier/prettier": [
+       "error",
+       {
+         endOfLine: "auto",
+         singleQuote: false,
+         tabWidth: 2,
+         trailingComma: "es5",
+         bracketSpacing: true,
+       },
+     ],
},
```

> ---

> ### 8. "import/no-default-export"
>
> **8. Правило `import/no-default-export` запрещает экспорт по умолчанию, требуя использования только именованных экспортов `(export { name })`, что улучшает ясность и управляемость кода..**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
+    "import/no-default-export": "error",
},
```

> ---

> ### 9. "no-unused-vars"
>
> **Правило no-unused-vars в ESLint предотвращает наличие неиспользуемых переменных, что помогает поддерживать чистоту и читаемость кода.**

### Что делают его параметры:

- `"error"`: Указывает, что неиспользуемые переменные вызывают ошибку.
- `vars: "all"`: Проверяет все переменные, чтобы убедиться, что они используются.
- `args: "after-used"`: Проверяет аргументы функций, но только те, которые идут после уже используемых. Например, если первый аргумент не используется, но второй — да, это не будет ошибкой.
- `ignoreRestSiblings: true:` Игнорирует неиспользуемые переменные, полученные через оператор rest `(...)`, что полезно при деструктуризации.

### Пример

```jsx
const example = (a, b) => {
  console.log(a); //  Переменная `b` вызовет ошибку, так как не используется
};
```

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
+    "no-unused-vars": [
+       "error",
+       {
+         vars: "all",
+         args: "after-used",
+         ignoreRestSiblings: true,
+       },
+     ],
},
```

> ---

> ### 10. "func-style"
>
> **Правило `func-style: ["error", "expression"]` требует использовать только функциональные выражения `(const func = function() {})`, запрещая декларации `(function func() {})`.**

**_Запрещает декларации функций, но разрешает выражения_**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
+    "func-style": ["error", "expression"],
},
```

> ---

> ### 11. "prefer-arrow-callback"
>
> **Эта настройка ESLint запрещает декларации функций и обычные функциональные выражения, разрешая только стрелочные функции:**

**_Принуждает использовать стрелочные функции вместо обычных function expressions_**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
+    "prefer-arrow-callback": ["error"],
},
```

> ---

> ### 12. "react/jsx-uses-vars"
>
> **Правило `react/jsx-uses-vars` предотвращает ошибки, связанные с неиспользуемыми переменными, автоматически помечая переменные, содержащие JSX, как используемые, чтобы ESLint не считал их неиспользованными.**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
     "prefer-arrow-callback": ["error"],
+    "react/jsx-uses-vars": "error",

},
```

> ---

> ### 13. "no-shadow"
>
> **Теневое копирование — это процесс, при котором локальная переменная имеет то же имя, что и переменная в содержащей ее области. Например: Примеры неправильного кода для этого правила:**

```jsx
var a = 3;
function b() {
  var a = 10;
}
```

#### Параметры правила:

**Если вы хотите убрать это правило, конфигурация будет такой:**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
     "prefer-arrow-callback": ["error"],
     "react/jsx-uses-vars": "error",
+    "no-shadow": "off",

},
```

> ---

> ### 14. "no-alert": "error",
>
> **Запрещает использование методов `alert()`,` confirm()`, и `prompt(`) в коде. Эти методы создают модальные диалоги, которые могут быть неприятными для пользователей и не всегда подходят для современных приложений. Это правило помогает избежать их использования в финальной версии кода**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
     "prefer-arrow-callback": ["error"],
     "react/jsx-uses-vars": "error",
     "no-shadow": "off",
+    "no-alert": "error",
},
```

> ---

> ### 15. eqeqeq: "error",
>
> **Требует использования строгого сравнения `(=== и !==)` вместо нестрогого сравнения `(== и !=)`. Это помогает избежать неожиданного поведения, связанного с неявным преобразованием типов в JavaScript.**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
     "prefer-arrow-callback": ["error"],
     "react/jsx-uses-vars": "error",
     "no-shadow": "off",
     "no-alert": "error",
+    eqeqeq: "error",
},
```

> ---

> ### 16. "react/jsx-no-undef": "error",
>
> **Предотвращает использование не определённых React-компонентов в JSX. Это помогает избежать ошибок, связанных с опечатками или забытыми импортами.**

```diff
rules: {
     ...eslintConfigPrettier.rules,
     "no-console": "warn",
     "react/jsx-no-target-blank": "off",
     "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
     "prettier/prettier": [
        "error",
        {
          endOfLine: "auto",
          singleQuote: false,
          tabWidth: 2,
          trailingComma: "es5",
          bracketSpacing: true,
        },
      ],
     "import/no-default-export": "error",
     "no-unused-vars": [
        "error",
        {
          vars: "all",
          args: "after-used",
          ignoreRestSiblings: true,
        },
      ],
     "func-style": ["error", "expression"],
     "prefer-arrow-callback": ["error"],
     "react/jsx-uses-vars": "error",
     "no-shadow": "off",
     "no-alert": "error",
     eqeqeq: "error",
+    "react/jsx-no-undef": "error",
},
```

> ---

> ### Мы написали правило для `export default`, но наш файл `eslint.config.js` вызывает ошибку, потому что он использует `export default`.

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/exportDefaultEslintConfig.png?raw=true)

> ## Чтобы решить эту проблему, нужно написать следующее правило:

![image](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images%20copy/fixedDefaultExport.png?raw=true)

## После проверяем...

![finish](https://github.com/ZhakshylykNasip/eslint-images/blob/main/images/finish.gif?raw=true)

> ---

## Поздравляем!

**Теперь, с настройками ESLint, Prettier для вашего React-проекта, вы обеспечите единообразие и чистоту кода. Линтер будет своевременно сообщать о любых проблемах с кодом и форматированием, что упростит поддержание высокого качества проекта.**
