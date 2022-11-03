---
layout: default
title: About the Creators
permalink: /about/
---

<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE-edge">
        <meta name="viewport" content="width-device-width, initial-scale=1.0">
    </head>
    <style>
        #cards {
          display: flex !important;
          flex-wrap: wrap !important;
          gap: 8px!important;  
          max-width: 916px !important;
          width: calc(100% - 20px) !important;
        }
        #cards:hover > .card::after {
          opacity: 1 !important;
        }
        .card {
          background-color: rgba(255, 255, 255, 0.1) !important;
          border-radius: 10px !important;
          cursor: pointer !important;
          display: flex !important;
          height: 260px !important;
          flex-direction: column !important;
          position: relative !important;
          width: 300px !important;  
        }
        .card:hover::before {
          opacity: 1 !important;
        }
        .card::before,
        .card::after {
          border-radius: inherit !important;
          content: "" !important;
          height: 100% !important;
          left: 0px !important;
          opacity: 0 !important;
          position: absolute !important;
          top: 0px !important;
          transition: opacity 500ms !important;
          width: 100% !important;
        }
        .card::before {
          background: radial-gradient(
            800px circle at var(--mouse-x) var(--mouse-y), 
            rgba(255, 255, 255, 0.06),
            transparent 40%
          )  !important;
          z-index: 3  !important;
        }
        .card::after {  
          background: radial-gradient(
            600px circle at var(--mouse-x) var(--mouse-y), 
            rgba(255, 255, 255, 0.4),
            transparent 40%
          )  !important;
          z-index: 1  !important;
        }
        .card > .card-content {
          background-color: var(--card-color)  !important;
          border-radius: inherit  !important;
          display: flex  !important;
          flex-direction: column  !important;
          flex-grow: 1  !important;
          inset: 1px  !important;
          padding: 10px  !important;
          position: absolute  !important;
          z-index: 2  !important;
        }
        /* -- ↓ ↓ ↓ extra card content styles ↓ ↓ ↓ -- */
        h1, h2, h3, h4, span {
          color: rgb(240, 240, 240)  !important;
          font-family: "Rubik", sans-serif  !important;
          font-weight: 400  !important;
          margin: 0px  !important;
        }
        i {  
          color: rgb(240, 240, 240)  !important;
        }
        .card-image {
          align-items: center  !important;
          display: flex  !important;
          height: 140px  !important;
          justify-content: center  !important;
          overflow: hidden  !important;
        }
        .card-image > i {
          font-size: 6em  !important;
          opacity: 0.25  !important;
        }
        .card-info-wrapper {
          align-items: center  !important;
          display: flex  !important;
          flex-grow: 1  !important;
          justify-content: flex-start  !important;
          padding: 0px 20px  !important;
        }
        .card-info {
          align-items: flex-start  !important;
          display: flex  !important;
          gap: 10px  !important;
        }
        .card-info > i {  
          font-size: 1em  !important;
          height: 20px  !important;
          line-height: 20px  !important;
        }
        .card-info-title > h3 {
          font-size: 1.1em  !important;
          line-height: 20px  !important;
        }
        .card-info-title > h4 {
          color: rgba(255, 255, 255, 0.5)  !important;
          font-size: 0.85em  !important;
          margin-top: 8px  !important;
        }
        /* -- ↓ ↓ ↓ some responsiveness ↓ ↓ ↓ -- */
        @media(max-width: 1000px) {
          body {
            align-items: flex-start  !important;  
            overflow: auto  !important;
          } 
          #cards {    
            max-width: 1000px  !important;
            padding: 10px 0px  !important;
          }
          .card {
            flex-shrink: 1  !important;
            width: calc(50% - 4px)  !important;
          }
        }
        @media(max-width: 500px) {
          .card {
            height: 180px  !important;
          }
          .card-image {
            height: 80px  !important;  
          }
          .card-image > i {
            font-size: 3em  !important;
          } 
          .card-info-wrapper {
            padding: 0px 10px  !important;
          }
          .card-info > i { 
            font-size: 0.8em  !important; 
          } 
          .card-info-title > h3 {
            font-size: 0.9em  !important;
          }        
          .card-info-title > h4 {
            font-size: 0.8em  !important;
            margin-top: 4px  !important;
          }
        }        
        @media(max-width: 1000px) {
          .card {
            width: 100%  !important;
          }
        } 
    </style>
    <body>
        <script>
            document.getElementById("cards").onmousemove = e => {
                for(const card of document.getElementsByClassName("card")) {
                    const rect = card.getBoundingClientRect(),
                        x = e.clientX - rect.left,
                        y = e.clientY - rect.top;          
                    card.style.setProperty("--mouse-x", `${x}px`);
                    card.style.setProperty("--mouse-y", `${y}px`);
            }
          };               
        </script>
        <div id="cards">
            <a id="card1" class="card"  href="https://h4seeb-cmd.github.io/turtle/" target="_blank">
              <div class="card">
                <div class="card-content">
                  <div class="card-image">
                    <i class="fa-solid fa-turtle"></i>
                  </div>
                  <div class="card-info-wrapper">
                    <div class="card-info">
                      <i class="fa-duotone fa-turtle"></i>
                      <div class="card-info-title">
                        <h3>Haseeb Beg - Frontend Developer</h3>
                        <h4>Part time Frontend Developer, full time idiot.</h4>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </a>          
            <a id="card2" class="card" href="https://tirth-thakkar.github.io/APCSP-Blog/" target="_blank">
              <div class="card">
                <div class="card-content">
                  <div class="card-image">
                    <i class="fa-duotone fa-computer"></i>
                  </div>
                  <div class="card-info-wrapper">
                    <div class="card-info">
                      <i class="fa-duotone fa-computer"></i>
                      <div class="card-info-title">
                        <h3>Tirth Thakkar - Frontend Developer</h3>
                        <h4>He tries help out ... when things work. They never do.
                        </h4>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </a>          
            <a id="card3" class="card" href="https://stg-7.github.io/FastPagesSTG/" target="_blank">
              <div class="card">
                <div class="card-content">
                  <div class="card-image">
                    <i class="fa-duotone fa-toilet"></i>
                  </div>
                  <div class="card-info-wrapper">
                    <div class="card-info">
                      <i class="fa-solid fa-toilet-paper-under"></i>
                      <div class="card-info-title">
                        <h3>Shaurya Goel - Scrum Master</h3>
                        <h4>"I'll be back" - Arnold Schwarzenegger</h4>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </a>         
            <a id="card4" class="card" href="https://chewyboba10.github.io/sushi-burrito/" target="_blank">
              <div class="card">
                <div class="card-content">
                  <div class="card-image">
                    <i class="fa-duotone fa-starship-freighter"></i>
                  </div>
                  <div class="card-info-wrapper">
                    <div class="card-info">
                      <i class="fa-duotone fa-starship-freighter"></i>
                      <div class="card-info-title">
                        <h3>Evan Aparri - Dev Ops</h3>
                        <h4>So good you don't notice, until you do.
                        </h4>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </a>
            <a id="card5" class="card" href="https://ylu-1258.github.io/YLu-Blog/" target="_blank">
              <div class="card">
                <div class="card-content">
                  <div class="card-image">
                    <i class="fa-solid fa-rectangle-terminal"></i>
                  </div>
                  <div class="card-info-wrapper">
                    <div class="card-info">
                      <i class="fa-regular fa-rectangle-terminal"></i>
                      <div class="card-info-title">
                        <h3>Alex Lu - Backend Developer</h3>
                        <h4>Coding god, probably already got an MIT scholarship. Resident API expert.</h4>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </a>          
          </div>
    </body>
</html>