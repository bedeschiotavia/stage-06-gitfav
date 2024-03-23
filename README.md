## Project Summary

This project is a single-page application developed using JavaScript that utilizes the GitHub API. 
It allows users to search for GitHub users and add them to their favorites list.
This project is part of the challenges of the Full Stack Bootcamp - Explorer by Rocketseat.

![gitfav-mockup](https://github.com/bedeschiotavia/stage-06-gitfav/assets/74593495/537eef75-04b5-4d26-b88c-d56680ddc988)


---

Below is a summary of the key JavaScript files and their functionalities:

### main.js

This file initializes the application by creating a new instance of the FavoritesView class and attaching it to the specified root element (#app).

```javascript
import { FavoritesView } from "./favorites.js"

new FavoritesView("#app")

```

### githubUsers.js

The GithubUser class provides a static method search to fetch user data from the GitHub API based on a given username.

```javascript
export class GithubUser {
  static search(username) {
    const endpoint = `https://api.github.com/users/${username}`

    return fetch(endpoint)
    .then(data => data.json())
    .then(({ login, name, public_repos, followers }) => ({
      login,
      name,
      public_repos,
      followers
    }))
  }
}
```

### favourites.js

This file contains two classes: Favorites and FavoritesView.
Favorites class manages the user's favorites list including loading, saving, adding, and deleting users. 
It utilizes localStorage to store user data locally within the browser. The load method retrieves user data from localStorage, initializing an empty array if no data is found. The save method stores user data back to localStorage whenever there are changes.

This project leverages localStorage to provide persistent storage for the user's favorites list, ensuring that the data is retained even if the user refreshes the page or closes the browser.

FavoritesView extends Favorites and handles the rendering of the favorites list in the HTML document, including adding event listeners for user interactions.


```javascript
import { GithubUser } from "./githubUser.js"

export class Favorites {
  // Constructor, load, save, add, delete methods, and other utilities
}

export class FavoritesView extends Favorites {
  // Constructor, onadd, update, createRow, removeAllTr, checkMessageNoFav methods
}
```
