# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
In the form in the '/' route, the form can accept any given text, this includes scripts and other malicious code. There is no sanitizer for text in the form, this allows an attacker to have the server run their own script or add their own changes to the dom of the site.
2. Briefly explain how a malicious attacker can exploit them.
The attacker can supply a script to the form which it would intake, and can cause the dom of site to 
make those changes once posted to the server.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
secure.ts has a sanitizer function that will clean the text with quotations if it notices unusual characters
so that an attacker ingesting script will do nothing on the server.