# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>CSS Animation + localStorage</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h2>Choose Your Theme</h2>
  <button id="toggleThemeBtn">Toggle Theme</button>
  <br><br>
  <img id="animatedImage" src="https://via.placeholder.com/150" alt="Sample Image">

  <script src="script.js"></script>
</body>
</html>

style.css
body {
  font-family: sans-serif;
  background-color: white;
  color: black;
  transition: background-color 0.5s ease, color 0.5s ease;
}

body.dark {
  background-color: #121212;
  color: white;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

img {
  display: block;
  margin-top: 30px;
  width: 150px;
  transition: transform 0.5s ease;
}

img.bounce {
  animation: bounce 0.6s ease;
}

@keyframes bounce {
  0%   { transform: translateY(0); }
  30%  { transform: translateY(-20px); }
  50%  { transform: translateY(0); }
  70%  { transform: translateY(-10px); }
  100% { transform: translateY(0); }
}

script.js
const toggleBtn = document.getElementById("toggleThemeBtn");
const image = document.getElementById("animatedImage");

// Load saved theme on page load
document.addEventListener("DOMContentLoaded", () => {
  const theme = localStorage.getItem("theme");
  if (theme === "dark") {
    document.body.classList.add("dark");
  }
});

// Toggle theme and save preference
toggleBtn.addEventListener("click", () => {
  document.body.classList.toggle("dark");
  const isDark = document.body.classList.contains("dark");
  localStorage.setItem("theme", isDark ? "dark" : "light");

  // Trigger bounce animation on image
  image.classList.remove("bounce"); // Reset if already added
  void image.offsetWidth; // Force reflow to restart animation
  image.classList.add("bounce");
});

