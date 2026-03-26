<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vector Motion Simulator</title>
    <style>
        body { font-family: sans-serif; background: #f4f7f6; display: flex; flex-direction: column; align-items: center; padding: 20px; color: #333; }
        .card { background: white; padding: 25px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); width: 100%; max-width: 850px; }
        .controls { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-bottom: 20px; background: #eee; padding: 15px; border-radius: 10px; }
        .control-group { display: flex; flex-direction: column; text-align: center; }
        canvas { background: #fff; border: 2px solid #ddd; border-radius: 8px; cursor: crosshair; width: 100%; height: 400px; }
        .formula { font-family: "Courier New", monospace; font-weight: bold; background: #eefbff; padding: 15px; border-radius: 8px; margin-bottom: 20px; border-left: 5px solid #007bff; }
        label { font-size: 14px; margin-bottom: 5px; color: #666; }
        input[type=range] { cursor: pointer; }
        .values { font-weight: bold; color: #007bff; }
    </style>
</head>
<body>

<div class="card">
    <h2>Vector Motion: r(t) → v(t) → a(t)</h2>
    
    <div class="controls">
        <div class="control-group">
            <label>X-Accel (i): <span class="values" id="valA">3</span></label>
            <input type="range" id="coeffA" min="-10" max="10" step="0.5" value="3">
        </div>
        <div class="control-group">
            <label>Y-Vel (j): <span class="values" id="valB">5</span></label>
            <input type="range" id="coeffB" min="-15" max="15" step="0.5" value="5">
        </div>
        <div class="control-group">
            <label>Y-Accel (j): <span class="values" id="valC">-8</span></label>
            <input type="range" id="coeffC" min="-15" max="15" step="0.5" value="-8">
        </div>
    </div>

    <div class="formula" id="mathDisplay">
        <!-- Formulas will be injected here -->
    </div>

    <canvas id="simCanvas"></canvas>
    <p style="font-size: 12px; color: #888;">* Red dot = Object, Blue line = Trajectory. Animation loops 0 to 2 seconds.</p>
</div>

<script>
    const canvas = document.getElementById('simCanvas');
    const ctx = canvas.getContext('2d');
    
    // UI Elements
    const inputA = document.getElementById('coeffA');
    const inputB = document.getElementById('coeffB');
    const inputC = document.getElementById('coeffC');
    const mathDisplay = document.getElementById('mathDisplay');

    let time = 0;

    function draw() {
        // Set internal resolution
        canvas.width = canvas.clientWidth;
        canvas.height = canvas.clientHeight;
        
        const a = parseFloat(inputA.value);
        const b = parseFloat(inputB.value);
        const c = parseFloat(inputC.value);

        // Update Text
        document.getElementById('valA').innerText = a;
        document.getElementById('valB').innerText = b;
        document.getElementById('valC').innerText = c;

        mathDisplay.innerHTML = `
            r(t) = (${a}t²)i + (${b}t + ${c}t²)j <br>
            v(t) = (${2*a}t)i + (${b} + ${2*c}t)j <br>
            a(t) = (${2*a})i + (${2*c})j
        `;

        // Clear Canvas
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        // Draw Grid
        ctx.strokeStyle = "#eee";
        ctx.beginPath();
        for(let i=0; i<canvas.width; i+=40) { ctx.moveTo(i,0); ctx.lineTo(i,canvas.height); }
        for(let i=0; i<canvas.height; i+=40) { ctx.moveTo(0,i); ctx.lineTo(canvas.width,i); }
        ctx.stroke();

        const centerX = canvas.width / 4;
        const centerY = canvas.height / 2;
        const scale = 15; // Scale for visualization

        // Draw Trajectory Line
        ctx.strokeStyle = "#007bff";
        ctx.lineWidth = 2;
        ctx.beginPath();
        ctx.moveTo(centerX, centerY);
        for(let t=0; t<=2.5; t+=0.05) {
            let px = centerX + (a * t * t) * scale;
            let py = centerY - (b * t + c * t * t) * scale;
            ctx.lineTo(px, py);
        }
        ctx.stroke();

        // Draw Animated Object
        let objX = centerX + (a * time * time) * scale;
        let objY = centerY - (b * time + c * time * time) * scale;

        ctx.fillStyle = "#ff4757";
        ctx.beginPath();
        ctx.arc(objX, objY, 8, 0, Math.PI * 2);
        ctx.fill();

        // Time Update
        time += 0.01;
        if (time > 2.5) time = 0;

        requestAnimationFrame(draw);
    }

    draw();
</script>

</body>
</html>
