
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday RAM!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* --- GLOBAL STYLES & BACKGROUND --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: radial-gradient(circle at center, #2d124d 0%, #0c0414 100%);
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            padding: 20px;
            position: relative;
        }

/* HEART CURSOR */  
    .heart{  
      position:fixed;  
      color:red;  
      pointer-events:none;  
      animation:floatHeart 1s linear forwards;  
      z-index:999;  
    }  

        /* Ambient Background Glows to match the image atmosphere */
        body::before, body::after {
            content: '';
            position: absolute;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            background: rgba(255, 0, 128, 0.15);
            filter: blur(80px);
            z-index: 0;
        }
        body::before { top: 10%; left: 10%; }
        body::after { bottom: 10%; right: 10%; }

        /* --- REUSABLE GLASSMORPHISM CONTAINER --- */
        .page {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 24px;
            padding: 40px 30px;
            width: 100%;
            max-width: 700px;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
            text-align: center;
            z-index: 1;
            display: none; /* Hidden by default, toggled via JS */
            animation: fadeIn 0.5s ease-in-out forwards;
        }

        .page.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- BUTTON STYLING --- */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            background: linear-gradient(90deg, #ff5e62, #ff9966);
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 16px;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 4px 15px rgba(255, 94, 98, 0.4);
            margin-top: 25px;
            text-decoration: none;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 94, 98, 0.6);
        }

        .div:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 94, 98, 0.6);
        }

        /* --- PAGE 1: HOME --- */
        .birthday-title {
            font-family: 'Dancing Script', cursive;
            font-size: 3.5rem;
            margin-bottom: 10px;
            color: #ffffff;
        }

        .birthday-title span {
            color: #ffd700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        .subtitle {
            font-size: 14px;
            color: #ddccff;
            margin-bottom: 30px;
            font-weight: 300;
        }

        /* Countdown Grid */
        .countdown-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin: 20px 0;
        }

        .countdown-box {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 15px 5px;
        }

        .countdown-box .number {
            font-size: 2rem;
            font-weight: 700;
            color: #ffd700;
            display: block;
        }

        .countdown-box .label {
            font-size: 12px;
            color: #b3a0cc;
            text-transform: capitalize;
        }

        /* --- PAGE 2: FRIENDSHIP JOURNEY --- */
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .three-column-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }

        .journey-card {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 16px;
            padding: 20px 12px;
            font-size: 13px;
            line-height: 1.6;
            color: #e0d5f0;
        }

        /* Distinct border tints for Page 2 cards as seen in image */
        .card-purple { border: 1px solid rgba(157, 78, 221, 0.4); }
        .card-blue { border: 1px solid rgba(0, 180, 216, 0.4); }
        .card-magenta { border: 1px solid rgba(255, 0, 127, 0.4); }

        .journey-card .icon {
            font-size: 24px;
            margin-bottom: 10px;
            display: block;
        }

        .journey-card h4 {
            font-size: 15px;
            color: #fff;
            margin-bottom: 10px;
            font-weight: 600;
        }

        /* --- PAGE 3: DETAILED MESSAGE --- */
        .letter-content {
            font-size: 14px;
            line-height: 1.8;
            color: #e6def2;
            text-align: center;
            max-width: 550px;
            margin: 0 auto;
        }

        .letter-content p {
            margin-bottom: 15px;
        }

        .highlight-quote {
            font-family: 'Dancing Script', cursive;
            font-size: 1.8rem;
            color: #ffd700;
            margin: 25px 0;
            text-shadow: 0 0 8px rgba(255, 215, 0, 0.3);
        }

        /* --- PAGE 4: WORLDWIDE WISHES --- */
        .languages-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }

        .languages-grid {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 94, 98, 0.6);
        }
.countdown-box,
.journey-card,
.lang-box,
.final-message{
    transition: all 0.3s ease;
}

