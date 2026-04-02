<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Live Monitoring</title>

<style>

body {
  margin: 0;
  font-family: poppins, sans-serif;
  background: #f4f6f9;
}

.container {
  width: 96%;
  max-width: 1600px;
  margin: auto;
}

/* 🔥 VERY LARGE VIDEO */
.video-container {
  margin: 10px auto;
  position: relative;
  background: black;
  border-radius: 10px;
  overflow: hidden;
}

iframe {
  width: 100%;
  height: 85vh;   /* 🔥 EXTRA LARGE */
  min-height: 450px;
  max-height: 900px;
  border: none;
}

.ribbon {
  position: absolute;
  top: 0;
  width: 100%;
  background: rgb(2, 82, 20);
  color: white;
  font-family: poppins, sans-serif;
  padding: 12px;
  text-align: center;
  font-weight: bold;
  font-size: 15px;
}

/* TIMER */
.timer-box {
  margin: 15px auto;
  background: #d9534f;
  color: white;
  display: flex;
  font-family: poppins, sans-serif;
  justify-content: space-between;
  align-items: center;
  padding: 12px 15px;
  border-radius: 8px;
  font-weight: bold;
  font-size: 18px;
  flex-wrap: wrap;
}

.timer {
  background: green;
  padding: 8px 16px;
  border-radius: 5px;
}

/* INSTRUCTIONS */
.instructions {
  margin: 15px auto;
  background: white;
  font-family: poppins, sans-serif;
  padding: 15px;
  border-radius: 10px;
}

.highlight-box {
  background: #fff3cd;
  border-left: 6px solid #ffc107;
  padding: 12px;
  margin-top: 12px;
  font-family: poppins, sans-serif;
  border-radius: 8px;
  font-weight: bold;
}

/* POPUP */
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.7);
  display: none;
  justify-content: center;
  font-family: poppins, sans-serif;
  align-items: center;
  z-index: 2000;
  padding: 15px;
}

.popup-box {
  background: white;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  width: 100%;
  max-width: 320px;
}

.popup-box h3 {
  color: red;   /* 🔴 RED WARNING TITLE */
}

.popup-box p {
  color: red;   /* 🔴 RED WARNING TEXT */
  font-weight: bold;
}

/* ✅ GREEN BUTTON */
.popup button {
  margin-top: 10px;
  padding: 10px 18px;
  background: green;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

/* 📱 MOBILE */
@media (max-width: 600px) {
  iframe {
    height: 60vh;
    min-height: 300px;
  }

  .timer-box {
    flex-direction: column;
    text-align: center;
    font-size: 16px;
  }
}

/* 📲 TABLET */
@media (min-width: 601px) and (max-width: 1024px) {
  iframe {
    height: 75vh;
  }
}

</style>
</head>

<body>

<div class="container">

  <!-- VIDEO -->
  <div class="video-container">
    <div class="ribbon">LIVE PROCTORING IN PROGRESS</div>
    <iframe src="https://vdo.ninja/?push=DNQNhcC&label=test_link_3&aspectratio=1.77777"
      allow="camera; microphone;"></iframe>
  </div>

  <!-- TIMER -->
  <div class="timer-box">
    ⚠️ Do not switch tabs or leave the screen
    <div class="timer" id="timer">90:00</div>
  </div>

  <!-- INSTRUCTIONS -->
  <div class="instructions">
    <h3>Instructions</h3>
    <ul>
      <li>Your full face must remain visible on the camera at all times.</li>
      <li>Scrolling down will not affect camera visibility. However, switching to another tab, app, or chatting may affect the camera and could lead to disqualification.</li>
      <li>Test duration: 70–90 minutes.</li>
      <li>Do not switch tabs or leave the screen. Doing so may disqualify you.</li>
      <li>Do not open or interact with WhatsApp notifications during the test. Doing so may affect your exam and lead to disqualification.</li>
      <li>You must maintain privacy while taking the test.</li>
    </ul>

    <div class="highlight-box">
      Scroll down and act like read. Behave as if you are actively taking the test.
    </div>
  </div>

</div>

<!-- POPUP -->
<div class="popup" id="popup">
  <div class="popup-box">
    <h3>⚠️ Warning!</h3>
    <p>You switched tabs. This activity is monitored.</p>
    <button onclick="closePopup()">Continue Test</button>
  </div>
</div>

<script>
let time = 90 * 60;
const timerEl = document.getElementById("timer");

setInterval(() => {
  let min = Math.floor(time / 60);
  let sec = time % 60;

  timerEl.innerText =
    (min < 10 ? "0" + min : min) + ":" +
    (sec < 10 ? "0" + sec : sec);

  if (time > 0) time--;
}, 1000);

// TAB SWITCH DETECTION
document.addEventListener("visibilitychange", function() {
  if (document.hidden) {
    document.getElementById("popup").style.display = "flex";
  }
});

function closePopup() {
  document.getElementById("popup").style.display = "none";
}
</script>

</body>
</html>
