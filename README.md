# Cookie Handler

A simple and flexible cookie handler for JavaScript and TypeScript projects.

## Installation

To install the package, run:

```bash
npm install cookie-handler-pro
or
npm i cookie-handler-pro
```

## Usage

#### Setting a Cookie

To set a cookie, import the setCookie function and use it with the desired options.

```bash
import { setCookie } from 'cookie-handler-pro';

// Set a cookie with various options
setCookie('username', 'john_doe', {
  expires: '7d', // Expires in 7 days
  path: '/',
  domain: 'example.com',
  secure: true,
  sameSite: 'Lax'
});

// Set a cookie to expire in 2 hours
setCookie('session', 'abcd1234', {
  expires: '2h',
  path: '/'
});
```

#### Getting a Cookie

To get a cookie, import the getCookie function and use it with the cookie name.

```bash
import { getCookie } from 'cookie-handler-pro';
const username = getCookie('username');
console.log(username); // Output: 'john_doe'
```

#### Deleting a Cookie

To delete a cookie, import the deleteCookie function and use it with the cookie name and options.

```bash
import { deleteCookie } from 'cookie-handler-pro';
deleteCookie('username', { path: '/', domain: 'example.com' });
```

## Usage in Next.js

#### Setting a Cookie in Next.js

To set a cookie in a Next.js project, you can use the setCookie function within your API routes or in your components. Here’s an example of setting a cookie in an API route:

```bash
// pages/api/set-username.ts
import { NextApiRequest, NextApiResponse } from 'next';
import { setCookie } from 'cookie-handler-pro';

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  setCookie('username', 'john_doe', {
    expires: '7d',
    path: '/',
    domain: req.headers.host,
    secure: process.env.NODE_ENV === 'production',
    sameSite: 'Lax'
  });

  res.status(200).json({ message: 'Cookie set successfully' });
}
```

#### Getting a Cookie in Next.js

To get a cookie in a Next.js project, you can use the getCookie function within your components or in your API routes. Here’s an example of getting a cookie in a component:

```bash
// pages/index.tsx
import { useEffect, useState } from 'react';
import { getCookie } from 'cookie-handler-pro';

const HomePage = () => {
  const [username, setUsername] = useState<string | null>(null);

  useEffect(() => {
    const cookieValue = getCookie('username');
    setUsername(cookieValue);
  }, []);

  return <div>Username: {username}</div>;
};

export default HomePage;
```

#### Deleting a Cookie in Next.js

To delete a cookie in a Next.js project, you can use the deleteCookie function within your API routes or in your components. Here’s an example of deleting a cookie in an API route:

```bash
// pages/api/delete-username.ts
import { NextApiRequest, NextApiResponse } from 'next';
import { deleteCookie } from 'cookie-handler-pro';

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  deleteCookie('username', { path: '/', domain: req.headers.host });

  res.status(200).json({ message: 'Cookie deleted successfully' });
}
```

#### Next.js App route

You can test in your Next.js application

```bash
"use client";

import { getCookie, setCookie, deleteCookie } from "cookie-handler-pro";

export default function Home() {
  const handleSetCookie = () => {
    setCookie("username", "john_doe", {
      expires: "7d",
      path: "/",
      domain: window.location.hostname, // Use window.location.hostname instead of req.headers.host
      secure: process.env.NODE_ENV === "production",
      sameSite: "Lax",
    });
  };
  const handleDeleteCookie = () => {
    deleteCookie("username");
  };
  const value = getCookie("username");
  return (
    <>
      <button onClick={handleSetCookie}>Set Cookie</button>
      <br />
      <button onClick={handleDeleteCookie}>deleted Cookie</button>
      <h1>Cookies: {value}</h1>
    </>
  );
}

```

#### Author: [N R SHAGOR](http://nrshagor.com "N R SHAGOR")

#### License: MIT
