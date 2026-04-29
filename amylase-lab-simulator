<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amylase Activity Lab Simulator</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f0f4f8; margin: 0; padding: 20px; color: #333; }
        .container { max-width: 900px; margin: 0 auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        h1 { text-align: center; color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 10px; }
        h2 { color: #34495e; border-left: 5px solid #3498db; padding-left: 10px;}
        
        /* Panels */
        .panel { display: none; padding: 20px; border: 1px solid #ddd; border-radius: 8px; margin-top: 20px; background-color: #fafafa; }
        .active-panel { display: block; }
        
        /* Setup Phase Styles */
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

        /* Review Phase (New) Styles */
        .volume-list { background: #fff; padding: 10px; border-radius: 5px; text-align: left; font-size: 0.9em; box-shadow: inset 0 1px 3px rgba(0,0,0,0.1); border: 1px solid #ecf0f1; margin-top: 10px;}
        .volume-list li { margin-bottom: 5px; color: #2c3e50; }
        .quiz-container { background: #fff3cd; border: 1px solid #ffeeba; padding: 20px; border-radius: 8px; margin-top: 20px; color: #856404; }
        .quiz-container h3 { margin-top: 0; color: #856404;}
        .quiz-option { margin-bottom: 10px; display: flex; align-items: flex-start; }
        .quiz-option input { margin-top: 4px; margin-right: 10px; cursor: pointer;}
        .quiz-option label { cursor: pointer; font-weight: 500;}
        #quiz-feedback { margin-top: 15px; font-weight: bold; font-size: 1.1em; display: none; }

        /* Experiment Phase Styles */
        .instructions { background: #e8f4f8; border-left: 5px solid #17a2b8; padding: 15px; margin-bottom: 20px; font-weight: bold; font-size: 1.1em; color: #0c5460; line-height: 1.4;}
        .controls { display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 20px; align-items: center; justify-content: center;}
        button { padding: 10px 15px; border: none; border-radius: 5px; background-color: #3498db; color: white; font-weight: bold; cursor: pointer; transition: 0.3s; font-size: 0.95em;}
        button:hover { background-color: #2980b9; }
        button:disabled { background-color: #b0bec5; cursor: not-allowed; }
        
        select { padding: 10px; border-radius: 5px; border: 2px solid #3498db; background: white; font-size: 0.95em;}
        select:disabled { border-color: #b0bec5; }

        .timer { font-size: 1.8em; font-family: monospace; background: #2c3e50; color: white; padding: 15px; border-radius: 8px; text-align: center; width: 150px; margin: 0 auto 20px auto; box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);}
        
        /* Schematic Diagram Styles */
        .diagram-container { display: flex; align-items: center; justify-content: center; gap: 20px; background: #fff; padding: 20px; border-radius: 10px; border: 2px dashed #bdc3c7; margin-bottom: 20px; flex-wrap: wrap;}
        .diagram-step { display: flex; flex-direction: column; align-items: center; text-align: center; font-size: 0.9em; font-weight: bold; color: #34495e;}
        .css-tube { width: 30px; height: 80px; border: 3px solid #7f8c8d; border-top: none; border-radius: 0 0 15px 15px; background: linear-gradient(to top, #eef 60%, white 60%); position: relative; margin-bottom: 10px;}
        .css-pipette { font-size: 30px; transform: rotate(-45deg); margin-bottom: 5px;}
        .css-arrow { font-size: 30px; color: #3498db; font-weight: bold;}
        .css-drop { font-size: 20px; color: #3498db; margin-bottom: 5px;}
        .css-well { width: 50px; height: 50px; border-radius: 50%; border: 3px solid #bdc3c7; background-color: #d4a373; margin-bottom: 10px;}

        .spot-plate { display: grid; grid-template-columns: repeat(6, 1fr); gap: 15px; background: #ecf0f1; padding: 20px; border-radius: 10px; box-shadow: inset 0 2px 5px rgba(0,0,0,0.1); margin-top: 20px; }
        .well-container { text-align: center; }
        .well { width: 60px; height: 60px; background: white; border-radius: 50%; border: 3px solid #bdc3c7; margin: 0 auto 8px auto; transition: background-color 0.5s ease; box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);}
        .well-container small { font-weight: bold; color: #7f8c8d;}

        /* Colors for reactions */
        .color-empty { background-color: white; }
        .color-iodine { background-color: #d4a373; border-color: #a67c52;} 
        .color-starch { background-color: #1a1a2e; border-color: #0c0c1a;} 
        .color-partial { background-color: #5d4037; border-color: #4e342e;} 
    </style>
</head>
<body>

<div class="container">
    <h1>Investigation: Effect of pH on Amylase Activity</h1>

    <div id="setup-panel" class="panel active-panel">
        <h2>Part 1: Laboratory Setup Verification</h2>
        <div class="setup-description">
            <p><strong>Goal:</strong> Prove why the pancreas secretes fresh amylase after food leaves the stomach (pH 2) and enters the small intestine (pH 9).</p>
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
            
            <div class="quiz-option">
                <input type="radio" id="q1-a" name="volume-quiz" value="wrong1">
                <label for="q1-a">To dilute the starch further so it breaks down naturally without any enzymes.</label>
            </div>
            <div class="quiz-option">
                <input type="radio" id="q1-b" name="volume-quiz" value="correct">
                <label for="q1-b">To keep the total volume at 10 mL, ensuring the concentration of starch is equal across all set-ups.</label>
            </div>
            <div class="quiz-option">
                <input type="radio" id="q1-c" name="volume-quiz" value="wrong2">
                <label for="q1-c">Because 5 mL is the standard safety requirement for neutralizing any accidental acids in the lab.</label>
            </div>
            <div class="quiz-option">
                <input type="radio" id="q1-d" name="volume-quiz" value="wrong3">
                <label for="q1-d">Because distilled water evaporates quickly, so extra is needed to prevent the tube from drying out.</label>
            </div>

            <div style="margin-top: 20px;">
                <button onclick="checkQuiz()">Submit Answer</button>
            </div>
            <div id="quiz-feedback"></div>
        </div>
    </div>

    <div id="experiment-panel" class="panel">
        <h2>Part 3: Conducting the Experiment</h2>
        
        <div class="diagram-container">
            <div class="diagram-step">
                <div class="css-tube"></div>
                <span>Reaction Mixture<br>(Starch + Amylase + pH)</span>
            </div>
            <div class="diagram-step">
                <div class="css-pipette">🖊️</div>
                <span>Extract 1 Drop</span>
            </div>
            <div class="diagram-step">
                <div class="css-arrow">➔</div>
            </div>
            <div class="diagram-step">
                <div class="css-drop">💧</div>
                <div class="css-well"></div>
                <span>Test in Spot Plate<br>(Contains Iodine Drop)</span>
            </div>
        </div>

        <div id="instruction-box" class="instructions">
            Step 1: First, add drops of Iodine solution to all the wells on your spot plate.
        </div>

        <div class="controls">
            <button id="btn-add-iodine" onclick="addIodine()">1. Add Iodine Solution</button>
            <select id="tube-selector" disabled>
                <option value="none">-- 2. Select Tube --</option>
                <option value="ph2">Test Tube 1 (pH 2 + Amylase) (Stomach)</option>
                <option value="ph7">Test Tube 2 (pH 7 + Amylase) (Mouth Cavity)</option>
                <option value="ph9">Test Tube 3 (pH 9 + Amylase) (Small Intestine)</option>
                <option value="control">Control Tube (Water)</option>
            </select>
            <button id="btn-incubate" onclick="incubate()" disabled>3. Incubate Tube (Wait 5 Mins)</button>
            <button id="btn-mix" onclick="addStarchAndStart()" disabled>4. Add Starch & Start the Timer</button>
            <button id="btn-test" onclick="takeSample()" disabled>5. Transfer 1 Drop to Plate at 1-minute Intervals</button>
            <button id="btn-reset" onclick="resetPlate()" style="background-color: #e74c3c;">Reset</button>
        </div>

        <div class="timer" id="timer-display">Wait: 0 min</div>

        <div class="spot-plate" id="spot-plate">
            </div>
    </div>
</div>

<script>
    let timerMinutes = 0;
    let selectedTube = "";
    let wellsUsedCount = 0;
    const maxWells = 6;

    // Generate Spot Plate UI 
    const spotPlateDiv = document.getElementById('spot-plate');
    for (let i = 0; i < maxWells; i++) {
        spotPlateDiv.innerHTML += `
            <div class="well-container">
                <div class="well color-empty" id="well-${i}"></div>
                <small>${i} min</small>
            </div>
        `;
    }

    // Phase 1 Logic: Setup Validation
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
                document.getElementById('review-panel').classList.add('active-panel'); // Go to new panel
            }, 2500);
        } else {
            alert("Errors found in your setup:\n\n" + errors.join("\n\n") + "\n\nPlease fix these and try again.");
        }
    }

    // Phase 1.5 Logic: Quiz
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
            }, 3500);
        } else {
            feedbackObj.style.color = "#e74c3c";
            feedbackObj.innerHTML = "❌ Incorrect. Hint: What happens to concentration if you have different total amounts of liquid holding the same amount of starch?";
        }
    }

    // Phase 3 Logic: Experiment
    function updateInstruction(text) {
        document.getElementById('instruction-box').innerText = text;
    }

    function addIodine() {
        for (let i = 0; i < maxWells; i++) {
            document.getElementById(`well-${i}`).className = 'well color-iodine';
        }
        document.getElementById('btn-add-iodine').disabled = true;
        document.getElementById('tube-selector').disabled = false;
        
        document.getElementById('tube-selector').addEventListener('change', function() {
            if(this.value !== "none") {
                document.getElementById('btn-incubate').disabled = false;
                if(this.value === 'control') {
                    updateInstruction(`Step 3: You selected the Control Tube. Click Incubate to simulate waiting 5 minutes for water to reach room temp.`);
                } else {
                    updateInstruction(`Step 3: You selected a pH tube. Click 'Incubate' to mix Amylase with the buffer and let the enzyme adjust for 5 minutes.`);
                }
            } else {
                document.getElementById('btn-incubate').disabled = true;
            }
        });

        updateInstruction("Step 2: Select a tube from the dropdown.");
    }

    function incubate() {
        document.getElementById('tube-selector').disabled = true;
        document.getElementById('btn-incubate').disabled = true;
        let waitTime = 1;
        document.getElementById('timer-display').innerText = `Wait: ${waitTime} min`;
        
        let interval = setInterval(() => {
            waitTime++;
            document.getElementById('timer-display').innerText = `Wait: ${waitTime} min`;
            if(waitTime >= 5) {
                clearInterval(interval);
                document.getElementById('timer-display').innerText = "Incubated 5m";
                document.getElementById('btn-mix').disabled = false;
                updateInstruction("Step 4: Incubation complete! Click 'Add Starch & Start' to begin the reaction.");
            }
        }, 600); 
    }

    function addStarchAndStart() {
        selectedTube = document.getElementById('tube-selector').value;
        document.getElementById('btn-mix').disabled = true;
        document.getElementById('btn-test').disabled = false;
        
        timerMinutes = 0;
        wellsUsedCount = 0;
        document.getElementById('timer-display').innerText = `Test: 00:00`;
        updateInstruction("Step 5: Starch added! The reaction has started. Test your first drop immediately by clicking the 'Transfer 1 Drop' button.");
        takeSample(); 
    }

    function takeSample() {
        if (wellsUsedCount >= maxWells) return;

        const well = document.getElementById(`well-${wellsUsedCount}`);
        
        if (timerMinutes === 0) {
            well.className = 'well color-starch'; 
        } else {
            if (selectedTube === 'ph7') {
                if (timerMinutes === 1) well.className = 'well color-partial'; 
                else well.className = 'well color-iodine'; 
            } else if (selectedTube === 'ph2') {
                well.className = 'well color-starch'; 
            } else if (selectedTube === 'ph9') {
                if (timerMinutes <= 2) well.className = 'well color-starch'; 
                else if (timerMinutes === 3) well.className = 'well color-partial'; 
                else well.className = 'well color-iodine'; 
            } else if (selectedTube === 'control') {
                well.className = 'well color-starch';
            }
        }

        wellsUsedCount++;
        timerMinutes++;
        
        if (wellsUsedCount < maxWells) {
            document.getElementById('timer-display').innerText = `Test: 0${timerMinutes}:00`;
            updateInstruction(`Minute ${timerMinutes - 1} tested. Click 'Transfer 1 Drop' to advance time 1 minute and test the next drop.`);
        } else {
            document.getElementById('btn-test').disabled = true;
            if(selectedTube === 'ph7'){
               updateInstruction("Results: The starch is gone! Amylase works perfectly at pH 7. Reset the plate to test the other tubes.");
            } else if (selectedTube === 'ph2'){
               updateInstruction("Results: At pH 2 (stomach acid), amylase is denatured. Starch stays present. Reset and test another tube.");
            } else {
               updateInstruction("Experiment complete for this tube. Reset the plate to test another.");
            }
        }
    }

    function resetPlate() {
        for (let i = 0; i < maxWells; i++) {
            document.getElementById(`well-${i}`).className = 'well color-empty';
        }
        document.getElementById('btn-add-iodine').disabled = false;
        document.getElementById('tube-selector').disabled = true;
        document.getElementById('tube-selector').value = "none";
        document.getElementById('btn-incubate').disabled = true;
        document.getElementById('btn-mix').disabled = true;
        document.getElementById('btn-test').disabled = true;
        document.getElementById('timer-display').innerText = "Wait: 0 min";
        timerMinutes = 0;
        wellsUsedCount = 0;
        updateInstruction("Step 1: First, add drops of Iodine solution to all the wells on your spot plate.");
    }
</script>

</body>
</html>
