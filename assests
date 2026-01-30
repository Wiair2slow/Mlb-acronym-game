// script.js

const acronymData = [
  {
    acronym: "NYY",
    answer: "New York Yankees",
    type: "team",
    playerImage: "assets/players/generic-batter-1.png"
  },
  {
    acronym: "LAD",
    answer: "Los Angeles Dodgers",
    type: "team",
    playerImage: "assets/players/generic-batter-2.png"
  },
  {
    acronym: "ATL",
    answer: "Atlanta Braves",
    type: "team",
    playerImage: "assets/players/generic-batter-3.png"
  },
  {
    acronym: "BAL",
    answer: "Baltimore Orioles",
    type: "team",
    playerImage: "assets/players/generic-batter-4.png"
  },
  {
    acronym: "OPS",
    answer: "On-base Plus Slugging",
    type: "stat",
    playerImage: "assets/players/generic-batter-5.png"
  },
  {
    acronym: "ERA",
    answer: "Earned Run Average",
    type: "stat",
    playerImage: "assets/players/generic-batter-6.png"
  },
  {
    acronym: "WAR",
    answer: "Wins Above Replacement",
    type: "stat",
    playerImage: "assets/players/generic-batter-7.png"
  }
];

let currentItem = null;

const acronymTextEl = document.getElementById("acronym-text");
const acronymTypeEl = document.getElementById("acronym-type");
const playerImageEl = document.getElementById("player-image");
const guessFormEl = document.getElementById("guess-form");
const guessInputEl = document.getElementById("guess-input");
const feedbackEl = document.getElementById("feedback");
const nextButtonEl = document.getElementById("next-button");

function pickRandomItem() {
  const index = Math.floor(Math.random() * acronymData.length);
  return acronymData[index];
}

function renderItem(item) {
  currentItem = item;

  acronymTextEl.textContent = item.acronym;
  acronymTypeEl.textContent = item.type === "team" ? "Team" : "Stat";

  playerImageEl.src = item.playerImage;
  playerImageEl.onerror = () => {
    // Fallback if image missing
    playerImageEl.style.display = "none";
  };

  feedbackEl.textContent = "";
  feedbackEl.className = "";
  guessInputEl.value = "";
  guessInputEl.disabled = false;
  nextButtonEl.classList.add("hidden");
}

function normalize(str) {
  return str.trim().toLowerCase().replace(/\s+/g, " ");
}

guessFormEl.addEventListener("submit", (e) => {
  e.preventDefault();
  if (!currentItem) return;

  const userGuess = normalize(guessInputEl.value);
  const correctAnswer = normalize(currentItem.answer);

  if (!userGuess) return;

  if (userGuess === correctAnswer) {
    feedbackEl.textContent = "Correct! 🎯";
    feedbackEl.className = "correct";
  } else {
    feedbackEl.textContent = `Not quite. Correct answer: ${currentItem.answer}`;
    feedbackEl.className = "incorrect";
  }

  guessInputEl.disabled = true;
  nextButtonEl.classList.remove("hidden");
});

nextButtonEl.addEventListener("click", () => {
  renderItem(pickRandomItem());
  guessInputEl.focus();
});

// Initial load
window.addEventListener("DOMContentLoaded", () => {
  renderItem(pickRandomItem());
  guessInputEl.focus();
});
