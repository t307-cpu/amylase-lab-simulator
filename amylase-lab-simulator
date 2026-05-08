<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Amylase Activity Lab Simulator</title>
<style>
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f0f4f8; margin: 0; padding: 20px; color: #333; }
.container { max-width: 950px; margin: 0 auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
h1 { text-align: center; color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 10px; }
h2 { color: #34495e; border-left: 5px solid #3498db; padding-left: 10px;}

.panel { display: none; padding: 20px; border: 1px solid #ddd; border-radius: 8px; margin-top: 20px; background-color: #fafafa; }
.active-panel { display: block; }

.student-form { display: flex; flex-direction: column; gap: 15px; max-width: 400px; margin: 0 auto; }
.student-form input { padding: 10px; font-size: 1.1em; border: 2px solid #bdc3c7; border-radius: 5px; }

.setup-description { background-color: #e3f2fd; padding: 15px; border-radius: 5px; margin-bottom: 20px; border-left: 5px solid #2196f3; font-size: 1.1em;}
.setup-grid { display: flex; justify-content: space-around; gap: 15px; margin: 20px 0; flex-wrap: wrap;}
.tube-station { text-align: center; border: 1px solid #ddd; border-radius: 8px; background: white; padding: 15px; width: calc(25% - 20px); min-width: 180px; box-sizing: border-box;}
.tube { width: 60px; height: 120px; border: 3px solid #7f8c8d; border-top: none; border-radius: 0 0 30px 30px; position: relative; background: #eef; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 14px; margin: 0 auto 15px auto;}
.ingredient-list { text-align: left; background: #fefefe; padding: 10px; border-radius: 4px; border: 1px solid #eee; margin-top: 10px;}
.ingredient-list strong {display: block; margin-bottom: 5px; color: #7f8c8d;}
.ingredient-item { margin-bottom: 8px; display: flex; align-items: center; }
.ingredient-item input { margin-right: 8px; cursor: pointer; scale: 1.2;}
.ingredient-item label { cursor: pointer; font-size: 0.9em;}
.setup-controls { text-align: center; margin-top: 30px; padding-top: 20px; border-top: 2px solid #ddd;}
#green-light { display: none; color: #27ae60; font-weight: bold; font-size: 1.3em; margin-top: 15px; padding: 10px; background-color: #e8f5e9; border-radius: 5px;}

.volume-list { background: #fff; padding: 10px; border-radius: 5px; text-align: left; font-size: 0.9em; box-shadow: inset 0 1px 3px rgba(0,0,0,0.1); border: 1px solid #ecf0f1; margin-top: 10px;}
.volume-list li { margin-bottom: 5px; color: #2c3e50; }

.quiz-container { background: #fff3cd; border: 1px solid #ffeeba; padding: 20px; border-radius: 8px; margin-top: 20px; color: #856404; }
.quiz-container h3 { margin-top: 0; color: #856404;}
.quiz-option { margin-bottom: 10px; display: flex; align-items: flex-start; }
.quiz-option input { margin-top: 4px; margin-right: 10px; cursor: pointer;}
.quiz-option label { cursor: pointer; font-weight: 500;}
.quiz-feedback { margin-top: 15px; font-weight: bold; font-size: 1.1em; display: none; }

.instructions { background: #e8f4f8; border-left: 5px solid #17a2b8; padding: 15px; margin-bottom: 20px; font-weight: bold; font-size: 1.1em; color: #0c5460; line-height: 1.4; transition: 0.3s;}
.highlight-instruction { background: #fff3cd; border-color: #ffc107; color: #856404; }
.controls { display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 20px; align-items: center; justify-content: center;}
button { padding: 10px 15px; border: none; border-radius: 5px; background-color: #3498db; color: white; font-weight: bold; cursor: pointer; transition: 0.3s; font-size: 0.95em;}
button:hover { background-color: #2980b9; }
button:disabled { background-color: #b0bec5; cursor: not-allowed; }
#btn-part4 { display: none; background-color: #27ae60; font-size: 1.1em; padding: 12px 20px;}
#btn-part4:hover { background-color: #2ecc71; }

.timer {
  font-size: 1.8em;
  font-family: monospace;
  background: #2c3e50;
  color: white;
  padding: 15px 28px;
  border-radius: 8px;
  text-align: center;
  min-width: 220px;
  width: fit-content;
  max-width: 100%;
  margin: 0 auto 20px auto;
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);
  white-space: nowrap;
  box-sizing: border-box;
}

.lab-bench { background: #fff; border: 2px solid #bdc3c7; border-radius: 10px; padding: 20px; margin-bottom: 20px; display: flex; flex-direction: column; gap: 20px; }
.shelf { display: flex; justify-content: space-around; background: #ecf0f1; padding: 15px; border-radius: 8px; flex-wrap: wrap; gap: 10px; border-bottom: 4px solid #95a5a6;}
.workspace { display: flex; justify-content: space-around; align-items: flex-end; padding-top: 10px; flex-wrap: wrap; gap: 15px;}

.draggable-item {
  padding: 10px 15px;
  background: white;
  border: 2px solid #7f8c8d;
  border-radius: 8px;
  cursor: grab;
  font-weight: bold;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  user-select: none;
  -webkit-user-select: none;
  -webkit-touch-callout: none;
  touch-action: none;
  transition: transform 0.2s, box-shadow 0.2s;
}
.draggable-item:active { cursor: grabbing; transform: scale(0.95); }
.draggable-item[draggable="false"] { opacity: 0.5; cursor: not-allowed; border-color: #bdc3c7; touch-action: auto; }
.target-glow { box-shadow: 0 0 12px 4px #f1c40f !important; border-color: #f39c12 !important; }
.item-glow { box-shadow: 0 0 12px 4px #3498db !important; border-color: #2980b9 !important; }

.main-tube-area { display: flex; flex-direction: column; align-items: center; border: 3px dashed transparent; padding: 10px; border-radius: 10px; transition: 0.3s;}

.main-tube {
  width: 110px;
  height: 160px;
  border: 3px solid #34495e;
  border-top: none;
  border-radius: 0 0 55px 55px;
  background: white;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  padding: 10px 8px;
  font-weight: bold;
  color: #2c3e50;
  font-size: 0.95em;
  text-align: center;
  line-height: 1.3;
  transition: background 0.5s;
  box-sizing: border-box;
  word-break: break-word;
}

.spot-plate { display: grid; grid-template-columns: repeat(6, 1fr); gap: 15px; background: #ecf0f1; padding: 20px; border-radius: 10px; box-shadow: inset 0 2px 5px rgba(0,0,0,0.1); border: 3px dashed transparent; transition: 0.3s;}
.well-container { text-align: center; }
.well { width: 50px; height: 50px; background: white; border-radius: 50%; border: 3px solid #bdc3c7; margin: 0 auto 8px auto; transition: background-color 0.5s ease; box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);}
.well-container small { font-weight: bold; color: #7f8c8d;}

.colour-empty { background-color: white; }
.colour-iodine { background-color: #d4a373; border-color: #a67c52;}
.colour-starch { background-color: #1a1a2e; border-color: #0c0c1a;}
.colour-partial { background-color: #5d4037; border-color: #4e342e;}

.touch-ghost {
  position: fixed !important;
  pointer-events: none !important;
  opacity: 0.85;
  z-index: 9999;
  transform: scale(1.05);
  box-shadow: 0 6px 14px rgba(0,0,0,0.3) !important;
}

.certificate-container { border: 10px solid #34495e; padding: 40px; text-align: center; background: #fdfbf7; border-radius: 10px; margin-top: 20px;}
.cert-title { font-size: 2.5em; color: #2c3e50; font-family: 'Georgia', serif; border-bottom: 2px solid #bdc3c7; padding-bottom: 10px; margin-bottom: 20px; }
.cert-body { font-size: 1.2em; color: #34495e; line-height: 1.8; }
.cert-name { font-size: 1.8em; font-weight: bold; color: #2980b9; margin: 15px 0; border-bottom: 1px dashed #2980b9; display: inline-block; padding: 0 20px;}
.cert-seal { width: 100px; height: 100px; background: #f1c40f; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 30px auto 0 auto; color: white; font-weight: bold; font-size: 1.5em; border: 5px double #e67e22; box-shadow: 0 4px 6px rgba(0,0,0,0.2); transform: rotate(-5deg);}
</style>
</head>
<body>
<div class="container">
<h1>Investigation: Effect of pH on Amylase Activity</h1>

<!-- PHASE 0 -->
<div id="intro-panel" class="panel active-panel">
  <h2>Welcome to the Virtual Lab</h2>
  <div class="setup-description">
    Please enter your details below to begin the investigation. A certificate of completion will be generated once you finish all lab activities.
  </div>
  <div class="student-form">
    <input type="text" id="inp-name" placeholder="Full Name" required>
    <input type="text" id="inp-class" placeholder="Class (e.g., 1A)" required>
    <input type="text" id="inp-number" placeholder="Class No. (e.g., 14)" required>
    <button onclick="startLab()">Begin Laboratory Setup</button>
  </div>
</div>

<!-- PART 1 -->
<div id="setup-panel" class="panel">
  <h2>Part 1: Laboratory Setup Verification</h2>
  <div class="setup-description">
    <p><strong>Goal:</strong> To investigate the denaturation of salivary amylase in gastric conditions (pH 2) and evaluate the physiological necessity of pancreatic amylase secretion for the resumption of carbohydrate digestion in the duodenum.</p>
    <p><strong>Task:</strong> Set up the correct test conditions below. Tick the exact boxes needed for each tube. Do not add extra liquids that don't belong!</p>
  </div>
  <div class="setup-grid">
    <div class="tube-station">
      <h3>Test Tube 1</h3><div class="tube">pH 2</div>
      <div class="ingredient-list">
        <div class="ingredient-item"><input type="checkbox" id="t1-starch"><label for="t1-starch">Starch Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t1-amylase"><label for="t1-amylase">Amylase Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t1-ph2"><label for="t1-ph2">pH 2 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t1-ph7"><label for="t1-ph7">pH 7 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t1-ph9"><label for="t1-ph9">pH 9 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t1-water"><label for="t1-water">Distilled Water</label></div>
      </div>
    </div>
    <div class="tube-station">
      <h3>Test Tube 2</h3><div class="tube">pH 7</div>
      <div class="ingredient-list">
        <div class="ingredient-item"><input type="checkbox" id="t2-starch"><label for="t2-starch">Starch Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t2-amylase"><label for="t2-amylase">Amylase Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t2-ph2"><label for="t2-ph2">pH 2 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t2-ph7"><label for="t2-ph7">pH 7 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t2-ph9"><label for="t2-ph9">pH 9 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t2-water"><label for="t2-water">Distilled Water</label></div>
      </div>
    </div>
    <div class="tube-station">
      <h3>Test Tube 3</h3><div class="tube">pH 9</div>
      <div class="ingredient-list">
        <div class="ingredient-item"><input type="checkbox" id="t3-starch"><label for="t3-starch">Starch Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t3-amylase"><label for="t3-amylase">Amylase Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t3-ph2"><label for="t3-ph2">pH 2 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t3-ph7"><label for="t3-ph7">pH 7 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t3-ph9"><label for="t3-ph9">pH 9 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t3-water"><label for="t3-water">Distilled Water</label></div>
      </div>
    </div>
    <div class="tube-station">
      <h3>Control Tube</h3><div class="tube">C</div>
      <div class="ingredient-list">
        <div class="ingredient-item"><input type="checkbox" id="t4-starch"><label for="t4-starch">Starch Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t4-amylase"><label for="t4-amylase">Amylase Solution</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t4-ph2"><label for="t4-ph2">pH 2 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t4-ph7"><label for="t4-ph7">pH 7 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t4-ph9"><label for="t4-ph9">pH 9 Buffer</label></div>
        <div class="ingredient-item"><input type="checkbox" id="t4-water"><label for="t4-water">Distilled Water</label></div>
      </div>
    </div>
  </div>
  <div class="setup-controls">
    <button id="btn-verify" onclick="verifySetup()">Verify Experimental Setup</button>
    <div id="green-light">✅ ALL CORRECT! GREEN LIGHT GRANTED. Proceeding to Volumes Check...</div>
  </div>
</div>

<!-- PART 2 -->
<div id="review-panel" class="panel">
  <h2>Part 2: Reviewing Volumes & Variables</h2>
  <div class="setup-description">
    Now that you have chosen the correct ingredients, let's look at the specific amounts (volumes) being added to each tube to ensure a fair test.
  </div>
  <div class="setup-grid">
    <div class="tube-station">
      <h3>Test Tube 1</h3>
      <ul class="volume-list">
        <li>💧 Starch: 5 mL</li>
        <li>🧪 Amylase: 1 mL</li>
        <li>🔴 pH 2 Buffer: 4 mL</li>
        <li><strong>Total: 10 mL</strong></li>
      </ul>
    </div>
    <div class="tube-station">
      <h3>Test Tube 2</h3>
      <ul class="volume-list">
        <li>💧 Starch: 5 mL</li>
        <li>🧪 Amylase: 1 mL</li>
        <li>🟢 pH 7 Buffer: 4 mL</li>
        <li><strong>Total: 10 mL</strong></li>
      </ul>
    </div>
    <div class="tube-station">
      <h3>Test Tube 3</h3>
      <ul class="volume-list">
        <li>💧 Starch: 5 mL</li>
        <li>🧪 Amylase: 1 mL</li>
        <li>🔵 pH 9 Buffer: 4 mL</li>
        <li><strong>Total: 10 mL</strong></li>
      </ul>
    </div>
    <div class="tube-station">
      <h3>Control Tube</h3>
      <ul class="volume-list">
        <li>💧 Starch: 5 mL</li>
        <li>💧 Distilled Water: 5 mL</li>
        <li><strong>Total: 10 mL</strong></li>
      </ul>
    </div>
  </div>
  <div class="quiz-container">
    <h3>Knowledge Check</h3>
    <p>Look at the volumes listed above. In Tubes 1, 2, and 3, you are adding 4 mL of buffer. <strong>Why is 5 mL, instead of 4 mL, of distilled water added to the Control Tube?</strong></p>
    <div class="quiz-option"><input type="radio" id="q1-a" name="volume-quiz" value="wrong1"><label for="q1-a">To dilute the starch further so it breaks down naturally without any enzymes.</label></div>
    <div class="quiz-option"><input type="radio" id="q1-b" name="volume-quiz" value="correct"><label for="q1-b">To keep the total volume at 10 mL, ensuring the concentration of starch is equal across all set-ups.</label></div>
    <div class="quiz-option"><input type="radio" id="q1-c" name="volume-quiz" value="wrong2"><label for="q1-c">Because 5 mL is the standard safety requirement for neutralizing any accidental acids in the lab.</label></div>
    <div class="quiz-option"><input type="radio" id="q1-d" name="volume-quiz" value="wrong3"><label for="q1-d">Because distilled water evaporates quickly, so extra is needed to prevent the tube from drying out.</label></div>
    <div style="margin-top: 20px;"><button onclick="checkQuiz()">Submit Answer</button></div>
    <div id="quiz-feedback" class="quiz-feedback"></div>
  </div>
</div>

<!-- PART 3 -->
<div id="experiment-panel" class="panel">
  <h2>Part 3: Interactive Virtual Lab Bench</h2>
  <div id="instruction-box" class="instructions highlight-instruction">
    Step 1: Drag the Iodine bottle to the Spot Plate to fill the wells.
  </div>
  <div class="timer" id="timer-display">Wait: 0 min</div>
  <div class="lab-bench">
    <div class="shelf">
      <div class="draggable-item" id="item-iodine" draggable="true" ondragstart="drag(event)">🟤 Iodine Solution</div>
      <div class="draggable-item" id="item-ph2" draggable="true" ondragstart="drag(event)">🔴 pH 2 Buffer</div>
      <div class="draggable-item" id="item-ph7" draggable="true" ondragstart="drag(event)">🟢 pH 7 Buffer</div>
      <div class="draggable-item" id="item-ph9" draggable="true" ondragstart="drag(event)">🔵 pH 9 Buffer</div>
      <div class="draggable-item" id="item-control" draggable="true" ondragstart="drag(event)">⚪ Distilled Water</div>
      <div class="draggable-item" id="item-amylase" draggable="false" ondragstart="drag(event)">🧫 Amylase Solution</div>
      <div class="draggable-item" id="item-starch" draggable="false" ondragstart="drag(event)">🥔 Starch Solution</div>
      <div class="draggable-item" id="item-Reaction Mixture" draggable="false" ondragstart="drag(event)">🖊 Reaction Mixture</div>
    </div>
    <div class="workspace">
      <div class="spot-plate" id="spot-plate" ondrop="dropPlate(event)" ondragover="allowDrop(event)"></div>
      <div class="main-tube-area" id="tube-area" ondrop="dropTube(event)" ondragover="allowDrop(event)">
        <div class="main-tube" id="reaction-tube">🧪<br>Empty<br>Tube</div>
        <button id="btn-incubate" onclick="incubate()" disabled style="margin-top: 15px;">Incubate (Wait 5m)</button>
      </div>
    </div>
  </div>
  <div class="controls">
    <button id="btn-reset" onclick="resetBench()" style="background-color: #e74c3c; display: none;">Reset Bench for Next Tube</button>
    <button id="btn-part4" onclick="proceedToPart4()">Proceed to Part 4 ➔</button>
  </div>
</div>

<!-- PART 4 -->
<div id="conclusion-panel" class="panel">
  <h2>Part 4: Conclusion & Analysis</h2>
  <div class="setup-description">
    You have successfully completed all four test conditions. Based on your observations of the iodine colour changes, answer the following questions to complete the lab.
  </div>
  <div class="quiz-container">
    <h3>Question 1</h3>
    <p>Based on your spot plate results, which test tube demonstrated the highest amylase activity (broke down starch the fastest)?</p>
    <div class="quiz-option"><input type="radio" id="q4-1a" name="q1-final" value="wrong1"><label for="q4-1a">Test Tube 1 (pH 2 - Stomach conditions)</label></div>
    <div class="quiz-option"><input type="radio" id="q4-1b" name="q1-final" value="correct"><label for="q4-1b">Test Tube 2 (pH 7 - Mouth cavity conditions)</label></div>
    <div class="quiz-option"><input type="radio" id="q4-1c" name="q1-final" value="wrong2"><label for="q4-1c">Test Tube 3 (pH 9 - Small intestine conditions)</label></div>
    <div class="quiz-option"><input type="radio" id="q4-1d" name="q1-final" value="wrong3"><label for="q4-1d">Control Tube</label></div>
    <hr style="border: 0; border-top: 1px solid #ffeeba; margin: 20px 0;">
    <h3>Question 2</h3>
    <p>Salivary amylase begins carbohydrate digestion in the mouth. Based on what happened in Test Tube 1, what is the physiological reason that <strong>pancreatic amylase</strong> must be secreted into the duodenum (small intestine) to resume digestion?</p>
    <div class="quiz-option"><input type="radio" id="q4-2a" name="q2-final" value="wrong1"><label for="q4-2a">Because starch cannot be fully digested in a single step and requires two different types of enzymes working simultaneously.</label></div>
    <div class="quiz-option"><input type="radio" id="q4-2b" name="q2-final" value="correct"><label for="q4-2b">Because salivary amylase is denatured by the highly acidic environment of the stomach, requiring a fresh enzyme source once the food enters the neutralised small intestine.</label></div>
    <div class="quiz-option"><input type="radio" id="q4-2c" name="q2-final" value="wrong2"><label for="q4-2c">Because the small intestine can only absorb carbohydrates that have been digested specifically by pancreatic enzymes, not salivary ones.</label></div>
    <div class="quiz-option"><input type="radio" id="q4-2d" name="q2-final" value="wrong3"><label for="q4-2d">Because salivary amylase only works on cooked starch, while pancreatic amylase is needed to digest raw starch.</label></div>
    <div style="margin-top: 20px;"><button onclick="checkPart4Quiz()">Submit Final Answers</button></div>
    <div id="part4-feedback" class="quiz-feedback"></div>
  </div>
</div>

<!-- CERTIFICATE -->
<div id="certificate-panel" class="panel">
  <div class="certificate-container">
    <div class="cert-title">Certificate of Completion</div>
    <div class="cert-body">
      This certifies that
      <div class="cert-name" id="display-name">Student Name</div>
      <br>
      of Class <strong id="display-class"></strong> (No. <strong id="display-number"></strong>)
      <br><br>
      has successfully completed the Virtual Investigation on the<br>
      <strong>Effect of pH on Amylase Activity</strong>.
    </div>
    <div class="cert-seal">PASSED</div>
  </div>
</div>

</div>

<script>
let studentName = "";
let studentClass = "";
let studentNumber = "";

let timerMinutes = 0;
let selectedTube = "";
let wellsUsedCount = 0;
const maxWells = 6;
let completedTubes = new Set();
let labState = "ADD_IODINE";

// Helper: convert tube id (e.g. "ph7") to nicely formatted label (e.g. "pH 7")
function formatPHLabel(tubeId) {
  if (tubeId.startsWith("ph")) {
    return "pH " + tubeId.substring(2);
  }
  return tubeId;
}

function init() {
  const spotPlateDiv = document.getElementById('spot-plate');
  for (let i = 0; i < maxWells; i++) {
    spotPlateDiv.innerHTML += `
      <div class="well-container">
        <div class="well colour-empty" id="well-${i}"></div>
        <small>${i} min</small>
      </div>
    `;
  }
  attachTouchHandlers();
}

let touchDraggedId = null;
let touchGhost = null;
let touchOffsetX = 0;
let touchOffsetY = 0;

function attachTouchHandlers() {
  document.querySelectorAll('.draggable-item').forEach(el => {
    el.addEventListener('touchstart', handleTouchStart, { passive: false });
    el.addEventListener('touchmove', handleTouchMove, { passive: false });
    el.addEventListener('touchend', handleTouchEnd, { passive: false });
    el.addEventListener('touchcancel', handleTouchCancel, { passive: false });
  });
}

function handleTouchStart(e) {
  const el = e.currentTarget;
  if (el.getAttribute('draggable') === 'false') return;
  e.preventDefault();

  touchDraggedId = el.id;
  const touch = e.touches[0];
  const rect = el.getBoundingClientRect();
  touchOffsetX = touch.clientX - rect.left;
  touchOffsetY = touch.clientY - rect.top;

  touchGhost = el.cloneNode(true);
  touchGhost.classList.add('touch-ghost');
  touchGhost.style.left = (touch.clientX - touchOffsetX) + 'px';
  touchGhost.style.top = (touch.clientY - touchOffsetY) + 'px';
  touchGhost.style.width = rect.width + 'px';
  document.body.appendChild(touchGhost);
}

function handleTouchMove(e) {
  if (!touchGhost) return;
  e.preventDefault();
  const touch = e.touches[0];
  touchGhost.style.left = (touch.clientX - touchOffsetX) + 'px';
  touchGhost.style.top = (touch.clientY - touchOffsetY) + 'px';
}

function handleTouchEnd(e) {
  if (!touchGhost || !touchDraggedId) {
    cleanupTouch();
    return;
  }
  e.preventDefault();
  const touch = e.changedTouches[0];

  touchGhost.style.display = 'none';
  const dropEl = document.elementFromPoint(touch.clientX, touch.clientY);
  touchGhost.style.display = '';

  const draggedId = touchDraggedId;
  cleanupTouch();

  if (!dropEl) return;

  const fakeEvent = {
    preventDefault: () => {},
    dataTransfer: { getData: () => draggedId }
  };

  if (dropEl.closest('#spot-plate')) {
    dropPlate(fakeEvent);
  } else if (dropEl.closest('#tube-area')) {
    dropTube(fakeEvent);
  }
}

function handleTouchCancel(e) {
  cleanupTouch();
}

function cleanupTouch() {
  if (touchGhost && touchGhost.parentNode) {
    touchGhost.parentNode.removeChild(touchGhost);
  }
  touchGhost = null;
  touchDraggedId = null;
}

init();

function startLab() {
  const nameInp = document.getElementById('inp-name').value.trim();
  const classInp = document.getElementById('inp-class').value.trim();
  const numInp = document.getElementById('inp-number').value.trim();
  if(!nameInp || !classInp || !numInp) {
    alert("Please fill in all details before starting.");
    return;
  }
  studentName = nameInp;
  studentClass = classInp;
  studentNumber = numInp;
  document.getElementById('intro-panel').classList.remove('active-panel');
  document.getElementById('setup-panel').classList.add('active-panel');
}

function verifySetup() {
  let errors = [];
  if (!document.getElementById('t1-starch').checked || !document.getElementById('t1-amylase').checked || !document.getElementById('t1-ph2').checked || document.getElementById('t1-ph7').checked || document.getElementById('t1-ph9').checked || document.getElementById('t1-water').checked) {
    errors.push("❌ Test Tube 1 is incorrect. You need exactly: Starch, Amylase, and pH 2 Buffer.");
  }
  if (!document.getElementById('t2-starch').checked || !document.getElementById('t2-amylase').checked || !document.getElementById('t2-ph7').checked || document.getElementById('t2-ph2').checked || document.getElementById('t2-ph9').checked || document.getElementById('t2-water').checked) {
    errors.push("❌ Test Tube 2 is incorrect. You need exactly: Starch, Amylase, and pH 7 Buffer.");
  }
  if (!document.getElementById('t3-starch').checked || !document.getElementById('t3-amylase').checked || !document.getElementById('t3-ph9').checked || document.getElementById('t3-ph2').checked || document.getElementById('t3-ph7').checked || document.getElementById('t3-water').checked) {
    errors.push("❌ Test Tube 3 is incorrect. You need exactly: Starch, Amylase, and pH 9 Buffer.");
  }
  if (!document.getElementById('t4-starch').checked || document.getElementById('t4-amylase').checked || document.getElementById('t4-ph2').checked || document.getElementById('t4-ph7').checked || document.getElementById('t4-ph9').checked || !document.getElementById('t4-water').checked) {
    errors.push("❌ Control Tube is incorrect. You need exactly: Starch and Distilled Water.");
  }

  if (errors.length === 0) {
    document.getElementById('green-light').style.display = 'block';
    document.getElementById('btn-verify').disabled = true;
    setTimeout(() => {
      document.getElementById('setup-panel').classList.remove('active-panel');
      document.getElementById('review-panel').classList.add('active-panel');
    }, 2500);
  } else {
    alert("Errors found in your setup:\n\n" + errors.join("\n\n") + "\n\nPlease fix these and try again.");
  }
}

function checkQuiz() {
  const options = document.getElementsByName('volume-quiz');
  let selectedValue = "";
  for(let i = 0; i < options.length; i++) {
    if(options[i].checked) selectedValue = options[i].value;
  }
  const feedbackObj = document.getElementById('quiz-feedback');
  feedbackObj.style.display = 'block';

  if (selectedValue === "") {
    feedbackObj.style.color = "#e74c3c";
    feedbackObj.innerHTML = "Please select an answer.";
  } else if (selectedValue === "correct") {
    feedbackObj.style.color = "#27ae60";
    feedbackObj.innerHTML = "✅ Correct! Total volume must remain constant (10 mL) to keep the starch concentration a controlled variable. Proceeding to experiment...";
    setTimeout(() => {
      document.getElementById('review-panel').classList.remove('active-panel');
      document.getElementById('experiment-panel').classList.add('active-panel');
      highlightDraggables();
    }, 3500);
  } else {
    feedbackObj.style.color = "#e74c3c";
    feedbackObj.innerHTML = "❌ Incorrect. Hint: What happens to concentration if you have different total amounts of liquid holding the same amount of starch?";
  }
}

function updateInstruction(text) {
  document.getElementById('instruction-box').innerText = text;
}

function setDraggable(id, isDraggable) {
  const el = document.getElementById(id);
  el.setAttribute('draggable', isDraggable);
  if(isDraggable) el.classList.add('item-glow');
  else el.classList.remove('item-glow');
}

function highlightDraggables() {
  document.querySelectorAll('.draggable-item').forEach(el => {
    el.setAttribute('draggable', 'false');
    el.classList.remove('item-glow');
  });
  document.getElementById('spot-plate').classList.remove('target-glow');
  document.getElementById('tube-area').classList.remove('target-glow');

  if (labState === "ADD_IODINE") {
    setDraggable('item-iodine', true);
    document.getElementById('spot-plate').classList.add('target-glow');
  } else if (labState === "ADD_PH") {
    ['item-ph2', 'item-ph7', 'item-ph9', 'item-control'].forEach(id => {
      let val = id.replace('item-', '');
      if(!completedTubes.has(val)) setDraggable(id, true);
    });
    document.getElementById('tube-area').classList.add('target-glow');
  } else if (labState === "ADD_AMYLASE") {
    setDraggable('item-amylase', true);
    document.getElementById('tube-area').classList.add('target-glow');
  } else if (labState === "ADD_STARCH") {
    setDraggable('item-starch', true);
    document.getElementById('tube-area').classList.add('target-glow');
  } else if (labState === "TESTING") {
    setDraggable('item-Reaction Mixture', true);
    document.getElementById('spot-plate').classList.add('target-glow');
  }
}

function drag(ev) {
  if(ev.target.getAttribute('draggable') === 'false') {
    ev.preventDefault();
    return;
  }
  ev.dataTransfer.setData("text", ev.target.id);
}

function allowDrop(ev) {
  ev.preventDefault();
}

function dropPlate(ev) {
  ev.preventDefault();
  let data = ev.dataTransfer.getData("text");
  if (data === "item-iodine" && labState === "ADD_IODINE") {
    for (let i = 0; i < maxWells; i++) {
      document.getElementById(`well-${i}`).className = 'well colour-iodine';
    }
    labState = "ADD_PH";
    updateInstruction("Step 2: Drag a pH buffer (pH 2 / 7 / 9) OR Distilled Water (for the Control) into the Main Tube.");
    highlightDraggables();
  }
  else if (data === "item-Reaction Mixture" && labState === "TESTING") {
    takeSample();
  }
}

function dropTube(ev) {
  ev.preventDefault();
  let data = ev.dataTransfer.getData("text");

  // --- Step 2: Add pH buffer OR Distilled Water ---
  if (data.startsWith("item-ph") || data === "item-control") {
    if (labState === "ADD_PH") {
      selectedTube = data.replace("item-", "");

      if (selectedTube === "control") {
        // Control tube: NO amylase added, but STILL needs to wait 5 minutes
        // to match the timing/procedure of the other set-ups (fair test)
        document.getElementById('reaction-tube').innerHTML = `🧪<br>Distilled<br>Water`;
        document.getElementById('reaction-tube').style.background = "linear-gradient(to top, #e0f7fa 40%, white 40%)";
        labState = "INCUBATE";
        updateInstruction("Step 3 (Control): No amylase is added to the control tube. However, to keep the procedure identical to the other set-ups, click 'Incubate' and wait the same 5 minutes before adding starch.");
        highlightDraggables();
        document.getElementById('btn-incubate').disabled = false;
        document.getElementById('btn-incubate').classList.add('item-glow');
      } else {
        // pH buffers: next step is to add amylase
        let tubeLabel = formatPHLabel(selectedTube) + "<br>Buffer";
        document.getElementById('reaction-tube').innerHTML = `🧪<br>${tubeLabel}`;
        document.getElementById('reaction-tube').style.background = "linear-gradient(to top, #e0f7fa 40%, white 40%)";
        labState = "ADD_AMYLASE";
        updateInstruction("Step 3: Now drag the Amylase Solution into the Main Tube to add the enzyme.");
        highlightDraggables();
      }
    }
  }
  // --- Step 3: Add Amylase (only for pH tubes) ---
  else if (data === "item-amylase" && labState === "ADD_AMYLASE") {
    let tubeLabel = formatPHLabel(selectedTube) + "<br>+<br>Amylase";
    document.getElementById('reaction-tube').innerHTML = `🧪<br>${tubeLabel}`;
    document.getElementById('reaction-tube').style.background = "linear-gradient(to top, #c8e6c9 50%, white 50%)";
    labState = "INCUBATE";
    updateInstruction("Step 4: Click the 'Incubate' button below the tube to equilibrate the enzyme for 5 minutes.");
    highlightDraggables();
    document.getElementById('btn-incubate').disabled = false;
    document.getElementById('btn-incubate').classList.add('item-glow');
  }
  // --- Step 4/5: Add Starch ---
  else if (data === "item-starch" && labState === "ADD_STARCH") {
    document.getElementById('reaction-tube').style.background = "linear-gradient(to top, #b2ebf2 60%, white 60%)";
    document.getElementById('reaction-tube').innerHTML = `🧪<br>Reaction<br>Mixture`;
    labState = "TESTING";
    timerMinutes = 0;
    document.getElementById('timer-display').innerText = `Test: 00:00`;
    updateInstruction("Step 5: Starch added! Timer started. Drag the Reaction Mixture to the Spot Plate to test Minute 0 immediately.");
    highlightDraggables();
  }
}

function incubate() {
  document.getElementById('btn-incubate').disabled = true;
  document.getElementById('btn-incubate').classList.remove('item-glow');
  let waitTime = 1;
  document.getElementById('timer-display').innerText = `Wait: ${waitTime} min`;
  let interval = setInterval(() => {
    waitTime++;
    document.getElementById('timer-display').innerText = `Wait: ${waitTime} min`;
    if(waitTime >= 5) {
      clearInterval(interval);
      document.getElementById('timer-display').innerText = "Wait: 5m Done";
      labState = "ADD_STARCH";
      updateInstruction("Step 4 Complete: Incubation done! Drag the Starch Solution to the Main Tube to start the reaction.");
      highlightDraggables();
    }
  }, 600);
}

function takeSample() {
  if (wellsUsedCount >= maxWells) return;
  const well = document.getElementById(`well-${wellsUsedCount}`);

  if (timerMinutes === 0) well.className = 'well colour-starch';
  else {
    if (selectedTube === 'ph7') {
      if (timerMinutes === 1) well.className = 'well colour-partial';
      else well.className = 'well colour-iodine';
    } else if (selectedTube === 'ph2' || selectedTube === 'control') {
      well.className = 'well colour-starch';
    } else if (selectedTube === 'ph9') {
      if (timerMinutes <= 2) well.className = 'well colour-starch';
      else if (timerMinutes === 3) well.className = 'well colour-partial';
      else well.className = 'well colour-iodine';
    }
  }

  wellsUsedCount++;
  timerMinutes++;

  if (wellsUsedCount < maxWells) {
    document.getElementById('timer-display').innerText = `Test: 0${timerMinutes}:00`;
    updateInstruction(`Minute ${timerMinutes - 1} tested. Wait a simulated minute, then drag the Reaction Mixture to the Spot Plate again.`);
  } else {
    completedTubes.add(selectedTube);
    let resultText = "";
    if(selectedTube === 'ph7') resultText = "Results: The starch is gone! Amylase works perfectly at pH 7.";
    else if (selectedTube === 'ph2') resultText = "Results: At pH 2 (stomach acid), amylase is denatured. Starch remains.";
    else if (selectedTube === 'ph9') resultText = "Results: At pH 9, amylase works but more slowly than at pH 7.";
    else if (selectedTube === 'control') resultText = "Results: No amylase added, so starch remains throughout (as expected for the control).";

    setDraggable('item-Reaction Mixture', false);
    document.getElementById('spot-plate').classList.remove('target-glow');

    if (completedTubes.size >= 4) {
      updateInstruction(resultText + " All 4 tubes completed! Click 'Proceed to Part 4'.");
      document.getElementById('btn-part4').style.display = 'inline-block';
    } else {
      updateInstruction(resultText + ` (${completedTubes.size}/4 done). Click 'Reset Bench' below to test the next condition.`);
      document.getElementById('btn-reset').style.display = 'inline-block';
    }
  }
}

function resetBench() {
  for (let i = 0; i < maxWells; i++) {
    document.getElementById(`well-${i}`).className = 'well colour-empty';
  }
  document.getElementById('reaction-tube').innerHTML = "🧪<br>Empty<br>Tube";
  document.getElementById('reaction-tube').style.background = "white";
  document.getElementById('btn-reset').style.display = 'none';
  document.getElementById('timer-display').innerText = "Wait: 0 min";
  timerMinutes = 0;
  wellsUsedCount = 0;
  selectedTube = "";
  labState = "ADD_IODINE";
  updateInstruction("Step 1: Drag the Iodine bottle to the Spot Plate to fill the wells for the next test.");
  highlightDraggables();
}

function proceedToPart4() {
  document.getElementById('experiment-panel').classList.remove('active-panel');
  document.getElementById('conclusion-panel').classList.add('active-panel');
}

function checkPart4Quiz() {
  const q1 = document.querySelector('input[name="q1-final"]:checked');
  const q2 = document.querySelector('input[name="q2-final"]:checked');
  const feedback = document.getElementById('part4-feedback');
  feedback.style.display = 'block';

  if (!q1 || !q2) {
    feedback.style.color = "#e74c3c";
    feedback.innerHTML = "Please answer both questions before submitting.";
    return;
  }
  if (q1.value === 'correct' && q2.value === 'correct') {
    feedback.style.color = "#27ae60";
    feedback.innerHTML = "✅ Excellent work! You correctly identified that amylase works best at a neutral pH (7), and that because stomach acid denatures the enzyme, a fresh supply from the pancreas is biologically necessary in the small intestine. Proceeding to your Certificate...";
    setTimeout(() => {
      document.getElementById('conclusion-panel').classList.remove('active-panel');
      document.getElementById('certificate-panel').classList.add('active-panel');
      document.getElementById('display-name').innerText = studentName;
      document.getElementById('display-class').innerText = studentClass;
      document.getElementById('display-number').innerText = studentNumber;
    }, 2500);
  } else {
    feedback.style.color = "#e74c3c";
    feedback.innerHTML = "❌ Not quite. Review your lab results to see which pH cleared the starch the fastest, and think about what happens to the physical structure of an enzyme when it is dropped into stomach acid (pH 2).";
  }
}
</script>
</body>
</html>
