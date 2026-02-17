<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Traveller in Ancient Palestine</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f0e8;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
    header {
      background: #5b4636;
      color: #fff;
      padding: 10px 20px;
    }
    header h1 {
      margin: 0;
      font-size: 1.4rem;
    }
    main {
      flex: 1;
      padding: 20px;
      max-width: 900px;
      margin: 0 auto;
    }
    #story {
      background: #fff;
      border-radius: 8px;
      padding: 15px 20px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      min-height: 140px;
      margin-bottom: 15px;
      line-height: 1.5;
    }
    #choices {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 15px;
    }
    .choice-btn {
      flex: 1 1 45%;
      padding: 10px;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      background: #e0d2b8;
      transition: background 0.2s, transform 0.1s;
      text-align: left;
    }
    .choice-btn:hover {
      background: #d1c09f;
      transform: translateY(-1px);
    }
    .choice-btn:active {
      transform: translateY(0);
    }
    #stats {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      font-size: 0.9rem;
      margin-bottom: 10px;
    }
    #stats span {
      background: #fff;
      padding: 6px 10px;
      border-radius: 6px;
      box-shadow: 0 1px 3px rgba(0,0,0,0.08);
    }
    #feedback {
      min-height: 24px;
      font-size: 0.95rem;
      margin-bottom: 10px;
    }
    #feedback.correct {
      color: #1b7a32;
    }
    #feedback.wrong {
      color: #b02020;
    }
    #help {
      font-size: 0.85rem;
      color: #444;
      margin-top: 5px;
    }
    #resetBtn {
      margin-top: 10px;
      padding: 8px 14px;
      border-radius: 6px;
      border: none;
      background: #5b4636;
      color: #fff;
      cursor: pointer;
    }
    #resetBtn:hover {
      background: #463326;
    }
    @media (max-width: 600px) {
      .choice-btn {
        flex: 1 1 100%;
      }
    }
  </style>
</head>
<body>
<header>
  <h1>Traveller in Ancient Palestine</h1>
</header>
<main>
  <div id="stats">
    <span>Moves: <strong id="moves">0</strong></span>
    <span>Correct answers: <strong id="correct">0</strong></span>
    <span>Difficulty: <strong id="difficultyLabel">1 (Easy)</strong></span>
    <span>Chapter: <strong id="chapterLabel">1</strong></span>
  </div>

  <div id="story"></div>
  <div id="choices"></div>
  <div id="feedback"></div>
  <div id="help"></div>
  <button id="resetBtn">Restart Journey</button>
</main>

