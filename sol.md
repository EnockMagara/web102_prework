# Web Development 102 Prework: Sea Monster Crowdfunding

## Project Overview

This project involved creating a website for Sea Monster Crowdfunding, a company that funds indie games. The website displays information about the games they have funded, including statistics and filtering options.

## Challenge Solutions and Logic

### Challenge 1: Introduction to Sea Monster Crowdfunding
**Secret Key:** Seaworthy

This challenge introduced the concept of the project and set up the basic structure of the website.

**Solution Logic:**
- Created the initial HTML structure for the website
- Set up a CSS file for basic styling
- Initialized a JavaScript file to handle dynamic content

### Challenge 2: Create the Dashboard
**Secret Key:** OOZEdiveTRAPpine

In this challenge, I created the dashboard section of the website, displaying key statistics about the funded games.

**Solution Logic:**
- Created a dashboard container in HTML
- Used JavaScript to calculate total contributions, total amount raised, and number of games
- Dynamically inserted these statistics into the dashboard using DOM manipulation
- Styled the dashboard for better visual presentation

### Challenge 3: Add Games to the Page
**Secret Key:** 6games-container.stats-card15

This challenge involved dynamically adding game information to the page using JavaScript.

**Solution Logic:**
- Created a container element with id "games-container"
- Implemented a function to create game cards:
  ```javascript
  function addGamesToPage(games) {
    games.forEach(game => {
      const gameCard = document.createElement("div");
      gameCard.classList.add("game-card");
      gameCard.innerHTML = `
        <img src="${game.img}" alt="${game.name}">
        <h3>${game.name}</h3>
        <p>${game.description}</p>
        <p>Pledged: $${game.pledged.toLocaleString()}</p>
        <p>Goal: $${game.goal.toLocaleString()}</p>
      `;
      gamesContainer.appendChild(gameCard);
    });
  }
  ```
- Called this function with the GAMES_JSON data to populate the page

### Challenge 4: Use reduce() to Get Website Stats
**Secret Key:** 11seafoamGAMES_JSON

In this challenge, I used the reduce() method to calculate and display overall statistics for the funded games.

**Solution Logic:**
- Used reduce() to calculate total contributions and total amount raised:
  ```javascript
  const totalContributions = GAMES_JSON.reduce((total, game) => total + game.backers, 0);
  const totalRaised = GAMES_JSON.reduce((total, game) => total + game.pledged, 0);
  ```
- Updated the dashboard with these calculated values

### Challenge 5: Add Filters to Show Certain Games
**Secret Key:** 19187800268BRAIN

This challenge required implementing filter functionality to display games based on their funding status.

**Solution Logic:**
- Created filter buttons in HTML
- Implemented filter functions using the filter() method:
  ```javascript
  function filterUnfundedOnly() {
    const unfundedGames = GAMES_JSON.filter(game => game.pledged < game.goal);
    addGamesToPage(unfundedGames);
  }

  function filterFundedOnly() {
    const fundedGames = GAMES_JSON.filter(game => game.pledged >= game.goal);
    addGamesToPage(fundedGames);
  }
  ```
- Added event listeners to the filter buttons to call these functions

### Challenge 6: Add More Information at the Top of the Page
**Secret Key:** 74FLANNELclick

In this challenge, I added more detailed information to the top of the page, including the number of funded and unfunded games.

**Solution Logic:**
- Calculated the number of unfunded games:
  ```javascript
  const unfundedGamesCount = GAMES_JSON.filter(game => game.pledged < game.goal).length;
  ```
- Created a description string using template literals and the ternary operator:
  ```javascript
  const unfundedDescription = `There are currently ${unfundedGamesCount} game${unfundedGamesCount === 1 ? '' : 's'} that ${unfundedGamesCount === 1 ? 'has' : 'have'} not yet met ${unfundedGamesCount === 1 ? 'its' : 'their'} funding goal.`;
  ```
- Added this information to the page using DOM manipulation

### Challenge 7: Select & Display the Top 2 Games
**Secret Key:** ZooHowCEDAR

The final challenge involved identifying and displaying the top two most funded games.

**Solution Logic:**
- Sorted the games array based on the pledged amount:
  ```javascript
  const sortedGames = GAMES_JSON.sort((a, b) => b.pledged - a.pledged);
  ```
- Used destructuring to get the top two games:
  ```javascript
  const [firstGame, secondGame] = sortedGames;
  ```
- Created elements to display these top games and added them to the page

## Key Learnings and Techniques Used

- **Array Methods:** Extensive use of reduce(), filter(), and sort() for data manipulation
- **DOM Manipulation:** Dynamic creation and modification of HTML elements using JavaScript
- **Template Literals:** Used for creating complex strings with embedded expressions
- **Event Handling:** Implemented click events for interactive filtering
- **Destructuring:** Applied to extract specific data from arrays and objects
- **Ternary Operator:** Used for concise conditional statements, especially in string formatting
- **toLocaleString():** Applied for formatting currency values
- **Arrow Functions:** Utilized for concise function expressions, especially in array methods

## Conclusion

This project provided hands-on experience with core web development concepts, emphasizing JavaScript's power in creating dynamic and interactive web pages. The implementation of features like dynamic content loading, statistical calculations, and filtering demonstrated the practical application of array methods and DOM manipulation techniques.