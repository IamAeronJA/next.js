Most applications need some kind of authentication mechanism to interact with data. In this module, we'll add authentication to a Next.js application, using GitHub oAuth.

Start by creating a new Next.js application:

```
npx create-next-app
```

Add the authentication module to the project:

```
npm i next-auth
```

In order to specify environment variables, use the `dotenv` module. Make sure you add `.env` to your `.gitignore` file, as it often contains secrets.
You can also use the built-in support for `.env.local` that [Next.js includes](https://nextjs.org/docs/basic-features/environment-variables).

```
npm install dotenv
```

### (optional) Install MySQL package for login session persistence

If you'd like support for a database backend, consider using MySQL. You can run a MySQL container image, although be aware that you should use MySQL version 5.7, as the `mysql` package doesn't support MySQL 8 at this time.
If you try to use MySQL 8, you'll [receive an error](https://stackoverflow.com/questions/52609940/mysql-8-er-not-supported-auth-mode/52610643) regarding mismatched authentication between the client and server.

```
npm install mysql
```

Run a MySQL v5 container:

```
docker run --detach --interactive --tty --publish 3306:3306 --env MYSQL_ROOT_PASSWORD=nextjstesting123 --name mysql mysql:5
```

Next, execute a shell inside the container, and create a database to use with `next-auth`.

```
docker exec --interactive --tty mysql bash
bash# mysql --password=nextjstesting123 --execute 'create database nextauth;'
```

### Configure the API route:

The file must be named `/pages/api/auth/[...nextauth].js`. (_Yes, the file name includes the special characters_)

* Configure the `site` value
* Add one or more OAuth providers

```
import NextAuth from 'next-auth'
import Providers from 'next-auth/providers'

const options = {
  site: 'http://localhost:3090',
  providers: [
    Providers.GitHub({
        clientId: process.env.GITHUB_ID,
        clientSecret: process.env.GITHUB_SECRET
    }),
  ],
}

export default (req, res) => NextAuth(req, res, options)
```

### Configure a sample login page:

You'll need a login page to present to the user, so they can choose what type of authentication to use. 

`pages/login.js`

```
import React from 'react'
import { 
  useSession, 
  signin, 
  signout 
} from 'next-auth/client'

export default () => {
  const [ session, loading ] = useSession()

  return <p>
    {!session && <>
      Not signed in <br/>
      <button onClick={signin}>Sign in</button>
    </>}
    {session && <>
      Signed in as {session.user.email} <br/>
      <button onClick={signout}>Sign out</button>
    </>}
  </p>
}
```

## Create GitHub OAuth App

In order to integrate your application with GitHub authentication, you'll need to create an OAuth application in the web interface.

The application ID and secret key need to be configured in your `.env` file.

Join the [CBT Nuggets Slack community](http://learn.gg/lc-ts)!
