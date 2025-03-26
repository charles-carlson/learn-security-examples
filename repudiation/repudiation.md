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
There is no tracking of actions from a user, and requests do not have any authorization. If the user wants to send a malacious request, the system would not be able to track how the malacious request happen.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
secure.ts uses a middleware that tracks every action from a user that includes ip, url, and method. This ensure that if there is an attack they know where it came from.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works? Uses a single chain of responsiblity pattern, the middleware pattern, so during every request, the middlware will pick up the request data from a user so that it knows if there is an attack, it knows where it came from.