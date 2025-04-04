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
2. Briefly explain different ways in which vulnerability can be exploited.
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.


1. According to http protocol, all cookies get automatically sent to a server UNLESS specifically forbidden to do so. Therefore, because the `httpOnly` and `sameSite` properties are not set, the cookies are configured so it can be used across domains. `httpOnly` means that cookies are readable programatically, which is a security issue. `sameSite` means that the cookie will only be sent to the server, and not to anyone else.
2. When the malicious link sends a post request to the server, the cookie with the session id is sent to the server as well, and the spoofer gets the session id. So any request to the server will give the client access to the session id.
3. **secure.ts** sets `httpOnly` and `sameSite` to `true`, meaning that cookies will not be sent along unless it is from the same server and http as was given the cookies.