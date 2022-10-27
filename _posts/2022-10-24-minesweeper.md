---
toc: true
layout: post
description: Front end for minesweeper!
categories: [markdown]
title: Minesweeper FrontEnd
---


<!--code for the login and registration forms that take username and password.-->
<body>
<section id="login" style="display:block;">
<!-- Login form for Minesweeper game, set display to false after successful login-->
    <h2>Login</h2>
    <form  method="POST">
    <label for="user">Username / Nombre de Usario:</label><br>
    <input type="text" id="user_login" name="user" value=""><br>
    <label for="pass">Password / Clave:</label><br>
    <input type="text" id="pwd_login" name="pass" value=""><br>
    <!--use a button instead of input-->
    <input type="submit" onclick= "loginVerify()" name ="submit" value = "SUBMIT/ENVIAR">
    </form>
</section>

<section id="Register" style="display:block;">
<!-- Registration form for Minesweeper game, set display to false after successful login-->
    <h2>Register</h2>
    <form method="POST">
    <label for="user">Username / Nombre de Usario:</label><br>
    <input type="text" id="rg_usr" name="user" value=""><br>
    <label for="pass">Password / Clave:</label><br>
    <input type="text" id="rg_pwd" name="pass" value=""><br>
    <input type="submit" onclick= "registration()" name ="submit" value = "SUBMIT/ENVIAR">
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
    //function should grab either true or false from the frost API, if true, reveal game grid, if false, do nothing, send an alert or smthin
    function loginVerify(){
        let usr = document.getElementById("user_login").value;
        let pwd = document.getElementById("pwd_login").value;
        let auth_url = "frost.nighthawkcodescrums.gq/api/auth/" + usr + "/" + pwd + "/verify";
        // make a query to frost.nighthawkcodescrums.gq/api/auth/<usr>/<pwd>/verify
        // If the returned statement is "true", hide the login and registration, and display high score and game board
        // if false, clear form, and send an alert to the user
        alert(auth_url)
    }
    function registration(){
        let usr = document.getElementById("rg_usr").value;
        let pwd = document.getElementById("rg_pwd").value;
        // make a query to frost.nighthawkcodescrums.gq/api/auth/<usr>/<pwd>/registration
    }
    function reaction(type, put_url, elemID) {
        fetch('frost.nighthawkcodescrums.gq/api/auth')
        .then(response => {
        if (response.status !== 200) {
            error('GET API response failure: ' + response.status);
        return;
        response.json().then(data => {
        document.getElementById(_GetPWD)
        })
    }
</script>

</body>