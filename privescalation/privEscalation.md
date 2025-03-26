# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
Insecure.ts does not use a session for the user using the server, and also does not check privileges when the user makes a request to the server. There is an absence of authorization.
2. Briefly explain how a malicious attacker can exploit them.
The attacker can send form data to change the roles of other users by guessing their user ids, and they can submit the request successfully since there is no session data managing their access level.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
Secure.ts uses a session to ensure the user is authorized to submit a request, and ensures they cannot change any other uses's level of privilege.