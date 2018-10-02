---
layout: post
title:  "[React] Error Handling"
author: "Yena Park"
---

The error handling can happen on two levels

## Application level
We need to install apollo-link-error for this. And also need apollo-link for combining two links.
```javascript
import { onError } from 'apollo-link-error';

const errorLink = onError(({ graphQLErrors, networkError }) => {
  if (graphQLErrors) {
    //do something with graphql error
  }
  if (networkError) {
    //do something with network error
  }
});

const link = ApolloLink.from([errorLink, httpLink]);

const client = new ApolloClient({
  link,
  cache,
});
```

## Query/mutation level
```javascript
import RepositoryList from '../Repository';
import Loading from '../Loading';
import ErrorMessage from '../Error';
.
.
.
const Profile = () => (
  <Query query={GET_REPOSITORIES_OF_CURRENT_USER}>
    {({data, loading, error}) => {
      if (error) {
        return <ErrorMessage error={error} />;
      }
      const { viewer } = data;

      if(loading || !viewer) {
        return <Loading />;
      }

      return <RepositoryList repositories={viewer.repositories} />;
    }}
  </Query>
);
```
Whereas the ErrorMessage component could look like the following:
```javascript
import React from 'react';

import './style.css';

const ErrorMessage = ({ error }) => (
  <div className="ErrorMessage">
    <small>{error.toString()}</small>
  </div>
);

export default ErrorMessage;
```
