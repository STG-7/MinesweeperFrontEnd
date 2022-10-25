---
toc: true
layout: post
description: Front end for minesweeper!
categories: [markdown]
title: Minesweeper FrontEnd
---


</head>
<!--code for the login and registration forms that take username and password.-->
<body>
<section id="login" style="display:block;">
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

<section id="Register" style="display:block;">
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
<!--work in progress code for communicaton between frontend and backend.-->
<script>
    const username = "user"
    const password = "pass"
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
</script>

</body>