<script>
  // Game state
  let moves = 0;
  let correctAnswers = 0;
  let difficulty = 1; // 1 = easy, 2 = medium, 3 = hard
  let chapterIndex = 0;

  const chapters = [
    {
      id: 1,
      title: "Arriving in a Small Village",
      text: `You are a young traveller walking through the dusty roads of ancient Palestine.
The sun is low, and you arrive at a small village of stone and mud-brick houses.
You see families gathered on flat rooftops, sharing a simple meal of bread, olives, and fruit.
Nearby, a group of people are praying together and speaking quietly about someone called Jesus.`,
      question: "Who is most likely gathered in the house, praying and talking about Jesus?",
      optionsEasy: [
        { text: "A group of early Christians meeting in a home", correct: true },
        { text: "Roman soldiers collecting taxes", correct: false }
      ],
      optionsMedium: [
        { text: "Early Christians praying and breaking bread", correct: true },
        { text: "Travelling merchants selling cloth", correct: false },
        { text: "Actors preparing a play", correct: false }
      ],
      optionsHard: [
        { text: "An early Christian community devoted to the Apostles’ teaching", correct: true },
        { text: "A Roman tax office counting coins", correct: false },
        { text: "A group of fishermen mending nets", correct: false },
        { text: "A group of builders planning a new road", correct: false }
      ],
      helpEasy: "Think about who would be praying and talking about Jesus in a home.",
      helpMedium: "Early Christians often met in homes to pray and break bread together.",
      helpHard: "Acts 2:42–47 describes Christians gathering for teaching, prayer, and breaking of bread.",
      onCorrect: "You are invited inside. The people welcome you warmly and offer you bread.",
      onWrong: "You hesitate, unsure who they are. You watch from a distance, still curious."
    },
    {
      id: 2,
      title: "Life in the Household",
      text: `Inside the house, you see an extended family: grandparents, parents, children, and cousins.
The father talks about paying Roman taxes, while the mother prepares food over a small fire.
Children help fetch water from a nearby well. On a shelf, you notice a scroll of the Torah.
The family explains that they are Jewish followers of Jesus.`,
      question: "Which description best matches everyday family life in Jesus’ time?",
      optionsEasy: [
        { text: "Large extended families living simply, with basic food and shared work", correct: true },
        { text: "Small families with many servants doing all the work", correct: false }
      ],
      optionsMedium: [
        { text: "Extended families, simple homes, and work like farming and fishing", correct: true },
        { text: "Families living in huge palaces with many luxuries", correct: false },
        { text: "Families moving every day with no regular home", correct: false }
      ],
      optionsHard: [
        { text: "Extended Jewish families in small stone or mud-brick houses, living from farming, fishing, and trade", correct: true },
        { text: "Mostly single people living alone in tall apartment buildings", correct: false },
        { text: "Families who never paid taxes or dealt with the Romans", correct: false },
        { text: "Families who ate meat at every meal and rarely worked", correct: false }
      ],
      helpEasy: "Think about simple homes, shared work, and basic food.",
      helpMedium: "Most people were not rich; life centred on work and family.",
      helpHard: "Remember: small houses, flat roofs, simple food, and Roman taxes.",
      onCorrect: "You help the family draw water and share their evening meal.",
      onWrong: "You imagine a different kind of life, but the family gently explains how simple their days really are."
    },
    {
      id: 3,
      title: "The Community Shares",
      text: `Later that evening, more believers arrive.
They place coins, bread, and jars of oil on a low table so that anyone in need can take what they require.
One man explains that they try to be “of one heart and soul,” sharing possessions so no one is left hungry.
You notice that some of them have suffered because of their faith, yet they are joyful.`,
      question: "What key characteristic of the early Christian community are you seeing?",
      optionsEasy: [
        { text: "They share what they have so that everyone is cared for.", correct: true },
        { text: "They keep everything secret and never help anyone.", correct: false }
      ],
      optionsMedium: [
        { text: "Radical generosity and sharing of possessions", correct: true },
        { text: "Competition to see who is richest", correct: false },
        { text: "Ignoring the poor and sick", correct: false }
      ],
      optionsHard: [
        { text: "Living in unity and sharing possessions so that no one is in need", correct: true },
        { text: "Saving everything only for their closest friends", correct: false },
        { text: "Hiding their faith and never helping others", correct: false },
        { text: "Only caring about learning new trades", correct: false }
      ],
      helpEasy: "Think about how they treat people who are in need.",
      helpMedium: "Acts 4:32–35 describes believers sharing everything in common.",
      helpHard: "Unity, generosity, and care for the poor are signs of a Spirit-filled community.",
      onCorrect: "They smile and tell you that this is how they follow Jesus’ teaching.",
      onWrong: "You are unsure at first, but their kindness slowly shows you what matters to them."
    },
    {
      id: 4,
      title: "Prayer, Worship, and Mission",
      text: `The next morning, the community gathers again.
They listen to the Apostles’ teaching, pray, and break bread in memory of Jesus.
Some members prepare to travel to nearby towns, even though they may face persecution.
They say the Holy Spirit gives them courage to share the good news.`,
      question: "How do these practices show the identity of the early Church?",
      optionsEasy: [
        { text: "They are a Spirit-filled community that prays, worships, and shares Jesus’ message.", correct: true },
        { text: "They are only a social club that meets for fun.", correct: false }
      ],
      optionsMedium: [
        { text: "They show the Church as a Spirit-filled community on mission", correct: true },
        { text: "They show that the Church only cares about rules", correct: false },
        { text: "They show that the Church avoids talking about Jesus", correct: false }
      ],
      optionsHard: [
        { text: "Their prayer, breaking of bread, unity, and mission reveal a Spirit-filled Church", correct: true },
        { text: "Their main goal is to escape all responsibility", correct: false },
        { text: "They only want to impress the Romans", correct: false },
        { text: "They are trying to become rich and powerful", correct: false }
      ],
      helpEasy: "Think about prayer, worship, and courage to share the message of Jesus.",
      helpMedium: "The Holy Spirit strengthens them to live and share their faith.",
      helpHard: "Connect their life to how parishes today pray, serve, and spread the Gospel.",
      onCorrect: "You realise their way of life is a model for Christian communities today.",
      onWrong: "You still have questions, but you sense there is something powerful about their faith."
    }
  ];

  function getOptionsForDifficulty(chapter) {
    if (difficulty === 1) return chapter.optionsEasy;
    if (difficulty === 2) return chapter.optionsMedium;
    return chapter.optionsHard;
  }

  function getHelpForDifficulty(chapter) {
    if (difficulty === 1) return chapter.helpEasy;
    if (difficulty === 2) return chapter.helpMedium;
    return chapter.helpHard;
  }

  function updateStats() {
    document.getElementById("moves").textContent = moves;
    document.getElementById("correct").textContent = correctAnswers;
    let label = "1 (Easy)";
    if (difficulty === 2) label = "2 (Medium)";
    if (difficulty === 3) label = "3 (Hard)";
    document.getElementById("difficultyLabel").textContent = label;
    document.getElementById("chapterLabel").textContent = chapters[chapterIndex].id;
  }

  function adjustDifficulty() {
    // Simple adaptive logic:
    // If player is doing very well, increase difficulty; if struggling, lower it (but not below 1).
    const accuracy = correctAnswers / Math.max(moves, 1);
    if (accuracy > 0.75 && moves >= 4 && difficulty < 3) {
      difficulty++;
    } else if (accuracy < 0.4 && moves >= 4 && difficulty > 1) {
      difficulty--;
    }
  }

  function showChapter() {
    const chapter = chapters[chapterIndex];
    const storyDiv = document.getElementById("story");
    const choicesDiv = document.getElementById("choices");
    const feedbackDiv = document.getElementById("feedback");
    const helpDiv = document.getElementById("help");

    storyDiv.textContent = chapter.text + "\n\n" + chapter.question;
    choicesDiv.innerHTML = "";
    feedbackDiv.textContent = "";
    feedbackDiv.className = "";
    helpDiv.textContent = "";

    const options = getOptionsForDifficulty(chapter);
    options.forEach((opt, index) => {
      const btn = document.createElement("button");
      btn.className = "choice-btn";
      btn.textContent = (index + 1) + ". " + opt.text;
      btn.addEventListener("click", () => handleChoice(opt, chapter));
      choicesDiv.appendChild(btn);
    });

    updateStats();
  }

  function handleChoice(option, chapter) {
    moves++;
    const feedbackDiv = document.getElementById("feedback");
    const helpDiv = document.getElementById("help");

    if (option.correct) {
      correctAnswers++;
      feedbackDiv.textContent = "Correct! " + chapter.onCorrect;
      feedbackDiv.className = "correct";
    } else {
      feedbackDiv.textContent = "Not quite. " + chapter.onWrong;
      feedbackDiv.className = "wrong";
      helpDiv.textContent = "Hint: " + getHelpForDifficulty(chapter);
    }

    adjustDifficulty();
    updateStats();

    // Move to next chapter after a short delay
    setTimeout(() => {
      chapterIndex++;
      if (chapterIndex >= chapters.length) {
        endGame();
      } else {
        showChapter();
      }
    }, 1600);
  }

  function endGame() {
    const storyDiv = document.getElementById("story");
    const choicesDiv = document.getElementById("choices");
    const feedbackDiv = document.getElementById("feedback");
    const helpDiv = document.getElementById("help");

    choicesDiv.innerHTML = "";
    helpDiv.textContent = "";

    let summary = `Your journey through ancient Palestine is complete.\n\n`;
    summary += `You made ${moves} moves and answered ${correctAnswers} questions correctly.\n`;

    if (correctAnswers === chapters.length) {
      summary += `You understood the early Christian community very well: their unity, generosity, prayer, and mission.`;
    } else if (correctAnswers >= chapters.length / 2) {
      summary += `You learned a lot about early Christians and everyday life in Jesus’ time.`;
    } else {
      summary += `You caught some ideas, but there is still more to explore about early Christians and their way of life.`;
    }

    storyDiv.textContent = summary;
    feedbackDiv.textContent = "You can restart the journey to try different choices or aim for a higher score.";
    feedbackDiv.className = "";
    updateStats();
  }

  function resetGame() {
    moves = 0;
    correctAnswers = 0;
    difficulty = 1;
    chapterIndex = 0;
    showChapter();
  }

  document.getElementById("resetBtn").addEventListener("click", resetGame);

  // Start game
  resetGame();
</script>
</body>
</html>
