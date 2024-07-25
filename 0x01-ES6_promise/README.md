# PROMISEs

### Promises: Handling Asynchronous Operations
JavaScript is single-threaded, meaning it can only execute one task at a time. However, many web applications involve asynchronous operations like fetching data from an API, which takes time. Promises provide a mechanism to handle these situations gracefully.

A Promise represents the eventual completion (or failure) of an asynchronous operation. It's like an IOU (I Owe You) - a placeholder for a future value. It can be in three states:

1. Pending: The initial state, indicating the operation is ongoing.
2. Fulfilled: The operation succeeded, and the Promise holds the resulting value.
3. Rejected: The operation failed, and the Promise holds the error reason.
