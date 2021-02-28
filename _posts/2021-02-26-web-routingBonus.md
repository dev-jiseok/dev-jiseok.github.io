---
layout : post
title : React⚛ ROUTING BONUS
color: rgb(242,85,44)
tags: [websolute,team,React,front-end,web,framework]
---


react-router dom 을 설치해 네비게이션을 만들어 준다.
react-router dom을 통해 ```<Home.js>```와 ```<About.js>```에 접근하는 방법을 알아본다.

{% raw %}
```javascript
//Home.js
import React from "react";
import axios from "axios";
import Movie from "../components/Movie";
import "./Home.css";

class Home extends React.Component {
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

export default Home;
```
{% endraw %}

{% raw %}
```javascript
//Movie.js
import React from "react";
import { Link } from "react-router-dom";
import PropTypes from "prop-types";
import "./Movie.css";

function Movie({ id, year, title, summary, poster, genres }) {
          return (
                    <div className="movie">
                              <Link
                                        to={{
                                                  pathname: `/movie/${id}`,
                                                  state: {
                                                            year,
                                                            title,
                                                            summary,
                                                            poster,
                                                            genres
                                                  }
                                        }}
                              >
                                        <img src={poster} alt={title} title={title} />
                                        <div className="movie__data">
                                                  <h3 className="movie__title">{title}</h3>
                                                  <h5 className="movie__year">{year}</h5>
                                                  <ul className="movie__genres">
                                                            {genres.map((genre, index) => (
                                                                      <li key={index} className="genres__genre">
                                                                                {genre}
                                                                      </li>
                                                            ))}
                                                  </ul>
                                                  <p className="movie__summary">{summary.slice(0, 180)}...</p>
                                        </div>
                              </Link>
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
{% endraw %}

{% raw %}
```javascript
//Detail.js

import React from "react";

class Detail extends React.Component {
          componentDidMount() {
                    const { location, history } = this.props;
                    if (location.state === undefined) {
                              history.push("/");
                    }
          }
          render() {
                    const { location } = this.props;
                    if (location.state) {
                              return <span>{location.state.title}</span>;
                    } else {
                              return null;
                    }
          }
}
export default Detail;
```
{% endraw %}

{% raw %}
```javascript
//Navigation.js
import React from "react";
import { Link } from "react-router-dom";
import "./Navigation.css";

function Navigation() {
          return (
                    <div className="nav">
                              <Link to="/">Home</Link>
                              <Link to="/about">About</Link>
                    </div>
          );
}

export default Navigation;
```
{% endraw %}

{% raw %}
```javascript
//App.js
import React from "react";
import { HashRouter, Route } from "react-router-dom";
import Home from "./routes/Home";
import About from "./routes/About";
import Detail from "./routes/Detail";
import Navigation from "./components/Navigation";
import "./App.css";

function App() {
  return (
    <HashRouter>
      <Navigation />
      <Route path="/" exact={true} component={Home} />
      <Route path="/about" component={About} />
      <Route path="/movie/:id" component={Detail} />
    </HashRouter>
  );
}

export default App;
```
{% endraw %}

{% raw %}
```css
/*Home.css*/
        .container {
          height: 100%;
          display: flex;
          justify-content: center;
        }
       
        .loader {
          width: 100%;
          height: 100vh;
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
{% endraw %}

{% raw %}
```css
/*Navigation.css*/
.nav {
          position: fixed;
          top: 50px;
          left: 10px;
          display: flex;
          flex-direction: column;
          background-color: white;
          padding: 10px 20px;
          box-shadow: 0 13px 27px -5px rgba(50, 50, 93, 0.25),
            0 8px 16px -8px rgba(0, 0, 0, 0.3), 0 -6px 16px -6px rgba(0, 0, 0, 0.025);
          border-radius: 5px;
        }
       
        .nav a {
          text-decoration: none;
          color: #0008fc;
          text-transform: uppercase;
          font-size: 12px;
          text-align: center;
          font-weight: 600;
        }
       
        .nav a:not(:last-child) {
          margin-bottom: 20px;
        }       
```
{% endraw %}

{% raw %}
```css
/*Movie.css*/
.movies .movie {
  width: 45%;
  background-color: white;
  margin-bottom: 70px;
  font-weight: 300;
  padding: 20px;
  border-radius: 5px;
 color: #adaeb9;
 box-shadow: 0 13px 27px -5px rgba(50, 50, 93, 0.25),
    0 8px 16px -8px rgba(0, 0, 0, 0.3), 0 -6px 16px -6px rgba(0, 0, 0, 0.025);
}

.movies .movie a {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  text-decoration: none;
  color: inherit;
}

.movie img {
  position: relative;
  top: -50px;
 max-width: 150px;
 width: 100%;
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
{% endraw %}

{% raw %}
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
```
{% endraw %}

완성 코드들..
