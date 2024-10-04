# Unit Tests in JS

This project includes tasks focused on learning to create unit tests in Node.js.

## Learning Objectives

- Use Mocha to write a test suite.
- Utilize various assertion libraries (Node or Chai).
- Present long test suites effectively.
- Understand when and how to use spies.
- Understand when and how to use stubs.
- Learn about hooks and their usage.
- Perform unit testing with async functions.
- Write integration tests with a simple Node server.

## Tasks To Complete

- [x] **0. Basic test with Mocha and Node assertion library**
  - **Install Mocha via npm:**
    - Set up scripts in your [`package.json`](package.json) to run Mocha using `npm test`.
    - Use `assert` for assertions.
  - **Create [`0-calcul.js`](0-calcul.js):**
    - Define a function `calculateNumber` that accepts two arguments `a` and `b`.
    - Round `a` and `b` and return their sum.
  - **Test cases:**
    - Create a file [`0-calcul.test.js`](0-calcul.test.js) with test cases for this function.
    - Assume `a` and `b` are always numbers.
    - Focus tests on the rounding behavior.
  - **Tips:**
    - This test suite may be more extensive than necessary; remember to check edge cases.
  - **Requirements:**
    - Use `assert`.
    - Run the test suite using `npm test 0-calcul.test.js`.
    - All tests must pass without warnings.
  - **Expected output:**
    ```powershell
    > const calculateNumber = require("./0-calcul.js");
    > calculateNumber(1, 3)
    4
    > calculateNumber(1, 3.7)
    5
    > calculateNumber(1.2, 3.7)
    5
    > calculateNumber(1.5, 3.7)
    6
    ```
  - **Run test:**
    ```powershell
    bob@dylan:~$ npm test 0-calcul.test.js

    > task_0@1.0.0 test /root
    > ./node_modules/mocha/bin/mocha "0-calcul.test.js"

      calculateNumber
        ✓ ...
        ...

      130 passing (35ms)
    ```

- [x] **1. Combining descriptions**
  - **Create [`1-calcul.js`](1-calcul.js):**
    - Enhance the function from the previous task.
    - Add a `type` argument that can be `SUM`, `SUBTRACT`, or `DIVIDE`.
    - Implement logic for each type.
  - **Test cases:**
    - Create a file [`1-calcul.test.js`](1-calcul.test.js) with tests for this function.
    - Assume `a` and `b` are always numbers.
    - Organize test cases using `describe`.
  - **Tips:**
    - As with previous tasks, consider edge cases.
  - **Requirements:**
    - Use `assert`.
    - Run the test suite using `npm test 1-calcul.test.js`.
    - All tests must pass without warnings.
  - **Expected output:**
    ```powershell
    > const calculateNumber = require("./1-calcul.js");
    > calculateNumber('SUM', 1.4, 4.5)
    6
    > calculateNumber('SUBTRACT', 1.4, 4.5)
    -4
    > calculateNumber('DIVIDE', 1.4, 4.5)
    0.2
    > calculateNumber('DIVIDE', 1.4, 0)
    'Error'
    ```

- [x] **2. Basic test using Chai assertion library**
  - Many developers prefer behavior-driven development for better readability and maintenance.
  - **Install Chai via npm:**
    - Copy [`1-calcul.js`](1-calcul.js) to a new file [`2-calcul_chai.js`](2-calcul_chai.js).
    - Copy [`1-calcul.test.js`](1-calcul.test.js) to [`2-calcul_chai.test.js`](2-calcul_chai.test.js).
    - Rewrite the test suite using `expect` from Chai.
  - **Tips:**
    - Maintain test coverage with readable tests to ease collaboration.
  - **Requirements:**
    - Run the test suite using `npm test 2-calcul_chai.test.js`.
    - All tests must pass without warnings.

