<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>A Message in the Stars ✨</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Poppins:wght@300;400;500&display=swap');

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    overflow:hidden;
    background:#03050d;
    color:white;
    font-family:'Poppins',sans-serif;
}

/* ================= SKY ================= */

.sky{
    position:fixed;
    inset:0;
    background:
        radial-gradient(circle at 50% 45%, #182348 0%, #080d20 35%, #03050d 75%);
    overflow:hidden;
}

.stars{
    position:absolute;
    inset:0;
}

.star{
    position:absolute;
    width:3px;
    height:3px;
    background:white;
    border-radius:50%;
    opacity:0;
    animation:twinkle 3s infinite ease-in-out;
}

@keyframes twinkle{
    0%,100%{
        opacity:.15;
        transform:scale(.7);
    }
    50%{
        opacity:1;
        transform:scale(1.4);
    }
}

/* moon */

.moon{
    position:absolute;
    width:120px;
    height:120px;
    border-radius:50%;
    top:9%;
    right:12%;
    background:#fff;
    box-shadow:
        0 0 30px rgba(255,255,255,.5),
        0 0 80px rgba(180,200,255,.25);
}

.moon:after{
    content:"";
    position:absolute;
    width:120px;
    height:120px;
    border-radius:50%;
    left:35px;
    top:-10px;
    background:#090d20;
}

/* ================= INTRO ================= */

.intro{
    position:relative;
    z-index:5;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    text-align:center;
    transition:1.5s ease;
}

.intro.hide{
    opacity:0;
    transform:scale(1.15);
    pointer-events:none;
}

.intro-content{
    max-width:700px;
    padding:30px;
}

.small{
    letter-spacing:5px;
    text-transform:uppercase;
    color:#9caee8;
    font-size:12px;
    margin-bottom:25px;
}

.intro h1{
    font-family:'Cormorant Garamond',serif;
    font-size:clamp(48px,8vw,90px);
    font-weight:500;
    line-height:.95;
    margin-bottom:25px;
}

.intro p{
    color:#b8c0d8;
    font-size:15px;
    line-height:1.8;
}

.begin{
    margin-top:35px;
    padding:15px 35px;
    border:1px solid rgba(255,255,255,.3);
    border-radius:50px;
    background:rgba(255,255,255,.05);
    color:white;
    cursor:pointer;
    font-family:'Poppins',sans-serif;
    letter-spacing:2px;
    transition:.4s;
}

.begin:hover{
    background:white;
    color:#080b18;
    box-shadow:0 0 35px rgba(255,255,255,.35);
    transform:translateY(-3px);
}

/* ================= CONSTELLATION ================= */

.constellation{
    position:absolute;
    z-index:4;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    opacity:0;
    pointer-events:none;
    transition:1.5s ease;
}

.constellation.show{
    opacity:1;
}

.constellation svg{
    position:absolute;
    width:min(600px,80vw);
    height:500px;
}

.line{
    stroke:rgba(190,210,255,.5);
    stroke-width:1;
    stroke-dasharray:1000;
    stroke-dashoffset:1000;
}

.constellation.show .line{
    animation:draw 3s forwards 1s;
}

@keyframes draw{
    to{
        stroke-dashoffset:0;
    }
}

.constellation-star{
    fill:white;
    filter:drop-shadow(0 0 8px white);
    opacity:0;
}

.constellation.show .constellation-star{
    animation:starAppear 1s forwards;
}

@keyframes starAppear{
    to{
        opacity:1;
    }
}

.constellation-title{
    position:absolute;
    top:13%;
    text-align:center;
    letter-spacing:4px;
    color:#aebff7;
    font-size:12px;
    text-transform:uppercase;
}

/* ================= MESSAGE ================= */

.message{
    position:absolute;
    z-index:10;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    opacity:0;
    pointer-events:none;
    transition:1.5s ease;
}

.message.show{
    opacity:1;
    pointer-events:auto;
}

.card{
    width:min(650px,90%);
    padding:55px 45px;
    text-align:center;

    background:rgba(255,255,255,.07);
    border:1px solid rgba(255,255,255,.16);
    border-radius:30px;

    backdrop-filter:blur(18px);
    box-shadow:
        0 30px 100px rgba(0,0,0,.5),
        inset 0 1px rgba(255,255,255,.15);

    animation:cardIn 1.5s ease;
}

@keyframes cardIn{
    from{
        opacity:0;
        transform:translateY(40px) scale(.9);
    }
    to{
        opacity:1;
        transform:none;
    }
}

.flower{
    font-size:42px;
    margin-bottom:15px;
}

.card .tiny{
    color:#aab9e8;
    letter-spacing:4px;
    font-size:11px;
    text-transform:uppercase;
}

.card h2{
    font-family:'Cormorant Garamond',serif;
    font-size:clamp(45px,7vw,70px);
    font-weight:600;
    margin:12px 0 20px;

    background:linear-gradient(90deg,#fff,#cbd8ff,#fff);
    -webkit-background-clip:text;
    color:transparent;
}

.card p{
    color:#d1d6e5;
    line-height:2;
    font-size:15px;
}

.quote{
    margin-top:25px;
    font-family:'Cormorant Garamond',serif;
    font-size:25px;
    color:#fff;
}

.signature{
    margin-top:30px;
    color:#aebff7;
    font-size:13px;
    letter-spacing:2px;
}

/* ================= PETALS ================= */

.petal{
    position:absolute;
    top:-30px;
    z-index:12;
    font-size:20px;
    animation:fall linear forwards;
}

@keyframes fall{
    0%{
        transform:translateY(-30px) rotate(0);
        opacity:0;
    }

    15%{
        opacity:1;
    }

    100%{
        transform:translateY(110vh) rotate(360deg);
        opacity:0;
    }
}

/* ================= RESPONSIVE ================= */

@media(max-width:600px){

    .moon{
        width:75px;
        height:75px;
        right:8%;
    }

    .moon:after{
        width:75px;
        height:75px;
        left:22px;
    }

    .card{
        padding:40px 25px;
    }

    .card p{
        font-size:14px;
    }
}
</style>
</head>

<body>

<div class="sky">

    <div class="stars" id="stars"></div>

    <div class="moon"></div>


    <!-- INTRO -->

    <section class="intro" id="intro">

        <div class="intro-content">

            <div class="small">
                A little surprise
            </div>

            <h1>
                Some people<br>
                leave a light behind.
            </h1>

            <p>
                Not every light comes from the stars.<br>
                Some come from the people who teach us<br>
                how to find our own way.
            </p>

            <button class="begin" onclick="beginSurprise()">
                ✦ FIND THE LIGHT
            </button>

        </div>

    </section>


    <!-- CONSTELLATION -->

    <section class="constellation" id="constellation">

        <div class="constellation-title">
            Connecting the stars...
        </div>

        <svg viewBox="0 0 600 500">

            <!-- constellation lines -->

            <line class="line"
                x1="130" y1="260"
                x2="200" y2="160"/>

            <line class="line"
                x1="200" y1="160"
                x2="300" y2="220"/>

            <line class="line"
                x1="300" y1="220"
                x2="390" y2="120"/>

            <line class="line"
                x1="390" y1="120"
                x2="470" y2="250"/>

            <line class="line"
                x1="470" y1="250"
                x2="350" y2="350"/>

            <line class="line"
                x1="350" y1="350"
                x2="200" y2="360"/>

            <line class="line"
                x1="200" y1="360"
                x2="130" y2="260"/>


            <!-- stars -->

            <circle class="constellation-star"
                cx="130" cy="260" r="5"
                style="animation-delay:.3s"/>

            <circle class="constellation-star"
                cx="200" cy="160" r="6"
                style="animation-delay:.6s"/>

            <circle class="constellation-star"
                cx="300" cy="220" r="7"
                style="animation-delay:.9s"/>

            <circle class="constellation-star"
                cx="390" cy="120" r="6"
                style="animation-delay:1.2s"/>

            <circle class="constellation-star"
                cx="470" cy="250" r="5"
                style="animation-delay:1.5s"/>

            <circle class="constellation-star"
                cx="350" cy="350" r="6"
                style="animation-delay:1.8s"/>

            <circle class="constellation-star"
                cx="200" cy="360" r="5"
                style="animation-delay:2.1s"/>

        </svg>

    </section>


    <!-- FINAL MESSAGE -->

    <section class="message" id="message">

        <div class="card">

            <div class="flower">
                🌷
            </div>

            <div class="tiny">
                For someone special
            </div>

            <!-- CHANGE TEACHER NAME HERE -->

            <h2>
                Dear Ma'am
            </h2>

            <p>
                A good teacher explains.<br>
                A great teacher inspires.
            </p>

            <div class="quote">
                “You didn't just teach us lessons,<br>
                you became part of our journey.”
            </div>

            <div class="signature">
                WITH GRATITUDE · WITH RESPECT · WITH LOVE
            </div>

            <div style="
                margin-top:25px;
                font-family:'Cormorant Garamond',serif;
                font-size:28px;
                color:#fff;
            ">
                Happy Teachers' Day ✨
            </div>

        </div>

    </section>

</div>


<script>

/* ================= CREATE STARS ================= */

const stars = document.getElementById("stars");

for(let i=0;i<120;i++){

    const star = document.createElement("div");

    star.className="star";

    star.style.left=Math.random()*100+"%";
    star.style.top=Math.random()*100+"%";

    star.style.animationDelay=
        Math.random()*4+"s";

    star.style.animationDuration=
        (2+Math.random()*4)+"s";

    stars.appendChild(star);
}


/* ================= START ================= */

function beginSurprise(){

    const intro =
        document.getElementById("intro");

    const constellation =
        document.getElementById("constellation");

    const message =
        document.getElementById("message");


    intro.classList.add("hide");

    setTimeout(()=>{

        constellation.classList.add("show");

    },800);


    /* reveal final message */

    setTimeout(()=>{

        constellation.style.opacity="0";

        setTimeout(()=>{

            message.classList.add("show");

            createPetals();

        },800);

    },5200);

}


/* ================= PETALS ================= */

function createPetals(){

    const symbols=[
        "🌸",
        "🌷",
        "✦",
        "✨",
        "🤍"
    ];

    setInterval(()=>{

        const petal =
            document.createElement("div");

        petal.className="petal";

        petal.innerHTML =
            symbols[
                Math.floor(
                    Math.random()*symbols.length
                )
            ];

        petal.style.left =
            Math.random()*100+"%";

        petal.style.animationDuration =
            (5+Math.random()*5)+"s";

        petal.style.fontSize =
            (12+Math.random()*15)+"px";

        document.body.appendChild(petal);

        setTimeout(()=>{
            petal.remove();
        },10000);

    },500);

}

</script>

</body>
</html>
