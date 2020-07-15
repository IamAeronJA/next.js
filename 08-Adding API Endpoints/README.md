## Adding API Endpoints to Next.js

API endpoints exist under the `/pages/api` directory. Simply create a new file and export a function that sends a response using the Node.js `http.ServerResponse`.
Your function should accepts a request and response object as input.

```
export default (request, response) => {
    // Send a response here
}
```

### Handling HTTP Methods

To handle a specific HTTP method, such as `GET`, `POST`, or `HEAD`, you can add a conditional statement to your function.

```
export default (request, response) => {
    if (request.method == 'POST') {
        response.end('Done')
    }
    else {
        throw `Method ${request.method} not supported`
    }
}
```

### Dynamic Routes

Callers of your API can pass parameters as segments of the URL path component. These are known as dynamic routes.
For example, consider that you want to retrieve the value of an environment variable, using following HTTP request:
```
GET http://localhost:3090/project/[projectId]
```

You could implement this using the following function in a file named `/pages/api/project/[id].js`.
Note that the `request.query.id` property contains the value passed into the route.

```
var projectList = [
    {
        id: 100,
        name: "Finance",
        members: ['Bob', 'Doug', 'Joe', 'Bill']
    },
    {
        id: 101,
        name: "Human Resources",
        members: ['Sally', 'Jill', 'Joe', 'Nancy']
    }
]

export default (request, response) => {
    if (request.method == 'GET') {
        response.send(projectList.findIndex(val => val.id == request.query.id))
    }
    else {
        throw `Method ${request.method} not supported`
    }
}
```

### Catch-all for Dynamic Routes

What happens if someone issues the following request to your API?

```
GET http://localhost:3090/project/100/101 
```

In RESTful design, this wouldn't be a good option, however you could retrieve multiple project IDs using URL path segments.

`[...projects].js`

```
export default (req, res) => {
    
}
```

## Learning Points

* APIs are created by exporting a default function, accepting a request & response
* Dynamic routes can accept parameter values via URL path segments