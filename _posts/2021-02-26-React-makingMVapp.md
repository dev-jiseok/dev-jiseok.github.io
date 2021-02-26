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
//App.js
import React from "react";
import axios from "axios";
import Movie from "./Movie";
import "./App.css";

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
      <section class="container">
        {isLoading ? (
          <div class="loader">
            <span class="loader__text">Loading...</span>
          </div>
        ) : (
            <div class="movies">
              {movies.map(movie => (
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
          )}
      </section>
    );
  }
}
export default App;
```
```css
/*App.css*/
body {
   background-color: #f2f2f2;
 }
```

<br>

### Adding Genres

```javascript
//Movie.js
import React from "react";
import PropTypes from "prop-types";
import "./Movie.css";

function Movie({ year, title, summary, poster, genres }) {
          return (
                    <div className="movie">
                              <img src={poster} alt={title} title={title} />
                              <div className="movie__data">
                                        <h3 className="movie__title">{title}</h3>
                                        <h5 className="movie__year">{year}</h5>
                                        <ul className="genres">
                                                  {genres.map((genre, index) => (
                                                            <li key={index} className="genres__genre">
                                                                      {genre}
                                                            </li>
                                                  ))}
                                        </ul>
                                        <p className="movie__summary">{summary}</p>
                              </div>
                    </div>
          );
}
Movie.propTypes = {
          id: PropTypes.number.isRequired,
          year: PropTypes.number.isRequired,
          title: PropTypes.string.isRequired,
          summary: PropTypes.string.isRequired,
          poster: PropTypes.string.isRequired,
          genres: PropTypes.arrayOf(PropTypes.string).isRequired
};

export default Movie;
```

```javascript
//App.js
import React from "react";
import axios from "axios";
import Movie from "./Movie";
import "./App.css";
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
      <section className="container">
        {isLoading ? (
          <div className="loader">
            <span className="loader__text">Loading...</span>
          </div>
        ) : (
            <div className="movies">
              {movies.map(movie => (
                <Movie
                  key={movie.id}
                  id={movie.id}
                  year={movie.year}
                  title={movie.title}
                  summary={movie.summary}
                  poster={movie.medium_cover_image}
                  genres={movie.genres}
                />
              ))}
            </div>
          )}
      </section>
    );
  }
}
export default App;
```

```css
body {
          margin: 0;
          padding: 0;
          font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
            Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
          background-color: #eff3f7;
          height: 100%;
        }
```

<br>

### Styles Timelapse

```css
/*App.css*/
* {
          box-sizing: border-box;
        }
       
        body {
          margin: 0;
          padding: 0;
         font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
           Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
          background-color: #eff3f7;
          height: 100%;
        }
       
        html,
        body,
        #potato,
        .container {
          height: 100%;
          display: flex;
          justify-content: center;
        }
       
        .loader {
          width: 100%;
          height: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
        }
       
        .movies {
          display: flex;
          justify-content: space-between;
          align-items: flex-start;
          flex-wrap: wrap;
          padding: 50px;
          padding-top: 70px;
          width: 80%;
        }
       
        .movies .movie {
          width: 45%;
          background-color: white;
          margin-bottom: 70px;
          display: flex;
          align-items: flex-start;
          justify-content: space-between;
          font-weight: 300;
          padding: 20px;
          border-radius: 5px;
          color: #adaeb9;
          box-shadow: 0 13px 27px -5px rgba(50, 50, 93, 0.25),
            0 8px 16px -8px rgba(0, 0, 0, 0.3), 0 -6px 16px -6px rgba(0, 0, 0, 0.025);
        }
       
        .movie img {
          position: relative;
          top: -50px;
          max-width: 120px;
          margin-right: 30px;
          box-shadow: 0 30px 60px -12px rgba(50, 50, 93, 0.25),
            0 18px 36px -18px rgba(0, 0, 0, 0.3), 0 -12px 36px -8px rgba(0, 0, 0, 0.025);
        }
       
        .movie .movie__title,
        .movie .movie__year {
          margin: 0;
          font-weight: 300;
        }
       
        .movie .movie__title {
          margin-bottom: 5px;
          font-size: 24px;
          color: #2c2c2c;
        }
       
        .movie .movie__genres {
          list-style: none;
          padding: 0;
          margin: 0;
          display: flex;
          margin: 5px 0px;
        }
       
        .movie__genres li,
        .movie .movie__year {
          margin-right: 10px;
          font-size: 14px;
        }
```

<br>

### Cutting the summary

```css
/*App.css*/
* {
          box-sizing: border-box;
        }
       
        body {
          margin: 0;
          padding: 0;
         font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
           Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
          background-color: #eff3f7;
          height: 100%;
        }
       
        html,
        body,
        #potato,
        .container {
          height: 100%;
          display: flex;
          justify-content: center;
        }
       
        .loader {
          width: 100%;
          height: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
          font-weight: 300;
        }
       
        .movies {
          display: flex;
          justify-content: space-between;
          align-items: flex-start;
          flex-wrap: wrap;
          padding: 50px;
          padding-top: 70px;
          width: 80%;
        }
       
        .movies .movie {
          width: 45%;
          background-color: white;
          margin-bottom: 70px;
          display: flex;
          align-items: flex-start;
          justify-content: space-between;
          font-weight: 300;
          padding: 20px;
          border-radius: 5px;
          color: #adaeb9;
          box-shadow: 0 13px 27px -5px rgba(50, 50, 93, 0.25),
            0 8px 16px -8px rgba(0, 0, 0, 0.3), 0 -6px 16px -6px rgba(0, 0, 0, 0.025);
        }
       
        .movie img {
          position: relative;
          top: -50px;
          max-width: 160px;
          margin-right: 30px;
          box-shadow: 0 30px 60px -12px rgba(50, 50, 93, 0.25),
            0 18px 36px -18px rgba(0, 0, 0, 0.3), 0 -12px 36px -8px rgba(0, 0, 0, 0.025);
        }
       
        .movie .movie__title,
        .movie .movie__year {
          margin: 0;
          font-weight: 300;
        }
       
        .movie .movie__title {
          margin-bottom: 5px;
          font-size: 24px;
          color: #2c2c2c;
        }
       
        .movie .movie__genres {
          list-style: none;
          padding: 0;
          margin: 0;
          display: flex;
          margin: 5px 0px;
        }
       
        .movie__genres li,
        .movie .movie__year {
          margin-right: 10px;
          font-size: 14px;
        }
```
