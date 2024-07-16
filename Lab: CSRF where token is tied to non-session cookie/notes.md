Cred:
wiener:peter
carlos:montoya


wiener:peter
csrfkey: OtqfBDHxT1DdyuBJof0rwjRKEB4LtkYW
csrf: GVtp4B1WDGPOAog0Uq4x0zQ4X5PTE2sG
session: iprKxuLAdX4AYUJ2NXcJL61yjQQGsloG


carlos:montoya
csrfKey: kpduN3DjdRN8DdscyB7r74uzap1EXk93
csrf: hYQ1fJo0qfjYzcJrfOrATbjnqAVTUy9C
session: eeU2LrOeDToNBQBqEOvAvhs2bwhzSyai


- csrf token can be reuse
    - check of it can be used by other user 
- requires both csrfkey and csrf token 
- invalid session cookie logs user out
- session key is tied to user 
- csrfkey and csrf token works even if session key belong to a different user 
    - csrf token can be reused other user


- search result get added to cookie 
    - check for CRLF injection (%0D%0A)
    - test payload - `?search=test;%0D%0ASet-Cookie%3A%20test%3Dinjection`

#### exploit

carlos:montoya
csrfKey: kpduN3DjdRN8DdscyB7r74uzap1EXk93
csrf: hYQ1fJo0qfjYzcJrfOrATbjnqAVTUy9C

- Inject csrfKey using `/?search` CRLF vulnerability 
    - payload - `?search=test;%0D%0ASet-Cookie%3A%20csrfKey%3DkpduN3DjdRN8DdscyB7r74uzap1EXk93`
- Craft csrf payload using the csrf token 


http://127.0.0.1:5500/Lab:%20CSRF%20where%20token%20is%20tied%20to%20non-session%20cookie/exploit.html
