---
title: "Understanding GraphQL"
date: "2020-12-01"
description: A beginner's guide to client-side GraphQL. You'll learn about what is GraphQL? why GraphQL? and how is it better than REST?
---

### What is GraphQL?

I first thought it was a type of database, which is a common misconception. It is not a database.

According to their documentation,

> GraphQL is a query language for your API, and a server-side runtime for executing queries by using a type system you define for your data. GraphQL isn't tied to any specific database or storage engine and is instead backed by your existing code and data.

This is just a fancy way of saying GraphQL, irrespective of what you use for the frontend and backend, lets you

- assign types to the data you fetch on the server-side.
- fetch only the data you need from the API endpoint.

Imagine you have the following API endpoint `users/<id>/posts` with data about posts, and you only want to display all the titles in the UI.

```
{
 posts:[{
     "id": "kjulhion34js",
     "title" : "GraphQL Rocks!",
     "content": "Lorem ipsum...",
     "comments": [...]
 },
 {
     "id": "jeidknrc23ps",
     "title": "GraphQL is the Best!",
     "content": "Lorem ipsum...",
     "comments": [...]
 },
  {
     "id": "msoled37hn9o",
     "title": "GraphQL is way better than REST",
     "content": "Lorem ipsum...",
     "comments": [...]
 },
 ]
}
```

With REST, you would have to fetch this whole JSON data to show only the titles. However, with GraphQL you can query for the titles directly using the following:

```
query {
     User(id:'alijnhus2yu3'){
        posts {
            title
        }
     }
}
```

Hence, GraphQL enables **declarative data fetching**, which means we can specify what data we want to fetch.
In Addition to this, GraphQL exposes only a single endpoint for all the data.

Let's say you need a user's name along with his posts.

- The REST way would be to use to `fetch` calls with different endpoints `users/<id>` and `users/<id>/posts` and get all the data from both endpoints.
- The GraphQL way is to use the same endpoint for both and fetch only required data.

```
query {
    User(id:'alijnhus2yu3') {
        name
        posts {
            title
        }
    }
}
```

### Why GraphQL?

- enables efficient data loading for mobile usage by keeping the data to be transferred over the network to a minimum.
- supports different client frameworks seamlessly.
- helps in faster feature development because of its efficient yet, flexible nature.

### How is it better than REST?

This section is a recap of what we have seen so far.

- The static nature of REST hinders rapid development when client-side requirements change. GraphQL, on the other hand, is adaptive since new endpoints according to the client's needs aren't required. The only modification needed is on the queries defined with the same endpoint.

- Using REST leads to overfetching and underfetching of data. Overfetching is when we get extra data. Underfetching happens when we need multiple requests on different endpoints to get all the necessary data.

- Another advantage of GraphQL is its Schema and Types. Once these are agreed upon, they serve as a _contract_ between client and server. Then, frontend and backend teams can work independently.

- Finally, it reduces the steps needed on the client side (4 are reduced to 2)
<style>
table, tr, td, th {
    border: 1px solid black;
    padding: 10px 30px;
}
table {
    border-collapse: collapse;
}
th{
    text-align:center;
}

</style>

  <table>
  <tr>
  <th>REST</th>
  <th>GraphQL</th>
  </tr>
  <td>
  <ol>
  <li>construct and send HTTP request </li>
  <li>receive and parse server reponse</li>
  <li>store data locally</li>
  <li>display info in UI</li>
  </ol>
  </td>
  <td>
  <ol>
  <li>construct and send HTTP request </li>
  <li>display info in UI</li>
  </ol>
  </td>
  </tr>
  </table>

That's it for this one. In my next blog, I will cover the graphQL concepts in form of a "hands-on" tutorial using the [Rick and Morty API](https://rickandmortyapi.com/graphql)

### Resources

- https://www.howtographql.com/
- https://graphql.org/
