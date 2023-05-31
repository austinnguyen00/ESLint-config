# ESLint with Prettier and Husky in React App

## Setting up ESLint with Airbnb style
1. Create a new `.eslintrc` file with `npm init @eslint/config`

![image](https://github.com/austinnguyen00/ESLint-config/assets/68253549/9d8cf0fa-71a3-4860-8414-19f97350da57)

After creating `.eslintrc.json` file, delete the rules

2. Install dependcies for `eslint-config-airbnb`

    - First install eslint airbnb `npx install-peerdeps --dev eslint-config-airbnb`
    - Then install other dependencies for typescript `npm install eslint-config-airbnb-typescript @typescript-eslint/eslint-plugin@^5.13.0 @typescript-eslint/parser@^5.0.0 --save-dev`
    
3. Configure eslint file
    ```
    extends: [
      'airbnb',
    + 'airbnb-typescript'
    ]
    ```
4. Configure the ESLint TypeScript parser
    ```
    {
      extends: ['airbnb', 'airbnb-typescript'],
    + parserOptions: {
    +   project: './tsconfig.json'
    + }
    }
    ```
5. In package.json, add scripts to lint files
    ```
    "lint": "eslint .",
    "lint:fix": "eslint --fix .",
    ```

## Setting up Prettier integrated with ESLint
1. Install packages  
    ```
    npm install --save-dev --save-exact prettier
    npm install --save-dev eslint-config-prettier
    npm install --save-dev eslint-plugin-prettier
    ```
    
2. Adding Prettier to `.eslintrc.json` config file  
    ```
    {
      "extends": [
        "some-other-config-you-use",
        "prettier"
      ]
    }

    {
      "plugins": ["prettier"],
      "rules": {
        "prettier/prettier": "error"
      }
    }
    ```
    
3. Install Prettier extension for VSCode
4. Turn on auto save in VSCode and Prettier will automatically format the file 

## Setting up Husky
1. One line command for setting up husky automatically

    ```
    npx husky-init and npm install
    ```
2. To set our init pre-commit hook to lint files before commit, run
  
    ```
    npx husky set .husky/pre-commit "npm run lint"
    ```     
