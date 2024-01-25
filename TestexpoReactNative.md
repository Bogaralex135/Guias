1. instalar expo con typescript

```bash
npx create-expo-app -t expo-template-blank-typescript
```

2. instalar dependencias

```bash
npx expo install jest-expo jest

npm install -D @testing-library/react-native
```

3. añade jest al package.json

```json
"scripts": {
  "test": "jest"
}

"jest": {
  "preset": "jest-expo",
  "transformIgnorePatterns": [
    "node_modules/(?!((jest-)?react-native|@react-native(-community)?)|expo(nent)?|@expo(nent)?/.*|@expo-google-fonts/.*|react-navigation|@react-navigation/.*|@unimodules/.*|unimodules|sentry-expo|native-base|react-native-svg)"
  ]
}

```

4. Comprueba que jest funciona

```bash
npx run test
```

si te sale este mensaje, no hay problemas.

```
No tests found, exiting with code 1
Run with `--passWithNoTests` to exit with code 0
In D:\pruebas\jesttest
6 files checked.
testMatch: **/**tests**/**/_.[jt]s?(x), \*\*/?(_.)+(spec|test).[tj]s?(x) - 0 matches
testPathIgnorePatterns: \\node_modules\\ - 6 matches
testRegex: - 0 matches
Pattern: - 0 matches
```

5. Haz tu primer test

Crea un archivo `App.test.js`

```javascript
import renderer from 'react-test-renderer'
import App from './App'

describe('App', () => {
  it('renders correctly', () => {
    const tree = renderer.create(<App />).toJSON()
    expect(tree).toMatchSnapshot()
  })
})
```

6. Ejecuta el test

```bash
npm run test
```

Te saldra un mensaje en consola de como este:

```bash
PASS  ./App.test.js
  App
    √ renders correctly (1060 ms)

 › 1 snapshot written.
Snapshot Summary
 › 1 snapshot written from 1 test suite.

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   1 written, 1 total
Time:        4.548 s
Ran all test suites.
```

Con eso ya tienes un primer test y todo configurado para hacer empezar a hacer test en tu aplicación.
