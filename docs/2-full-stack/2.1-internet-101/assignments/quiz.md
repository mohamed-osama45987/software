# Quiz: Internet 101

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What does HTTP stand for?

- [ ] Hypertext Transmission Protocol
- [ ] Hypertext Transfer Protocol
- [ ] High Transfer Text Protocol
- [ ] Host Transfer Protocol

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "HTTP" section.
- **Think:** Two words are about moving data ("Transfer"), one is about formatting it ("Hypertext"). Match the acronym letter-by-letter.

</details>

2. In a typical frontend-backend interaction, which statement correctly describes "requests" and "responses"?

- [ ] Backends send requests; frontends send responses
- [ ] Frontends send requests to backends; backends send back responses
- [ ] Requests and responses are sent simultaneously by both sides
- [ ] Only backends can send requests to 3rd-party APIs

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "HTTP" section.
- **Think:** Who is doing the asking (client) and who is doing the answering (server)? The lesson names both roles explicitly.

</details>

3. What does a URL's port number identify?

- [ ] The country the server is located in
- [ ] Which application on a computer should receive the request
- [ ] The speed of the internet connection
- [ ] The version of HTTP being used

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → URLs".
- **Think:** A single computer can run many programs at once. The port narrows a request down from "this computer" to "this specific program on this computer".

</details>

4. Why can we usually omit the port number when typing a URL like `https://example.com`?

- [ ] Because HTTPS doesn't use ports
- [ ] Because the browser guesses the port randomly
- [ ] Because the application is using the default port for that protocol (e.g. 443 for HTTPS)
- [ ] Because ports are only used for FTP

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → URLs".
- **Think:** The lesson gives the specific default port numbers for HTTP and HTTPS. "Default" is the key word here.

</details>

5. What does an IPv4 address look like?

- [ ] A domain name like `example.com`
- [ ] Four numbers from 0–255 separated by dots, e.g. `192.158.1.38`
- [ ] A string of letters and numbers separated by colons
- [ ] A 6-digit port number

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → IP Addresses".
- **Think:** The lesson gives a concrete example address — look at its format directly.

</details>

6. Why is IPv6 being introduced alongside IPv4?

- [ ] IPv6 is faster than IPv4 for all requests
- [ ] The world is running out of available IPv4 addresses
- [ ] IPv4 doesn't support HTTPS
- [ ] IPv6 replaces the need for DNS

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → IP Addresses".
- **Think:** This is a scarcity problem, not a speed or security problem. The lesson states the reason in one sentence.

</details>

7. What is the main job of DNS?

- [ ] Encrypting requests so they can't be intercepted
- [ ] Translating domain names into IP addresses
- [ ] Storing the content of websites
- [ ] Assigning port numbers to applications

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → DNS".
- **Think:** DNS sits between something human-readable (a domain name) and something machine-routable (an address). Which direction does the translation go?

</details>

8. Why is it useful that domain names are decoupled from IP addresses via DNS?

- [ ] It makes websites load faster
- [ ] We can change which server hosts our site without changing our domain name
- [ ] It removes the need for HTTP requests entirely
- [ ] It allows multiple domains to share one port

<details>
<summary>Show hint</summary>

- **Where:** [Internet 101](../README.md) — "Internet Addressing → DNS".
- **Think:** The lesson explicitly says this decoupling is "helpful" for one specific reason related to switching infrastructure.

</details>

9. Which HTTP request method is the default and most common, triggered simply by entering a URL in the browser bar?

- [ ] POST
- [ ] DELETE
- [ ] PUT
- [ ] GET

<details>
<summary>Show hint</summary>

- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Request Method" table.
- **Think:** The table's "Notes" column for one method directly describes what happens when you visit a URL.

</details>

10. A user submits a form to create a new account. Which HTTP method would this typically use?

- [ ] GET
- [ ] POST
- [ ] DELETE
- [ ] None — forms don't use HTTP methods

<details>
<summary>Show hint</summary>

- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Request Method" table.
- **Think:** Match the table's "Purpose" column to "create an account" — which row says "Create data"?

</details>

11. A user visits a page that doesn't exist on the server. What status code would the response most likely have?

- [ ] 200
- [ ] 403
- [ ] 404
- [ ] 500

<details>
<summary>Show hint</summary>

- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Response Status Code" table.
- **Think:** The table's "Meaning" column for one status code is almost a direct quote of the scenario.

</details>

12. Why must our app's promise/callback logic assume "it will take an indefinite amount of time to receive a response" for an HTTP request?

- [ ] Because servers are intentionally slow
- [ ] Because requests travel across the internet and connectivity can be unstable
- [ ] Because JavaScript pauses all code while waiting
- [ ] Because HTTP requests are always larger than 1MB

<details>
<summary>Show hint</summary>

- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — Introduction.
- **Think:** This connects directly back to *why* Promises (Module 0) exist — what real-world property of "the internet" makes timing unpredictable?

</details>

13. What is one stated benefit of using Thunder Client to send a request, compared to testing via the app's frontend?

- [ ] It automatically writes your frontend code for you
- [ ] It helps determine whether a bug is in the API/backend or in the frontend
- [ ] It's the only way to send a GET request
- [ ] It bypasses the need for a backend entirely

<details>
<summary>Show hint</summary>

- **Where:** [HTTP Requests and Responses](../2.1.2-http-requests-and-responses.md) — "Thunder Client" section.
- **Think:** Thunder Client lets you talk to the API *directly*, with the frontend out of the picture. What kind of question does removing a variable help you answer?

</details>

14. Why does Rocket recommend disabling Chrome's cache while DevTools is open during development?

- [ ] To make the browser use less memory
- [ ] To avoid situations where the app doesn't reflect recent code changes due to cached responses
- [ ] Because the Network panel doesn't work with cache enabled
- [ ] To prevent other tabs from loading

<details>
<summary>Show hint</summary>

- **Where:** [Chrome DevTools Network Panel](../2.1.1-chrome-devtools-network-panel.md) — "Disable Cache".
- **Think:** Caching means the browser reuses an *old* response instead of fetching a *new* one. During active development, what's the risk of seeing an old response?

</details>
