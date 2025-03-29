# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?


1. neither sending nor getting/retrieving messages requires authentication. In addition, the messages are logged on the console, which means anyone can see anyone's messages.
2. in secure.ts, there is "working" user authentication, and logging is saved to a local server log file that is not visible from a client side. This protects messages from being seen by anyone.
3. the secure version uses middleware. So before any requests to the server are handled, the time, request method, and user (ip address) are logged. This makes it so we can see in the server log if anyone is trying to access a message they shouldn't.