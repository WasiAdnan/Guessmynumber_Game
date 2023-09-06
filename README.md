# Guessmynumber_Game
I created this game here the user has to enter number of his choice if the guessed number is correct he wins.if user enters wrong number then score is going to decrease by one(-1) .and this game even stores the highscore...

# HTML  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="mycss.css" />
  </head>
  <body>
    <header>
      <h1 class="guess1">Guess my number</h1>
      <p class="between">(Between 1 and 20)</p>
      <button class="btn">Again</button>
      <div class="nmbr">?</div>
    </header>
    <main>
      <section class="left">
        <input type="number" class="number" />
        <button class="check">Check!</button>
      </section>
      <section class="right">
        <p class="guess">start guessing...</p>

        <p class="Score">💯 score: <span class="sc">20</span></p>
        <p class="high-score">🥇 Highscore: <span class="Hs">0</span></p>
      </section>
    </main>

    <script src="script.js"></script>
  </body>
</html>


# CSS   -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


@import url('https://fonts.googleapis.com/css?family=Press+Start+2P&display=swap');

* {
  margin: 0;
  padding: 0;
}
html {
  font-size: 4 rem;
  box-sizing: border-box;
}
@media screen and (max-width: 500px) {
  header {
    width: 100%;
  }
}
@media screen and (max-width: 500px) {
  main {
    width: 100%;
    color: blue;
  }
}
body {
  background-color: rgb(34, 34, 34);
  color: rgb(238, 238, 238);
  font-family: 'Press start 2p', 'sans-serif';
  display: flex;
  flex-direction: column;
}
header {
  height: 35vh;
  border-bottom: 7px solid #eee;
}
.guess1 {
  font-size: 3rem;
  position: relative;
  text-align: center;
  padding-top: 5%;
}
.between {
  /* position: relative;

  left: 82%;
  bottom: 30%;
  font-size: 0.9rem;*/
  border: none;
  font-family: inherit;
  position: absolute;
  padding: 0.8rem;
  top: 2rem;
  left: 70rem;
  /* cursor: pointer; */
}
.btn {
  /* font-family: 'Press statt 2p', 'sans-serif'; */
  /* position: relative;
  bottom: 50%; */
  border: none;
  font-family: inherit;
  position: absolute;
  padding: 0.8rem;
  top: 2rem;
  left: 2rem;
  cursor: pointer;
}
.nmbr {
  font-size: 3rem;
  display: inline-block;
  background-color: #eee;
  color: rgb(34, 34, 34);
  padding: 1.3rem;
  margin-left: 50vw;
  margin-top: 10vh;
}
main {
  display: flex;
  text-align: center;
  justify-content: space-around;
  /* font-size: 2rem; */
}
.left {
  display: flex;
  flex-direction: column;
  margin-top: 20vh;
}
.number {
  /* margin-top: 20vh; */

  margin-bottom: 9vh;
  padding: 3vh;
  padding-bottom: 3vh;
  text-size-adjust: 5rem;
  width: 20em;
  font-family: inherit;
}
.check {
  padding: 2vh;
  font-family: inherit;
  width: 100%;
  cursor: pointer;
  margin-left: 2vw;
}
.right {
  margin-top: 20vh;
}
.guess {
  margin-bottom: 15vh;
  font-size: 1.5rem;
}
.Score {
  margin-bottom: 5vh;
  font-size: 1rem;
}




#  JAVA-SCRIPT       --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


'use strict';
console.log(document.querySelector('.guess').textContent);

// console.log(
//   (document.querySelector('.guess').textContent = 'Correct Number!🎉🎊')
// );

// document.querySelector('.sc').textContent = 10;
// document.querySelector('.Hs').textContent = 15;
// document.querySelector('.nmbr').textContent = 13;

let secretNumber = Math.trunc(Math.random() * 20) + 1;

let score = 20;

let highScore = 0;

//   Refracted code   after function for  " .guess "  class  .....................................

const guess = function (message) {
  document.querySelector('.guess').textContent = message;
};

document.querySelector('.check').addEventListener('click', function () {
  let val = Number(document.querySelector('.number').value);
  if (!val) {
    // document.querySelector('.guess').textContent = '⛔ No Number';

    guess('⛔ No Number');
  }

  //    INVALID INPUT
  else if (val > 20) {
    //  BEFORE  FUNCTION  GUESS   ---------------------------------------------
    //   document.querySelector('.guess').textContent =
    //     'Selected invalid input please select between 1 and 20';
    // }

    //  AFTER FUNCTION .GUESS  ---------------------------------------------

    guess('Selected invalid input please select between 1 and 20');
  }

  //            REFRACTED     CODE   FOR         BELOW   ----------------------------------------------------------------
  else if (val !== secretNumber) {
    if (score > 1) {
      // document.querySelector('.guess').textContent =
      //   val > secretNumber ? '📈 Too High...' : '📉 Too low...';

      guess(val > secretNumber ? '📈 Too High...' : '📉 Too low...');

      score--;
      document.querySelector('.sc').textContent = score;
    } else {
      // document.querySelector('.guess').textContent = '🤦‍♂️ You lost the game';

      guess('🤦‍♂️ You lost the game');
    }
  }

  //              NOT      REFRACTED      CODE       FOR        ABOVE

  //    WHEN VALUE IS TOO LOW
  // else if (val < secretNumber) {
  //   if (score > 1) {
  //   document.querySelector('.guess').textContent = '📉 Too low...';
  //   score--;
  //   document.querySelector('.sc').textContent = score;
  // } else {
  //   document.querySelector('.guess').textContent = '🤦‍♂️ You lost the game';
  //   }
  // }

  // //    WHEN VALUE IS TOO HIGH
  // else if (val > secretNumber) {
  //   if (score > 1) {
  //     document.querySelector('.guess').textContent = '📈 Too High...';
  //     score--;
  //     document.querySelector('.sc').textContent = score;
  //   } else {
  //     document.querySelector('.guess').textContent = '🤦‍♂️ You lost the game';
  //   }
  // }
  else if (val === secretNumber) {
    // document.querySelector('.guess').textContent = 'You won 🎊🎊🎉🎉';

    guess('You won 🎊🎊🎉🎉');

    document.querySelector('.nmbr').textContent = secretNumber;

    document.querySelector('body').style.backgroundColor = 'rgb(80,168,50';
    document.querySelector('.nmbr').style.fontSize = '6rem';

    if (score > highScore) {
      highScore = score;
      document.querySelector('.Hs').textContent = highScore;
    }
  }
});

document.querySelector('.btn').addEventListener('click', function () {
  secretNumber = Math.trunc(Math.random() * 20) + 1;
  score = 20;

  // document.querySelector('.guess').textContent = 'start guessing...';

  guess('start guessing...');

  document.querySelector('.sc').textContent = score;
  secretNumber = Math.trunc(Math.random() * 20) + 1;
  document.querySelector('.number').value = ' ';
  document.querySelector('.nmbr').textContent = '?';
  document.querySelector('.nmbr').style.fontSize = '3rem';
  document.querySelector('body').style.backgroundColor = 'rgb(34,34,34)';
});
