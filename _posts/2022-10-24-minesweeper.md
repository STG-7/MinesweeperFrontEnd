---
toc: true
layout: post
description: Front end for minesweeper!
categories: [markdown]
title: Minesweeper FrontEnd
---

<!--bakground styling-->
<head>
    <style>
        body {
            background: linear-gradient(-45deg, #bbf0e5, rgb(196, 226, 238), rgb(176, 231, 231), rgb(97, 130, 226), rgb(176, 231, 231));
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
            height: 100vh;
        }
        @keyframes gradient {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }
    </style>
</head>
<!--code for the login and registration forms that take username and password.-->
<body>
<section id="login">
<!-- Login form for Minesweeper game, set display to false after successful login-->
    <h2>Login</h2>
    <form action = "user_auth.py" method="POST">
    <label for="user">Username / Nombre de Usario:</label><br>
    <input type="text" id="user" name="user" value=""><br>
    <label for="pass">Password / Clave:</label><br>
    <input type="text" id="pass" name="pass" value=""><br>
    <input type="submit" name ="submit" value = "SUBMIT/ENVIAR">
    </form>
</section>

<section id="Register">
<!-- Registration form for Minesweeper game, set display to false after successful login-->
    <h2>Register</h2>
    <form method="POST">
    <label for="user">Username / Nombre de Usario:</label><br>
    <input type="text" id="user" name="user" value=""><br>
    <label for="pass">Password / Clave:</label><br>
    <input type="text" id="pass" name="pass" value=""><br>
    <input type="submit" name ="submit" value = "SUBMIT/ENVIAR">
    </form>
</section>
<<<<<<< HEAD:_posts/2022-10-24-min.md
<!-- script for authentications, add minesweeper functions below when possible-->
<script>

=======
<!--work in progress code for communicaton between frontend and backend.-->
<script>
    const username = "user"
    const password = "pass"
>>>>>>> 78a956198293ac431ffba12c5022a69cd937c624:_posts/2022-10-24-minesweeper.md
    const url = "frost.nighthawkcodescrums.gq/api/auth"
    const options = {
        method: 'GET',
        mode: 'cors',
        cache: 'default', 
        credentials: 'omit', 
        headers: {
            'Content-Type': 'application/json'
            }
        };
<<<<<<< HEAD:_posts/2022-10-24-min.md
    var usr, pwd;
=======
    const put_options = {...options, method: 'PUT'};
    function reaction(type, put_url, elemID) {
        fetch('frost.nighthawkcodescrums.gq/api/auth')
        .then(response => {
        if (response.status !== 200) {
            error('GET API response failure: ' + response.status);
        return;
        response.json().then(data => {
        document.getElementById(_GetPWD)
        })
>>>>>>> 78a956198293ac431ffba12c5022a69cd937c624:_posts/2022-10-24-minesweeper.md
</script>

</body>