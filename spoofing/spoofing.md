# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
Insecure.ts stores the cookie publicly in document, allowing the cookie to be accessed across other windows.
It can be accessed programmicatliy, through querying the dom for the cookie.
2. Briefly explain different ways in which vulnerability can be exploited.
The cookie can be queried and used for a post request/get request if the cookie is publicly available across domains. The cookie can also be taken through links when the user access malacious domains. Also the secret is not hashed, and its a text string hard coded in the session.
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
secure.ts uses a secure middleware that ensure that cookie will not be publicly available across domains, and 
it will check for a route if a cookie session id is present. It also ensures cookie will be sent in requests only for the same site. We take the secret from a command line argument, or an environment variable not part of source code.