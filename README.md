<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>5 Question Quiz</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background: #f9f9f9; }
    h1 { color: #333; }
    .question { margin-bottom: 20px; padding: 10px; background: #fff; border-radius: 10px; box-shadow: 0 0 5px rgba(0,0,0,0.1); }
    .options { margin-left: 20px; }
    .scorecard { margin-top: 30px; background: #e6ffe6; padding: 15px; border-radius: 10px; }
    button { padding: 10px 20px; margin-top: 20px; font-size: 16px; background-color: #28a745; color: white; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background-color: #218838; }
  </style>
</head>
<body>

  <h1>5 Question Quiz</h1>

  <form id="quizForm">
    <div class="question">
      <p>1. Question 1</p>
      <div class="options">
        <label><input type="radio" name="q1" value="A"> A.</label><br>
        <label><input type="radio" name="q1" value="B"> B.</label><br>
        <label><input type="radio" name="q1" value="C"> C.</label><br>
        <label><input type="radio" name="q1" value="D"> D.</label>
      </div>
    </div>

    <div class="question">
      <p>2. Question 2</p>
      <div class="options">
        <label><input type="radio" name="q2" value="A"> A.</label><br>
        <label><input type="radio" name="q2" value="B"> B.</label><br>
        <label><input type="radio" name="q2" value="C"> C.</label><br>
        <label><input type="radio" name="q2" value="D"> D.</label>
      </div>
    </div>

    <div class="question">
      <p>3. Question 3</p>
      <div class="options">
        <label><input type="radio" name="q3" value="A"> A.</label><br>
        <label><input type="radio" name="q3" value="B"> B.</label><br>
        <label><input type="radio" name="q3" value="C"> C.</label><br>
        <label><input type="radio" name="q3" value="D"> D.</label>
      </div>
    </div>

    <div class="question">
      <p>4. Question 4</p>
      <div class="options">
        <label><input type="radio" name="q4" value="A"> A.</label><br>
        <label><input type="radio" name="q4" value="B"> B.</label><br>
        <label><input type="radio" name="q4" value="C"> C.</label><br>
        <label><input type="radio" name="q4" value="D"> D.</label>
      </div>
    </div>

    <div class="question">
      <p>5. Question 5</p>
      <div class="options">
        <label><input type="radio" name="q5" value="A"> A.</label><br>
        <label><input type="radio" name="q5" value="B"> B.</label><br>
        <label><input type="radio" name="q5" value="C"> C.</label><br>
        <label><input type="radio" name="q5" value="D"> D.</label>
      </div>
    </div>

    <button type="button" onclick="submitQuiz()">Submit</button>
  </form>

  <div class="scorecard" id="scorecard" style="display:none;"></div>

  <script>
    const answerKey = { q1: 'B', q2: 'A', q3: 'C', q4: 'D', q5: 'A' };
    const marks = { correct: 8, incorrect: -11, skip: -3 };

    function submitQuiz() {
      let form = document.forms['quizForm'];
      let score = 0;
      let correct = [], incorrect = [], skip = [];

      for (let i = 1; i <= 5; i++) {
        let qName = "q" + i;
        let selected = form[qName].value;
        if (!selected) {
          score += marks.skip;
          skip.push(i);
        } else if (selected === answerKey[qName]) {
          score += marks.correct;
          correct.push(i);
        } else {
          score += marks.incorrect;
          incorrect.push(i);
        }
      }

      // Display results
      let resultDiv = document.getElementById("scorecard");
      resultDiv.style.display = "block";
      resultDiv.innerHTML = `
        <h2>Scorecard</h2>
        <p><strong>Total Score:</strong> ${score}</p>
        <p><strong>Correct:</strong> ${correct.length} (Questions: ${correct.join(', ') || 'None'})</p>
        <p><strong>Incorrect:</strong> ${incorrect.length} (Questions: ${incorrect.join(', ') || 'None'})</p>
        <p><strong>Skipped:</strong> ${skip.length} (Questions: ${skip.join(', ') || 'None'})</p>
      `;
    }
  </script>

</body>
</html>
