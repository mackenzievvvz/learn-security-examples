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
2. Briefly explain how a malicious attacker can exploit them.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?

1. the logic in insecure.ts first does not take into account logged in/authenticated users. it also doesn't check the client's the session, which may differ from the requested user.
2. if a malicious attacker knows the user id of some other admin, they can change the role of that person without any checks.
3. secure.ts checks that the session is for a logged in admin. This means that only admin can make update role requests to a user.