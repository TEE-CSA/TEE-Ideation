---
title: jQuery and CRUD Principles Lesson Overview
description: Our lesson on jQuery and CRUD!
type: plan
courses: {'csa': {'week': 15}}
---

# Overview of Today's Lesson

- jQuery
    - What is jQuery?
    - What is jQuery used for?
    - Demonstration of application in markdown and HTML tables
        - Be able to explain similarities and/or differences between markdown and HTML tables
- CRUD principles
    - What does CRUD stand for?
    - How can CRUD be applied to jQuery and beyond?
    - Show demonstration of applying CRUD to tables created
- Hacks (tentative)
    - A quiz that covers the concepts taught 
    - Creating their own table with jQuery and explaining how it works
    - Extra: create something completely unique using jQuery and CRUD, explaining how the project applies the two

# What is jQuery?

Any volunteers?

Essentially, jQuery is a library that allows us to use some of JavaScript's built in functions. Think of it as one of the lines you could see at the very top of a code file along with many other import statements. 

## Benefits of jQuery

Some benefits of jQuery include but are not limited to:

- Makes it easier for us to write JavaScript and HTML code
- Very flexible in terms of which browsers it can work on
- Simplifies some of the most common JavaScript functions into fewer lines of code

**Question:** What are some real life applications of jQuery? Name at least two you can think of. 

## Basic Syntax

Whenever you are working with jQuery, the most basic format you will you use is the following:

```$(selector).action()```

Some examples of these include:

```$(this).hide()``` - hides the current element.


```$("p").hide()``` - hides all <p> elements.


```$(".test").hide()``` - hides all elements with class="test".


```$("#test").hide()``` - hides the element with id="test".

## Using JQuery with APIs

Using an online movie database

<html>
<head>
  <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.25/css/jquery.dataTables.min.css">
    <style>
    body {
      font-family: Arial, sans-serif;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    form {
      margin-bottom: 20px;
    }
    input[type="text"] {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      border-radius: 4px;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      cursor: pointer;
    }
    .movie-container {
      margin-bottom: 20px;
    }
    .movie-series-table {
      width: 100%;
      border-collapse: collapse;
    }
    .movie-series-table th,
    .movie-series-table td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }
    .movie-series-table th {
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>
  <h1>Movie Search</h1>

  <h2>Search for a Movie Series</h2>
  <form id="seriesForm">
    <input type="text" id="seriesInput" placeholder="Enter series title">
    <button type="submit">Search</button>
  </form>
  <div id="seriesContainer"></div>

  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="https://cdn.datatables.net/1.10.25/js/jquery.dataTables.min.js"></script>
  <script>
    function fetchMovieSeriesData(seriesTitle) {
      var apiUrl = "https://api.themoviedb.org/3/search/movie?api_key=5f87798890b72c6ac53b262ba43ed8c6&query=" + encodeURIComponent(seriesTitle); 
      var request = new XMLHttpRequest(); // requests data
      request.open("GET", apiUrl, true); // fetches the data from the url
      request.onload = function() { 
        if (request.status === 200) { // if request is successful - more specific than before
          var data = JSON.parse(request.responseText); // JS variable from JSON data
          fetchSeriesMovieData(data);
        } else {
          document.getElementById("seriesContainer").textContent = "Error fetching movie series data.";
        }
      };
      request.onerror = function() {
        document.getElementById("seriesContainer").textContent = "Error fetching movie series data.";
      };
      request.send();
    }
    function fetchSeriesMovieData(data) {
      if (data.results && data.results.length > 0) { // checks that data contains info and is not empty
        var movieSeries = data.results;
        var creditsDataPromises = movieSeries.map(function(movie) { // creates an array of promises, which each fetch data for a movie in the series through a separate API request
          var apiUrl = "https://api.themoviedb.org/3/movie/" + movie.id + "/credits?api_key=5f87798890b72c6ac53b262ba43ed8c6";
          return fetch(apiUrl).then(function(response) { // each request from each promise
            return response.json();
          });
        });
        Promise.all(creditsDataPromises).then(function(creditsData) { // All promises are resolved and a new function is called with the movies series and the data
          displayMovieSeriesData(movieSeries, creditsData);  
        }).catch(function(error) { // if an error appears
          document.getElementById("seriesContainer").textContent = "Error fetching movie series data.";
        });
      } else {
        document.getElementById("seriesContainer").textContent = "No movie series found.";
      }
    }
    function displayMovieSeriesData(movieSeries, creditsData) {
      var table = document.createElement("table"); // creates a JS table
      table.classList.add("movie-series-table"); // styles the table
      var tableHeader = table.createTHead(); // a header is created 
      var headerRow = tableHeader.insertRow(); // Rows are added to the table
      var columns = ["Title", "Popularity", "Vote Count", "Vote Average", "Poster"]; // column titles
      for (var i = 0; i < columns.length; i++) { // iterates through column array and continues until i is greater than length of columns
      // basically, rows are created for every column
        var th = document.createElement("th"); // rows are added underneath the headers
        th.textContent = columns[i]; // data is added to the rows
        headerRow.appendChild(th); // the rows are displayed
      }
      var tableBody = table.createTBody(); // the body of the table is created
      for (var j = 0; j < movieSeries.length; j++) { // another for loop but iterates through the data
      // this way, every single row with contain data since the loop stops once all the data is iterated through
        var movie = movieSeries[j]; // the data is assigned to a variable
        var row = tableBody.insertRow(); // rows are added to the body
        var titleCell = row.insertCell(); 
        titleCell.textContent = movie.title; // the title is displayed in new cells at the rows
        var popularityCell = row.insertCell();
        popularityCell.textContent = movie.popularity; // the popularity is displayed
        var voteCountCell = row.insertCell();
        voteCountCell.textContent = movie.vote_count; // the vote count is displayed
        var voteAverageCell = row.insertCell();
        voteAverageCell.textContent = movie.vote_average; // the vote average is displayed
        var posterCell = row.insertCell();
        var posterImage = document.createElement("img");
        posterImage.src = "https://image.tmdb.org/t/p/w200" + movie.poster_path;
        posterImage.alt = "Movie Poster";
        posterCell.appendChild(posterImage);
      }
      document.getElementById("seriesContainer").appendChild(table);
      $('.movie-series-table').DataTable();
    } 
    document.getElementById("seriesForm").addEventListener("submit", function(event) {
      event.preventDefault();
      var seriesTitle = document.getElementById("seriesInput").value;
      fetchMovieSeriesData(seriesTitle);
    });
  </script>
</body>
</html>

