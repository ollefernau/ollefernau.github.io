
<head>
  <title>Media Player</title>
  <link rel="stylesheet" type="text/css" href="player.css">
</head>
<body>
  <div id="player">
    <div id="track-list">
      <ul>
        <li class="current-track" data-track="piano and strings.mp3">Track 1</li>
        <li data-track="track2.mp3">Track 2</li>
        <li data-track="track3.mp3">Track 3</li>
        <li data-track="track4.mp3">Track 4</li>
      </ul>
    </div>
    <audio id="audio" controls>
      <source src="track1.mp3" type="audio/mpeg">
    </audio>
    <div id="controls">
      <button id="play-pause">Play</button>
      <div id="time">
        <span id="current-time"></span> / <span id="total-duration"></span>
      </div>
    </div>
  </div>
  <script src="player.js"></script>
</body>
</html>
#track-list {
  width: 200px;
  float: left;
}

#track-list ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

#track-list li {
  padding: 10px;
  cursor: pointer;
}

#track-list .current-track {
  background-color: #ddd;
}

#player {
  width: 500px;
  margin: 0 auto;
}

#controls {
  margin-top: 10px;
}

#time {
  margin-left: 10px;
}
var trackList = document.querySelector("#track-list ul");
var tracks = trackList.querySelectorAll("li");
var audio = document.querySelector("#audio");
var playPause = document.querySelector("#play-pause");
var currentTime = document.querySelector("#current-time");
var totalDuration = document.querySelector("#total-duration");

// Add click event to each track in the track list
for (var i = 0; i < tracks.length; i++) {
  tracks[i].addEventListener("click", function() {
    var currentTrack = trackList.querySelector(".current-track");
    currentTrack.classList.remove("current-track");
    this.classList.add("current-track");
    audio.src = this.dataset.track;
    audio.play();
    playPause.innerHTML = "Pause";
    totalDuration.innerHTML = formatTime(audio.duration);
  });
}

// Update current time as the audio plays
audio.addEventListener("timeupdate", function() {
  currentTime.innerHTML = formatTime(audio.currentTime);
});


      
        
