# Football Team Cards

A small web app that displays the 1986 Argentina World Cup squad as player cards and lets you filter them by position or by players who have nicknames. Built to practice modern JavaScript methods like `map`, `filter`, destructuring, and DOM manipulation.

## Demo

The page shows:

- Team-level stats (team name, sport, year, head coach).
- A dropdown to filter teammates.
- A responsive grid of player cards.

You can filter the cards by:

- **All Players**
- **Nicknames** (only players who have a nickname)
- **Position Forward**
- **Position Midfielder**
- **Position Defender**
- **Position Goalkeeper**

## Tech Stack

- **HTML** – structure and content for the team stats, filter, and cards.
- **CSS** – layout, colors, and responsive card grid.
- **JavaScript** – data model for the team, filtering logic, DOM updates.

## Features

- Displays team info for:
  - Team: **Argentina**
  - Sport: **Football**
  - Year: **1986**
  - Head coach: **Carlos Bilardo**
- Renders each player as a card with:
  - Name (with “(Captain)” prefix when applicable)
  - Position
  - Shirt number
  - Nickname or `N/A` if none
- Dropdown filter that:
  - Shows only players with a nickname.
  - Shows only players of a selected position.
  - Resets to all players.

## How to Run the Project

1. **Clone the repository:**

   ```bash
   git clone https://github.com/SharpSanders/football-cards.git
   cd football-cards
Open the app:

Option A: Double-click index.html to open it in your browser.

Option B (recommended while developing): Use the Live Server extension in VS Code to serve index.html.

You should see the Team stats heading and a grid of player cards.

How to Use
Review the team stats at the top of the page.

Use the “Filter Teammates” dropdown:

Select All Players to see everyone.

Select Nicknames to show only players with a defined nickname.

Select one of the position options to filter by role (forward, midfielder, defender, goalkeeper).

The cards update instantly based on your selection.

How It Works (JavaScript Overview)
All of the logic lives in script.js:

A myFavoriteFootballTeam object stores:

Team, sport, year, and whether they’re World Cup winners.

Head coach data (name and matches).

A players array with each player’s name, position, number, isCaptain, and nickname.

Object.freeze(myFavoriteFootballTeam):

Prevents the root team object from being modified, treating it like read-only data.

Destructuring:

js
Copy code
const { sport, team, year, players } = myFavoriteFootballTeam;
const { coachName } = myFavoriteFootballTeam.headCoach;
This pulls out the keys you need for easier use.

The UI text (team name, sport, year, coach) is set by updating the corresponding DOM elements’ textContent.

setPlayerCards(arr = players):

Takes an array of players (default is all players).

Uses .map() and template literals to create HTML for each player card.

Uses a ternary operator to prepend “(Captain)” for captains.

Displays N/A when nickname is null.

Dropdown change handler:

js
Copy code
playersDropdownList.addEventListener("change", (e) => {
  playerCards.innerHTML = "";

  switch (e.target.value) {
    case "nickname":
      setPlayerCards(players.filter(player => player.nickname !== null));
      break;
    case "forward":
      setPlayerCards(players.filter(player => player.position === "forward"));
      break;
    // ...other cases...
    default:
      setPlayerCards();
  }
});
This uses .filter() to generate subsets of the players array based on the selected value.

Project Structure
text
Copy code
football-cards/
├── index.html   # Markup for team stats, filter dropdown, and player cards container
├── styles.css   # Styling for background, typography, layout, and card design
└── script.js    # Team data object, destructuring, filter logic, and DOM rendering
What I Practiced
Modeling data with nested objects and arrays.

Using Object.freeze to treat data as immutable.

Destructuring objects to simplify variable access.

Using array methods (map, filter) to generate and filter UI.

Working with DOM APIs (getElementById, innerHTML, event listeners).

Basic responsive layout with flexbox and media queries.

Future Improvements
Add more teams and let the user switch between them.

Add search by player name or number.

Add sorting options (e.g. by position, number, or name).

Highlight the captain card more visually.

Add animations or transitions when the card set changes.

Author
Created by Trevyn Sanders.