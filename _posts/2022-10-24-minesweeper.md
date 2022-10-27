---
layout: post
description: Click to Play
categories: [markdown]
title: Play
---


<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"></script>
<!--code for the login and registration forms that take username and password.-->
<body>
<style>
    #login {
        background: white;
        border-radius: 18px;
        margin-top: 5%;
        margin-bottom: 5%;
        margin-left: 15%;
        margin-right: 15%;
    }
    #register {
        background: white;
        border-radius: 18px;
        margin-top: 5%;
        margin-bottom: 5%;
        margin-left: 15%;
        margin-right: 15%;
    }
    form{
        margin-top: 2em;
        margin-bottom: 2em;
        margin-left: auto;
        margin-right: auto;
        width: 10em
    }
</style>

<section id="login" style="display:block;">
<!-- Login form for Minesweeper game, set display to false after successful login-->
    <form>
        <br>
        <h2>Login</h2>
        <label for="user">Username / Nombre de Usario:</label><br>
        <input type="text" id="usr_login" name="user" value=""><br>
        <label for="pass">Password / Clave:</label><br>
        <input type="text" id="pwd_login" name="pass" value=""><br><br>
        <!--use a button instead of input-->
        <button id ="login_submit" type='button'>SUBMIT/ENVIAR</button>
        <script>
            $("#login_submit").click(function() {
                let usr = document.getElementById("usr_login").value;
                let pwd = document.getElementById("pwd_login").value;
                let auth_url = "https://frost.nighthawkcodescrums.gq/api/auth/" + usr + "/" + pwd + "/verify";
                const headers = {
                        method: 'GET', // *GET, POST, PUT, DELETE, etc.
                        mode: 'cors', // no-cors, *cors, same-origin
                        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
                        credentials: 'omit', // include, *same-origin, omit
                        headers: {'Content-Type': 'application/json'},
                };
                var xhr = new XMLHttpRequest();
                xhr.open("GET", auth_url);

                xhr.onreadystatechange = function () {
                if (xhr.readyState === 4 && xhr.status == 200) {
                    console.log(xhr.status);
                    console.log(xhr.responseText);
                }};

                xhr.send();
            });
        </script>
        
    </form>
    <br>
</section>

<section id="register" style="display:block;">
<!-- Registration form for Minesweeper game, set display to false after successful login-->
    <form method="POST">
        <h2>Register</h2>
        <label for="user">Username / Nombre de Usario:</label><br>
        <input type="text" id="rg_usr" name="user" value=""><br>
        <label for="pass">Password / Clave:</label><br>
        <input type="text" id="rg_pwd" name="pass" value=""><br><br>
        <button id ="registration_submit">SUBMIT/ENVIAR</button>
        <script>
                $("#registration_submit").click(function() {
                    let usr = document.getElementById("usr_login").value;
                    let pwd = document.getElementById("pwd_login").value;
                    let auth_url = "frost.nighthawkcodescrums.gq/api/auth/" + usr + "/" + pwd + "/register";
                    const headers = {
                        method: 'GET', // *GET, POST, PUT, DELETE, etc.
                        mode: 'cors', // no-cors, *cors, same-origin
                        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
                        credentials: 'omit', // include, *same-origin, omit
                        headers: {'Content-Type': 'application/json'},
                        };
                    fetch(url, headers)
                        .then((response) => response.json())
                        .then((result) => {console.log('Success:', result);})
                        .catch((error) => {console.error('Error:', error);});
                });
        </script>
    </form>

</section>

<!--work in progress code for communicaton between frontend and backend.-->
<!-- 
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
        let usr = document.getElementById("usr_login").value;
        let pwd = document.getElementById("pwd_login").value;
        let auth_url = "frost.nighthawkcodescrums.gq/api/auth/" + usr + "/" + pwd + "/verify";
        console.log(auth_url)
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
-->

</body>