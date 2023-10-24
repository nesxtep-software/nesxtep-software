# Installation and Configuration of Jest + React Testing Library 

## In React + Vite Projects

1. Installations:
    ```shell
    yarn add --dev jest babel-jest @babel/preset-env @babel/preset-react 
    yarn add --dev @testing-library/react @types/jest jest-environment-jsdom
    ```
2. Optional: If we use Fetch API in the project:
    ```shell
    yarn add --dev whatwg-fetch
    ```

3. Update the scripts in __package.json__:
    ```json
    "scripts: {
        ...
        "test": "jest --watchAll"
    ```

4. Create the Babel configuration __babel.config.js__
    ```javascript
    module.exports = {
        presets: [
            [ '@babel/preset-env', { targets: { esmodules: true } } ],
            [ '@babel/preset-react', { runtime: 'automatic' } ],
        ],
    };
    ```

5. Optional, but eventually necessary, create Jest config and setup:
   1. __jest.config.js__
        ```javascript
        module.exports = {
            testEnvironment: 'jest-environment-jsdom',
            setupFiles: ['./jest.setup.js']
        }
        ```

    2. __jest.setup.js__
        ```javascript
        // En caso de necesitar la implementación del FetchAPI
        import 'whatwg-fetch'; // <-- yarn add whatwg-fetch
        ```

