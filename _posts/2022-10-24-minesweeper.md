---
layout: post
description: Click to Play
categories: [Play]
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

<section id="minesweeper" style="display:none;">
    <div id="box">
         <h2>MINESWEEPER!</h2><hr><br><br>
            <div id="field"></div>
            <br>
          <div id="lost" style="display: none;">
            <h3>You got bombed!</h3>
            <button id="new-game-button" type="button" onclick="reload()">Start Again</button>
          </div>         
    </div>
</section>
<section id="login" style="display:block;">
<!-- Login form for Minesweeper game, set display to false after successful login-->
    <form>
        <br>
        <h2>Login</h2>
        <label for="user">Username / Nombre de Usario:</label><br>
        <input type="text" id="usr_login" name="user" value=""><br>
        <label for="pass">Password / Clave:</label><br>
        <input type="password" id="pwd_login" name="pass" value=""><br><br>
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
                    let data = xhr.responseText;
                    console.log(data);
                    console.log(typeof data);
                    if (data == "true\n") {
                        document.getElementById("login").style.display = "none";
                        document.getElementById("register").style.display = "none";
                        document.getElementById("minesweeper").style.display = "block";
                    };
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
        <input type="password" id="rg_pwd" name="pass" value=""><br><br>
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
<script>
    var components = {
    num_of_rows : 12,
    num_of_cols : 24,
    num_of_bombs : 55,
    bomb : '💣',
    alive : true,
    colors : {1: 'blue', 2: 'green', 3: 'red', 4: 'purple', 5: 'maroon', 6: 'turquoise', 7: 'black', 8: 'grey'}
    }

    function startGame() {
        components.bombs = placeBombs();
        document.getElementById('field').appendChild(createTable());
    }

    function placeBombs() {
        var i, rows = [];
        
        for (i=0; i<components.num_of_bombs; i++) {
            placeSingleBomb(rows);
        }
        return rows;
    } 

    function placeSingleBomb(bombs) {

        var nrow, ncol, row, col;
        nrow = Math.floor(Math.random() * components.num_of_rows);
        ncol = Math.floor(Math.random() * components.num_of_cols);
        row = bombs[nrow];
        
        if (!row) {
            row = [];
            bombs[nrow] = row;
        }
        
        col = row[ncol];
        
        if (!col) {
            row[ncol] = true;
            return
        } 
        else {
            placeSingleBomb(bombs);
        }
    }

    function cellID(i, j) {
        return 'cell-' + i + '-' + j;
    }

    function createTable() {
        var table, row, td, i, j;
        table = document.createElement('table');
        
        for (i=0; i<components.num_of_rows; i++) {
            row = document.createElement('tr');
            for (j=0; j<components.num_of_cols; j++) {
                td = document.createElement('td');
                td.id = cellID(i, j);
                row.appendChild(td);
                addCellListeners(td, i, j);
            }
            table.appendChild(row);
        }
        return table;
    }

    function addCellListeners(td, i, j) {
        td.addEventListener('mousedown', function(event) {
            if (!components.alive) {
                return;
            }
            components.mousewhiches += event.which;
            if (event.which === 3) {
                return;
            }
            if (this.flagged) {
                return;
            }
            this.style.backgroundColor = 'lightGrey';
        });

        td.addEventListener('mouseup', function(event) {
        
            if (!components.alive) {
                return;
            }

            if (this.clicked && components.mousewhiches == 4) {
                performMassClick(this, i, j);
            }

            components.mousewhiches = 0;
            
            if (event.which === 3) {
            
                if (this.clicked) {
                    return;
                }
                if (this.flagged) {
                    this.flagged = false;
                    this.textContent = '';
                } else {
                    this.flagged = true;
                    this.textContent = components.flag;
                }

                event.preventDefault();
                event.stopPropagation();
            
                return false;
            } 
            else {
                handleCellClick(this, i, j);
            }
        });

        td.oncontextmenu = function() { 
            return false; 
        };
    }

    function handleCellClick(cell, i, j) {
        if (!components.alive) {
            return;
        }

        if (cell.flagged) {
            return;
        }

        cell.clicked = true;

        if (components.bombs[i][j]) {
            cell.style.color = 'red';
            cell.textContent = components.bomb;
            gameOver();
            
        }
        else {
            cell.style.backgroundColor = 'lightGrey';
            num_of_bombs = adjacentBombs(i, j);
            if (num_of_bombs) {
                cell.style.color = components.colors[num_of_bombs];
                cell.textContent = num_of_bombs;
            } 
            else {
                clickAdjacentBombs(i, j);
            }
        }
    }

    function adjacentBombs(row, col) {
        var i, j, num_of_bombs;
        num_of_bombs = 0;

        for (i=-1; i<2; i++) {
            for (j=-1; j<2; j++) {
                if (components.bombs[row + i] && components.bombs[row + i][col + j]) {
                    num_of_bombs++;
                }
            }
        }
        return num_of_bombs;
    }

    function adjacentFlags(row, col) {
        var i, j, num_flags;
        num_flags = 0;

        for (i=-1; i<2; i++) {
            for (j=-1; j<2; j++) {
                cell = document.getElementById(cellID(row + i, col + j));
                if (!!cell && cell.flagged) {
                    num_flags++;
                }
            }
        }
        return num_flags;
    }

    function clickAdjacentBombs(row, col) {
        var i, j, cell;
        
        for (i=-1; i<2; i++) {
            for (j=-1; j<2; j++) {
                if (i === 0 && j === 0) {
                    continue;
                }
                cell = document.getElementById(cellID(row + i, col + j));
                if (!!cell && !cell.clicked && !cell.flagged) {
                    handleCellClick(cell, row + i, col + j);
                }
            }
        }
    }

    function performMassClick(cell, row, col) {
        if (adjacentFlags(row, col) === adjacentBombs(row, col)) {
            clickAdjacentBombs(row, col);
        }
    }

    function gameOver() {
        components.alive = false;
        document.getElementById('lost').style.display="block";
        
    }

    function reload(){
        window.location.reload();
    }

    window.addEventListener('load', function() {
        document.getElementById('lost').style.display="none";
        startGame();
    });
</script>

</body>