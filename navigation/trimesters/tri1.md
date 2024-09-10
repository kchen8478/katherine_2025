---
layout: page
title: Trimester 1
units: "1,2,3,4,5,6,7,8,9"
search_exclude: true
menu: /nav/home.html
---
<!-- tri2.md has the border info and the old frontend development (button code) -->
<!-- GRADIENT LINE -->
<html>
<hr class="gradient">
</html>
<style>
hr.gradient {
  height: 3px;
  border: none;
  border-radius: 6px;
  background: linear-gradient(
    90deg,
    rgba(13, 8, 96, 1) 0%,
    rgba(9, 9, 121, 1) 21%,
    rgba(6, 84, 170, 1) 51%,
    rgba(0, 255, 113, 1) 100%
  );
}
</style>

# Frontend Development (Button)
<!--
<html>
<head>
<style>
div {
  border: 1px solid #9999FF;
  padding: 5px;
  color: white;
}
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}
</style>
</head>
<body>

<div class="clearfix">
  <button onclick="myFunction()">:D</button>

<p id="demo"></p>

<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "D:";
}
</script>
Coding, also known as programming, is the process of writing instructions for computers to follow. These instructions, or programs, tell computers what to do, such as build websites and apps, analyze data, and create software.
</div>

</body>
</html> -->
<html>
<head>
<style>
p.solid {border-style: solid;}
</style>
</head>

<body>
<p class="solid">
Coding, also known as programming, is the process of writing instructions for computers to follow. These instructions, or programs, tell computers what to do, such as build websites and apps, analyze data, and create software. 
<br>
<button onclick="myFunction()">:D</button>

<p id="demo"></p>

<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "D:";
}
</script>
</p>
</body>

<body>
<p class="solid">
    <a href="https://miro.medium.com/v2/resize:fit:1400/0*7VyEZgzwUhQMeBqb">link1</a>
    <br>
    <a href="https://media.licdn.com/dms/image/D4D12AQF6mW4EuB-99Q/article-cover_image-shrink_720_1280/0/1692951785182?e=2147483647&v=beta&t=I6_1-aBTAg0fihJHret-C4hRNuffBu8JyrqKfXsm74w">link2</a>
    <br>
    Coding tells a machine which actions to perform and how to complete tasks. Programming languages provide the rules for building websites, apps, and other computer-based technologies. Each programming language helps humans accurately communicate with machines.
</p>
</body>
</html>

<!-- GRADIENT LINE -->
<html>
<hr class="gradient">
</html>

<style>
hr.gradient {
  height: 3px;
  border: none;
  border-radius: 6px;
  background: linear-gradient(
    90deg,
    rgba(13, 8, 96, 1) 0%,
    rgba(9, 9, 121, 1) 21%,
    rgba(6, 84, 170, 1) 51%,
    rgba(0, 255, 113, 1) 100%
  );
}
</style>

<p> </p>

# Github Pages Playground
<!-- <p>Make a copy of the Github Pages Notebook folder, then create a nav/github_pages.html, then link it to an md file</p> -->

{%include nav/github_pages.html %} 
{%github_playground.html%}