# Rest API Demo With Concurrent Requests

API is implemented in NodeJS using express 

In this repo, we are going to demonstrate the use of handling multiple requests of the same payload and how we can make sure to avoid duplicate creation of the same resource. Please refer to the [Article]() for the explanation.

# How to run

Make sure to have node installed

`npm install -g nodemon` => Make sure to install this globally.

`git clone <repo>` from Github

`> npm i`

`> npm run dev`

Go to Postman or any http client tool and try to perform the following request multiple times

```
POST http://localhost:3000/api/payments
{
    "user_id": 1234,
    "order_id": "1234-567-xq34343",
    "status": "SUCCESS",
    "amount": 100,
    "transaction_id": "T23232323"
}
```

In the database we should have only one payments entry for the above user and rest of them should be ignored.
How we manage with ignored calls its left upto us. Either we can log them or store them in another table for auditing.

The concurrent rest calls are also demonstrated in the e2e tests. Check out `test/e2e/payments.js` file.

## Tests

### End-to-end (e2e) Tests

Make sure to install mochal globablly `npm install mocha -g`

Make sure to create a database name and configure the db credentials in `config.js`


`> npm run test:e2e`

In the e2e tests `test/e2e/payments.js`, there is a demonstration of making concurrent calls to the same endpoint.



### References

https://60devs.com/synchronization-of-concurrent-http-requests-in-node.html

https://60devs.com/making-better-http-apis.html

https://stackoverflow.com/questions/129329/optimistic-vs-pessimistic-locking

https://blog.couchbase.com/optimistic-or-pessimistic-locking-which-one-should-you-pick/
