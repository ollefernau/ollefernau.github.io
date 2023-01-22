# Olle Fernau




<!DOCTYPE html>
<html>
<head>
  <title>Olle Fernau>
  <style>
    body {
      background-color: orange;
      text-align: left; /* center the elements inside the body */
    }
    h1 {
      text-align: Left
    }
    /* Style for the media player */
    .media-player {
      width: 50%; /* half of the screen width */
      margin: 0 auto; /* center the element horizontally */
    }
    /* Style for the progress bar */
    .progress-bar {
      width: 100%;
      height: 30px;
      background: #ccc;
    }
    .progress {
      height: 100%;
      background: #4CAF50;
    }
  </style>
</head>
<body>
  <h1>Contact</h1>
  <h1>Music</h1>
  <div class="media-player">
    <audio id="audio" controls>
      <source src="your-music-file.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <br>
    <button id="play-pause" onclick="playPause()">Play/Pause</button>
    <input type="range" id="volume" min="0" max="1" step="0.1" onchange="changeVolume()">
    <br>
    <div class="progress-bar">
      <div class="progress" id="progress"></div>
    </div>
  </div>
  <script>
    var audio = document.getElementById("audio");
    var playPause = document.getElementById("play-pause");
    var volume = document.getElementById("volume");
    var progress = document.getElementById("progress");

    function playPause() {
      if (audio.paused) {
        audio.play();
        playPause.innerHTML = "Pause";
      } else {
        audio.pause();
        playPause.innerHTML = "Play";
      }
    }

    function changeVolume() {
      audio.volume = volume.value;
    }

    audio.addEventListener("timeupdate", function() {
      var currentTime = audio.currentTime;
      var duration = audio.duration;
      var percentage = (currentTime / duration) * 100;
      progress.style.width = percentage + "%";
    });
  </script>
</body>
</html>