.countdown-box:hover,
.journey-card:hover,
.lang-box:hover,
.final-message:hover{
    transform: translateY(-5px) scale(1.02);
    box-shadow: 0 8px 25px rgba(255, 94, 98, 0.5);
}
        /* Custom border colors matching the language boxes */
        .lang-box {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 12px;
            padding: 15px 10px;
            font-size: 11px;
            line-height: 1.5;
            text-align: left;
        }
        .lang-box h4 { 
            text-align: center; 
            margin-bottom: 8px; 
            font-size: 13px;
        }
        .border-teal { border: 1px solid #00a896; }
        .border-orange { border: 1px solid #f77f00; }
        .border-purple { border: 1px solid #7209b7; }
        .border-blue { border: 1px solid #4361ee; }
        .border-pink { border: 1px solid #f72585; }

        /* Final Heart Box Container */
        .final-box {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(114, 9, 183, 0.5);
            border-radius: 16px;
            padding: 20px;
            font-size: 12px;
            line-height: 1.6;
            color: #dcd1ec;
            margin-top: 15px;
        }

        .final-box h4 {
            font-size: 14px;
            color: #fff;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        .forever-footer {
            margin-top: 15px;
            font-weight: 600;
            color: #ff5e62;
            font-size: 14px;
        }

        /* Responsive design adjustments */
        @media (max-width: 650px) {
            .three-column-grid, .languages-grid {
                grid-template-columns: 1fr;
            }
            .countdown-container {
                grid-template-columns: repeat(2, 1fr);
            }
            .birthday-title { font-size: 2.5rem; }
        }
    </style>
</head>
<body>

    <div id="page1" class="page active">
        <h1 class="birthday-title">Happy Birthday <span>RAM</span> 🎂❤️</h1>
        <p class="subtitle">Thank you for being the most amazing person in my life ❤️<br>This small website is made only for YOU ✨</p>
        
        <div class="countdown-container">
            <div class="countdown-box"><span class="number" id="days">00</span><span class="label">Days</span></div>
            <div class="countdown-box"><span class="number" id="hours">00</span><span class="label">Hours</span></div>
            <div class="countdown-box"><span class="number" id="minutes">00</span><span class="label">Minutes</span></div>
            <div class="countdown-box"><span class="number" id="seconds">00</span><span class="label">Seconds</span></div>
        </div>

        <button class="btn" onclick="navigateTo('page2')">💌 Secret Message</button>
    </div>

    <div id="page2" class="page">
        <h2 class="section-title">📖 Our Friendship Journey</h2>
        
        <div class="three-column-grid">
            <div class="journey-card card-purple">
                <span class="icon">😂</span>
                <h4>Endless Laughs</h4>
                <p>Every joke, every random conversation and every silly moment with you becomes a memory worth keeping forever.</p>
            </div>
            <div class="journey-card card-blue">
                <span class="icon">🤝</span>
                <h4>True Support</h4>
                <p>You stood beside me through good days and difficult days. Your support means more than words can express.</p>
            </div>
            <div class="journey-card card-magenta">
                <span class="icon">✨</span>
                <h4>Golden Memories</h4>
                <p>Every photo, every trip and every chat has become a treasure because we shared it together.</p>
            </div>
        </div>

        <button class="btn" onclick="navigateTo('page3')">Forever Best Friends ✨</button>
    </div>

    <div id="page3" class="page">
        <h2 class="section-title">💌 Message From Your Best Friend</h2>
        
        <div class="letter-content">
            <p><strong>Happy Birthday To The Most Amazing Person Ever ❤️</strong></p>
            <p>I seriously feel lucky to have someone like you in my life 🌍✨</p>
            <p>Thank you for every laugh 😂, every memory 📸, every late night talk 🌙, every moment of support 🤝 and every smile you gave me 💕</p>
            <p>You are not just my best friend... you are my comfort person, my happiness, and one of the best parts of my life ❤️</p>
            <p>I hope this birthday brings: endless happiness 🌸, success 📈, peace 🌙, love 💕, good health 🌿 and every dream you wish for ✨</p>
            <p>Never change yourself because you are truly special 🌟</p>
            
            <div class="highlight-quote">“No matter what happens, I'll always be there for you ❤️”</div>
            
            <p>Happy Birthday Once Again 🎂✨</p>
        </div>

        <button class="btn" onclick="navigateTo('page4')">Your Special Gift 🎁</button>
    </div>

    <div id="page4" class="page">
        <h2 class="section-title">🌍 Birthday Wishes Around The World</h2>
        
        <div class="languages-grid">
            <div class="lang-box border-teal">
                <h4>English</h4>
                <p>Happy Birthday to the person who makes my life brighter just by being in it. You are more than a best friend – you are my safe place, my happiness, and the reason behind so many unforgettable memories.</p>
            </div>
            <div class="lang-box border-orange">
                <h4>Marathi</h4>
                <p>माझ्या आयुष्यातील सर्वात मौल्यवान, खास आणि अमूल्य मित्राला वाढदिवसाच्या मनःपूर्वक शुभेच्छा! तुझ्यासारखा मित्र मिळणे हे खरेच नशिबाचे काम आहे. देव करो तुझ्या आयुष्यात नेहमी आनंद, प्रेम, यश आणि समाधान भरलेले असो.</p>
            </div>
            <div class="lang-box border-purple">
                <h4>Sanskrit</h4>
                <p>प्रिय मित्र, जन्मदिवसस्य असङ्ख्याः शुभकामनाः! ईश्वरः त्वां सर्वदा सुखिनं, स्वस्थं, यशस्विनं, तेजस्विनं च करोतु। तव जीवनं प्रेम्णा, शान्त्या, समृद्ध्या, सौभाग्येन च परिपूर्णं भवतु। सर्वे मनोरथाः सिद्धिं गच्छन्तु।</p>
            </div>
        </div>

        <div class="languages-grid" style="grid-template-columns: repeat(2, 1fr); max-width: 500px; margin: 0 auto 20px;">
            <div class="lang-box border-blue">
                <h4>Korean</h4>
                <p>세상에서 가장 소중한 내 친구야, 생일 정말 축하해! 너는 내 삶에 행복과 웃음을 가져다주는 특별한 사람이야. 앞으로도 우리의 우정이 지금처럼 오래오래 계속되면 좋겠어!</p>
            </div>
            <div class="lang-box border-pink">
                <h4>French</h4>
                <p>Joyeux anniversaire à mon incroyable meilleur ami ! Tu es l'une des personnes les plus précieuses de ma vie. Je te souhaite une année remplie de bonheur, d'amour, de succès et d'aventures incroyables. 🎂💖</p>
            </div>
        </div>

       <div class="final-message" align="center">

    <h2>❤️ A Final Message From My Heart ❤️</h2>

    <p>
        Different languages may have different words,
        different scripts, and different ways of expressing emotions,
        but today they all share the same meaning —
        you are someone truly special.
    </p>

    <p>
        Thank you for every laugh we shared,
        every memory we created,
        every challenge we faced together,
        and every moment that strengthened our friendship.
    </p>

    <p>
        You have been a source of happiness,
        support, comfort, and inspiration in my life,
        and I am incredibly grateful for every moment we've spent together.
    </p>

    <p>
        May this birthday bring you endless happiness,
        great success, good health,
        beautiful adventures, and countless reasons to smile.
    </p>

    <p>
        May all your dreams come true,
        may every goal become reality,
        and may your life always be filled with love,
        peace, and joy.
    </p>

    <p>
        No matter where life takes us,
        our friendship will always remain one of the most precious parts of my life.
    </p>

    <h3>🎂 Happy Birthday Once Again! 🎂</h3>

    <h2 class="forever">❤️ Forever Best Friends ❤️</h2>

    <h4>♾️ Today • Tomorrow • Always ♾️</h4>

</div>
    </div>

    <script>
        // Simple and robust Routing Function
        function navigateTo(pageId) {
            // Find all elements with class 'page' and remove 'active'
            const pages = document.querySelectorAll('.page');
            pages.forEach(page => {
                page.classList.remove('active');
            });

            // Add 'active' class to the targeted container ID
            const targetPage = document.getElementById(pageId);
            if (targetPage) {
                targetPage.classList.add('active');
                // Auto scroll smoothly to top when layout switches
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }
        }

       const birthdayDate =
new Date("June 7, 2026 00:00:00").getTime();

setInterval(()=>{

const now = new Date().getTime();

const gap = birthdayDate - now;

document.getElementById("days").innerHTML =
Math.floor(gap/(1000*60*60*24));

document.getElementById("hours").innerHTML =
Math.floor((gap%(1000*60*60*24))/(1000*60*60));

document.getElementById("minutes").innerHTML =
Math.floor((gap%(1000*60*60))/(1000*60));

document.getElementById("seconds").innerHTML =
Math.floor((gap%(1000*60))/1000);

},1000);
    </script>
</body>
</html>
