---
layout : post
title : React⚛ MAKING THE MOVIE APP
color: rgb(242,85,44)
tags: [websolute,team,React,front-end,web,framework]
---

### Fetching Movies from API

```javascript
import React from "react";
import axios from "axios";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };
  getMovies = async () => {
    const movies = await axios.get("https://yts-proxy.now.sh/list_movies.json");
  };
  componentDidMount() {
    this.getMovies();
  }
  render() {
    const { isLoading } = this.state;
    return <div>{isLoading ? "Loading..." : "We are ready"}</div>;
  }
}
export default App;
```

<br>

### Rendering the Movies

```javascript
// src/Movie.js
import React from "react";
import PropTypes from "prop-types";

function Movie({ id, year, title, summary, poster }) {
          return <h4>{title}</h4>;
}

Movie.PropTypes = {
          id: PropTypes.number.isRequired,
          year: PropTypes.number.isRequired,
          title: PropTypes.string.isRequired,
          summary: PropTypes.string.isRequired,
          poster: PropTypes.string.isRequired
};

export default Movie;
```

```javascript
// App.js
import React from "react";
import axios from "axios";
import Movie from "./Movie";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };
  getMovies = async () => {
    const {
      data: {
        data: { movies }
      }
    } = await axios.get(
      "https://yts-proxy.now.sh/list_movies.json?sort_by=rating"
    );
    this.setState({ movies, isLoading: false });
  };
  componentDidMount() {
    this.getMovies();
  }
  render() {
    const { isLoading, movies } = this.state;
    return (
      <div>
        {isLoading
          ? "Loading..."
          : movies.map(movie => (
            <Movie
              key={movie.id}
              id={movie.id}
              year={movie.year}
              title={movie.title}
              summary={movie.summary}
              poster={movie.medium_cover_image}
            />
          ))}
      </div>
    );
  }
}
export default App;
```

### Styling the Movies

```javascript

```