# negative9ball.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Choose Your Fate: Caribbean 1600s</title>
  <style>
    body {
      font-family: Georgia, serif;
      background: #f5efe0;
      color: #2b2b2b;
      padding: 20px;
      max-width: 700px;
      margin: auto;
      line-height: 1.6;
    }
    h1, h2 {
      text-align: center;
      color: #004085;
    }
    h1 {
      margin-bottom: 30px;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
    }
    #game {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      margin: 20px 0;
    }
    #game p {
      font-size: 18px;
      margin-bottom: 20px;
      text-align: justify;
    }
    .choice {
      display: block;
      width: 100%;
      margin: 10px 0;
      padding: 15px;
      background: #cce5ff;
      border: 2px solid #004085;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      font-family: Georgia, serif;
      transition: all 0.3s ease;
    }
    .choice:hover {
      background: #99ccff;
      transform: translateY(-2px);
      box-shadow: 0 4px 8px rgba(0,64,133,0.3);
    }
    .choice:active {
      transform: translateY(0);
    }
    @media (max-width: 600px) {
      body {
        padding: 10px;
      }
      h1 {
        font-size: 24px;
      }
      #game p {
        font-size: 16px;
      }
      .choice {
        padding: 12px;
        font-size: 15px;
      }
    }
  </style>
</head>
<body>

  <h1>🌴 Choose Your Fate: Caribbean 1600s 🌴</h1>
  <div id="game"></div>

  <script>
    // --- Story Data ---
    const story = {
      start: {
        text: "It is the 1600s in the Caribbean. Life here is dangerous, unfair, and full of choices. Will you survive? Choose your character:",
        choices: [
          { text: "Enslaved African", next: "enslaved1" },
          { text: "Indentured Servant", next: "servant1" }
        ]
      },

      // --- Enslaved African Path ---
      enslaved1: {
        text: "You are forced to cut cane in the hot sun. At night, you hear whispers of escape. Do you:",
        choices: [
          { text: "Attempt Escape", next: "enslaved_escape" },
          { text: "Endure and Wait", next: "enslaved_wait" }
        ]
      },
      enslaved_escape: {
        text: "You flee into the jungle. A maroon community offers to take you in. Do you:",
        choices: [
          { text: "Join the Maroons", next: "enslaved_maroons" },
          { text: "Try to Survive Alone", next: "enslaved_alone" }
        ]
      },
      enslaved_wait: {
        text: "Years pass. A rebellion begins among the enslaved. Do you:",
        choices: [
          { text: "Join the Revolt", next: "enslaved_revolt" },
          { text: "Stay Loyal to Survive", next: "enslaved_loyal" }
        ]
      },
      enslaved_maroons: {
        text: "You raid plantations with allies. Colonial troops close in. You fight bravely, but survival is uncertain. ✊ END",
        choices: []
      },
      enslaved_alone: {
        text: "Alone, disease and hunger weaken you. Without allies, your freedom is short-lived. 🥀 END",
        choices: []
      },
      enslaved_revolt: {
        text: "You fight in the rebellion. You are captured and executed, but your courage inspires others. 🔥 END",
        choices: []
      },
      enslaved_loyal: {
        text: "You survive, but remain enslaved until death. The system crushed your fate. ⛓️ END",
        choices: []
      },

      // --- Indentured Servant Path ---
      servant1: {
        text: "Your master is cruel and your contract long. Do you:",
        choices: [
          { text: "Run Away to Pirate Port", next: "servant_pirate" },
          { text: "Endure and Finish Contract", next: "servant_contract" }
        ]
      },
      servant_pirate: {
        text: "You reach a pirate haven. A captain offers you a spot on his crew. Do you:",
        choices: [
          { text: "Join the Pirate Crew", next: "servant_pirate_crew" },
          { text: "Stay in the Port", next: "servant_port" }
        ]
      },
      servant_contract: {
        text: "After years, your contract nears its end, but your master refuses to free you. Do you:",
        choices: [
          { text: "Fight in Court", next: "servant_court" },
          { text: "Accept Continued Service", next: "servant_service" }
        ]
      },
      servant_pirate_crew: {
        text: "You raid ships and strike gold! But the navy hunts you down. You are captured and hanged. ☠️ END",
        choices: []
      },
      servant_port: {
        text: "You find work on the docks, but disease spreads quickly. You die in poverty. ⚓ END",
        choices: []
      },
      servant_court: {
        text: "You fight for your rights, but the court sides with your master. Justice is denied. ⚖️ END",
        choices: []
      },
      servant_service: {
        text: "You serve quietly until old. Freed at last, but with nothing to live on. 🕊️ END",
        choices: []
      }
    };

    // --- Game Engine ---
    const gameDiv = document.getElementById("game");

    function showNode(nodeKey) {
      const node = story[nodeKey];
      gameDiv.innerHTML = `<p>${node.text}</p>`;
      
      node.choices.forEach(choice => {
        const button = document.createElement("button");
        button.className = "choice";
        button.textContent = choice.text;
        button.onclick = () => showNode(choice.next);
        gameDiv.appendChild(button);
      });
    }

    // Start Game
    showNode("start");
  </script>
</body>
</html>