- [x] **3. Spies**
  - Spies allow logging useful information about function calls. Use Sinon for this.
  - **Install Sinon via npm:**
    - Create a new file named [`utils.js`](utils.js) and define a module `Utils` with `calculateNumber`.
  - **Create [`3-payment.js`](3-payment.js):**
    - Define `sendPaymentRequestToApi`, calling `Utils.calculateNumber` and logging the total.
  - **Create [`3-payment.test.js`](3-payment.test.js):**
    - Use `sinon.spy` to verify the call to `Utils.calculateNumber`.
  - **Requirements:**
    - Run the test suite using `npm test 3-payment.test.js`.
    - All tests must pass without warnings.
    - Use a spy for this task.
  - **Tips:**
    - Always restore a spy after use to prevent unexpected behavior.

- [x] **4. Stubs**
  - Stubs allow custom implementations for wrapped functions. Use Sinon for stubs.
  - **Create [`4-payment.js`](4-payment.js):**
    - Copy from [`3-payment.js`](3-payment.js).
  - **Create [`4-payment.test.js`](4-payment.test.js):**
    - Stub `Utils.calculateNumber` to return `10` and verify its usage.
    - Add a spy for `console.log` to confirm correct output.
  - **Requirements:**
    - Run the test suite using `npm test 4-payment.test.js`.
    - All tests must pass without warnings.
    - Use a stub for this task.
  - **Tips:**
    - Stubs can speed up tests significantly.

- [x] **5. Hooks**
  - Hooks allow execution of functions before running tests.
  - **Copy from [`4-payment.js`](4-payment.js) to [`5-payment.js`](5-payment.js).**
  - **Create [`5-payment.test.js`](5-payment.test.js):**
    - Include two tests with `beforeEach` and `afterEach` hooks.
  - **Requirements:**
    - Run the test suite using `npm test 5-payment.test.js`.
    - All tests must pass without warnings.
    - Use only one spy.

- [x] **6. Async tests with done**
  - Learn to support async testing.
  - **Create [`6-payment_token.js`](6-payment_token.js):**
    - Define `getPaymentTokenFromAPI` with a success parameter.
  - **Create [`6-payment_token.test.js`](6-payment_token.test.js):**
    - Write a test suite for `getPaymentTokenFromAPI`.
  - **Requirements:**
    - Run the test suite using `npm test 6-payment_token.test.js`.
    - All tests must pass without warnings.
    - Use the `done` callback for async testing.

- [x] **7. Skip**
  - Use `skip` for failing tests instead of commenting them out.
  - **Use [`7-skip.test.js`](7-skip.test.js):**
    - Make the test suite pass without fixing or removing the failing test.
  - **Requirements:**
    - Run the test suite using `npm test 7-skip.test.js`.
    - All tests must pass without warnings.

- [x] **8. Basic Integration Testing**
  - In the folder [`8-api`](8-api/), copy the provided `package.json`.
  - **Create [`api.js`](api.js):**
    - Use Express to create an app listening on port 7865.
  - **Create [`api.test.js`](api.test.js):**
    - Write a suite for the index page.
  - **Requirements:**
    - Run the test suite using `yarn test 8-api/api.test.js`.
    - All tests must pass without warnings.

- [x] **9. Regex Integration Testing**
  - In the folder [`9-api`](9-api/), reuse the project from [`8-api`](8-api/).
  - **Modify [`api.js`](api.js):**
    - Add a `GET /cart/:id` endpoint.
  - **Modify [`api.test.js`](api.test.js):**
    - Add tests for the cart page.
  - **Requirements:**
    - Run the test suite using `yarn test 9-api/api.test.js`.
    - All tests must pass without warnings.

- [x] **10. Deep Equality & Post Integration Testing**
  - In the folder [`10-api`](10-api/), reuse the project from [`9-api`](9-api/).
  - **Modify [`api.js`](api.js):**
    - Add `GET /available_payments` and `POST /login` endpoints.
  - **Modify [`api.test.js`](api.test.js):**
    - Add test suites for the new endpoints.
  - **Requirements:**
    - Run the test suite using `yarn test 10-api/api.test.js`.
    - All tests must pass without warnings.