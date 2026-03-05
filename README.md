<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ERAT Practice Quiz</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&amp;display=swap" rel="stylesheet">
  <style>
    * { font-family: 'Poppins', sans-serif; }
    body { margin: 0; padding: 0; }
    .subject-card { transition: all 0.3s ease; }
    .subject-card:hover { transform: translateY(-8px); }
    .option-btn { transition: all 0.2s ease; cursor: pointer; }
    .option-btn:hover { transform: translateX(5px); }
    .option-btn.selected { background: linear-gradient(135deg, #6366f1, #8b5cf6); color: white; }
    .progress-bar { transition: width 0.5s ease; }
    .fade-in { animation: fadeIn 0.5s ease; }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    .timer-danger { color: #ef4444; font-weight: bold; }
    .confetti-piece { position: fixed; pointer-events: none; animation: confetti-fall 3s ease-out forwards; }
    @keyframes confetti-fall { to { transform: translateY(100vh) rotate(720deg); opacity: 0; } }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full w-full bg-gray-50 text-gray-900">
  <div id="app" class="h-full w-full flex flex-col"><!-- Login Screen -->
   <div id="login-screen" class="min-h-full w-full flex items-center justify-center p-4 bg-gray-50">
    <div class="w-full max-w-md">
     <div class="bg-white shadow-lg rounded-3xl p-8 border border-gray-200">
      <div class="text-center mb-8">
       <div class="text-4xl mb-4">
        📚
       </div>
       <h1 class="text-3xl font-bold mb-2 text-gray-900">ERAT Quiz</h1>
       <p class="text-gray-600 text-sm">School Year 2025-2026</p>
      </div>
      <form id="login-form" onsubmit="handleLogin(event);" class="space-y-4">
       <div><label class="block text-sm font-medium mb-2 text-gray-700">Full Name</label> <input id="full-name" type="text" placeholder="Enter your name" required class="w-full px-4 py-2 rounded-lg bg-white border border-gray-300 text-gray-900 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label class="block text-sm font-medium mb-2 text-gray-700">Student Code</label> <input id="student-code" type="text" placeholder="Enter code" required class="w-full px-4 py-2 rounded-lg bg-white border border-gray-300 text-gray-900 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div><button type="submit" class="w-full py-3 rounded-lg bg-blue-600 hover:bg-blue-700 text-white font-semibold">Start Quiz →</button>
      </form>
     </div>
    </div>
   </div><!-- Home Screen -->
   <div id="home-screen" class="hidden min-h-full w-full p-6 md:p-10 overflow-auto">
    <div class="max-w-7xl mx-auto">
     <header class="text-center mb-12">
      <div class="text-4xl mb-4">
       📚
      </div>
      <h1 id="main-title" class="text-4xl md:text-5xl font-bold mb-2 text-gray-900">Enhanced Regional Achievement Test</h1>
      <p id="school-year-display" class="text-gray-600 mt-2">School Year 2025-2026</p>
     </header>
     <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-12"><button onclick="startQuiz('math');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🔢
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">Mathematics</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('english');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        📖
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">English</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('epp');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🔧
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">EPP/TLE</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('mapeh');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🎨
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">MAPEH</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('science');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🔬
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">Science</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('filipino');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🇵🇭
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">Filipino</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('ap');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        🌏
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">Araling Panlipunan</h3><p class="text-sm text-gray-600">20 Questions • 30 min</p></button> <button onclick="startQuiz('values');" class="subject-card bg-white border border-gray-200 shadow hover:shadow-lg rounded-2xl p-6 text-left hover:border-blue-300">
       <div class="text-4xl mb-3">
        💝
       </div><h3 class="text-lg font-bold mb-1 text-gray-900">Values Education</h3><p class="text-sm text-gray-600">40 Questions • 60 min</p></button>
     </div>
    </div>
   </div><!-- Quiz Screen -->
   <div id="quiz-screen" class="hidden min-h-full w-full p-4 md:p-8 overflow-auto">
    <div class="flex gap-6 max-w-7xl mx-auto">
     <div class="flex-1">
      <div class="bg-white border border-gray-200 rounded-2xl p-4 md:p-6 mb-6 shadow">
       <div class="flex justify-between items-center mb-4">
        <div>
         <h2 id="quiz-title" class="text-2xl font-bold text-gray-900">Mathematics</h2>
         <p class="text-gray-600 text-sm">Question <span id="q-num">1</span> / <span id="q-total">20</span></p>
        </div>
        <div id="timer" class="text-3xl font-mono font-bold bg-blue-600 text-white px-6 py-2 rounded-lg">
         30:00
        </div>
       </div>
       <div class="w-full h-2 bg-gray-200 rounded-full overflow-hidden">
        <div id="progress" class="progress-bar h-full bg-blue-600"></div>
       </div>
      </div>
      <div class="bg-white border border-gray-200 rounded-2xl p-6 md:p-8 fade-in shadow">
       <p id="question" class="text-lg md:text-xl font-medium mb-8 text-gray-900">Loading...</p>
       <div id="options" class="space-y-3 mb-8"></div>
       <div class="flex justify-between pt-6 border-t border-gray-200"><button id="prev-btn" onclick="prevQ();" class="px-6 py-3 rounded-lg bg-gray-300 hover:bg-gray-400 text-gray-900 font-medium disabled:opacity-50">← Previous</button> <button id="next-btn" onclick="nextQ();" class="px-6 py-3 rounded-lg bg-blue-600 hover:bg-blue-700 text-white font-medium">Next →</button> <button id="submit-btn" onclick="submitQ();" class="hidden px-6 py-3 rounded-lg bg-green-600 hover:bg-green-700 text-white font-medium">Submit Quiz ✓</button>
       </div>
      </div>
     </div>
     <div class="hidden lg:block w-80">
      <div class="bg-white border border-gray-200 rounded-2xl p-4 shadow sticky top-4 max-h-screen overflow-y-auto">
       <h3 class="font-bold text-gray-900 mb-4 text-sm">📊 PROGRESS</h3>
       <div id="summary-content" class="space-y-3 text-sm mb-4">
       </div>
       <div class="border-t border-gray-200 pt-4 mt-4">
        <h4 class="font-bold text-gray-900 mb-3 text-xs">📚 ALL SUBJECTS</h4>
        <div id="all-subjects-summary" class="space-y-2 text-xs">
        </div>
       </div>
       <div class="border-t border-gray-200 pt-4 mt-4 bg-blue-50 rounded-lg p-3">
        <p class="text-xs text-gray-600 mb-1">Overall Score</p>
        <div class="flex items-baseline gap-2">
         <span id="overall-score" class="text-2xl font-bold text-blue-600">0</span> <span id="overall-total" class="text-sm text-gray-600">/ 0</span>
        </div>
        <p id="overall-percentage" class="text-xs text-gray-600 mt-1">0% Complete</p>
       </div>
      </div>
     </div>
    </div>
   </div><!-- Results Screen -->
   <div id="results-screen" class="hidden min-h-full w-full p-4 md:p-8 overflow-auto flex items-center justify-center bg-gray-50">
    <div class="max-w-2xl w-full">
     <div class="bg-white border border-gray-200 rounded-3xl p-8 text-center shadow-lg">
      <div id="result-icon" class="text-6xl mb-4">
       🎉
      </div>
      <h2 class="text-3xl font-bold mb-2 text-gray-900">Quiz Complete!</h2>
      <p id="result-subject" class="text-gray-600 mb-8">Mathematics</p>
      <div class="bg-gray-50 rounded-2xl p-6 mb-8 border border-gray-200">
       <div class="text-5xl font-bold text-green-600 mb-2">
        <span id="score">0</span>/<span id="total">20</span>
       </div>
       <p class="text-gray-600">Correct Answers</p>
       <div id="percent" class="text-3xl font-bold mt-2 text-gray-900">
        0%
       </div>
      </div>
      <div class="grid grid-cols-3 gap-4 mb-8">
       <div class="bg-green-50 rounded-xl p-4 border border-green-200">
        <div class="text-2xl font-bold text-green-600" id="correct">
         0
        </div>
        <p class="text-sm text-gray-600">Correct</p>
       </div>
       <div class="bg-red-50 rounded-xl p-4 border border-red-200">
        <div class="text-2xl font-bold text-red-600" id="wrong">
         0
        </div>
        <p class="text-sm text-gray-600">Wrong</p>
       </div>
       <div class="bg-amber-50 rounded-xl p-4 border border-amber-200">
        <div class="text-2xl font-bold text-amber-600" id="skipped">
         0
        </div>
        <p class="text-sm text-gray-600">Skipped</p>
       </div>
      </div>
      <div class="bg-gray-50 border border-gray-200 rounded-xl p-4 mb-8">
       <p class="text-sm font-medium mb-2 text-gray-700">📊 Performance Summary</p>
       <p id="performance-text" class="text-lg font-semibold text-gray-900"></p>
      </div>
      <div class="flex flex-col sm:flex-row gap-3 justify-center flex-wrap"><button onclick="goHome();" class="px-6 py-3 rounded-lg bg-green-600 hover:bg-green-700 text-white font-medium">🏠 Home</button> <button onclick="retryQ();" class="px-6 py-3 rounded-lg bg-blue-600 hover:bg-blue-700 text-white font-medium">🔄 Retry</button> <button id="review-btn" onclick="reviewAnswers();" class="px-6 py-3 rounded-lg bg-cyan-600 hover:bg-cyan-700 text-white font-medium">👁️ Review Answers</button> <button id="next-subject-btn" onclick="nextSubject();" class="px-6 py-3 rounded-lg bg-purple-600 hover:bg-purple-700 text-white font-medium">⏭️ Next Subject</button>
      </div>
     </div>
    </div>
   </div><!-- Review Modal -->
   <div id="review-modal" class="hidden fixed inset-0 bg-black/40 backdrop-blur flex items-center justify-center p-4 z-50">
    <div class="bg-white border border-gray-200 rounded-2xl max-w-2xl w-full max-h-96 overflow-y-auto shadow-xl">
     <div class="p-6 border-b border-gray-200 sticky top-0 bg-white">
      <div class="flex justify-between items-center">
       <h3 class="text-xl font-bold text-gray-900">👁️ Review Your Answers</h3><button onclick="closeReview();" class="text-gray-400 hover:text-gray-600 text-2xl">×</button>
      </div>
     </div>
     <div id="review-content" class="p-6 space-y-4 text-gray-900">
      <!-- Populated by JavaScript -->
     </div>
    </div>
   </div><!-- Submit to Teacher Modal -->
   <div id="submit-modal" class="hidden fixed inset-0 bg-black/40 backdrop-blur flex items-center justify-center p-4 z-50">
    <div class="bg-white border border-gray-200 rounded-2xl max-w-md w-full shadow-xl">
     <div class="p-6 border-b border-gray-200">
      <h3 class="text-xl font-bold text-gray-900">📤 Submit Results to Teacher</h3>
     </div>
     <form id="submit-form" onsubmit="submitToTeacher(event);" class="p-6 space-y-4">
      <div>
       <label class="block text-sm font-medium mb-2 text-gray-700">Teacher's Email</label> <input id="teacher-email" type="email" placeholder="teacher@school.com" required class="w-full px-4 py-2 rounded-lg bg-white border border-gray-300 text-gray-900 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500">
      </div>
      <div>
       <label class="block text-sm font-medium mb-2 text-gray-700">Message (Optional)</label> <textarea id="teacher-message" placeholder="Add a message..." class="w-full px-4 py-2 rounded-lg bg-white border border-gray-300 text-gray-900 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500 h-24"></textarea>
      </div>
      <p id="submit-status" class="text-sm text-gray-600"></p>
      <div class="flex gap-3">
       <button type="button" onclick="closeSubmitForm();" class="flex-1 px-4 py-2 rounded-lg bg-gray-300 hover:bg-gray-400 text-gray-900 font-medium">Cancel</button> <button type="submit" class="flex-1 px-4 py-2 rounded-lg bg-orange-600 hover:bg-orange-700 text-white font-medium">Send ✓</button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Final Summary Screen -->
  <div id="final-summary-screen" class="hidden min-h-full w-full p-4 md:p-8 overflow-auto flex items-center justify-center bg-gray-50">
   <div class="max-w-3xl w-full">
    <div class="bg-white border border-gray-200 rounded-3xl p-8 text-center shadow-lg">
     <div class="text-6xl mb-4">
      🎓
     </div>
     <h2 class="text-3xl font-bold mb-2 text-gray-900">All Subjects Complete!</h2>
     <p class="text-gray-600 mb-8">Your Overall Performance</p>
     <div class="bg-gradient-to-r from-blue-50 to-cyan-50 rounded-2xl p-8 mb-8 border border-blue-200">
      <div class="text-6xl font-bold text-blue-600 mb-2">
       <span id="final-score">0</span>/<span id="final-total">160</span>
      </div>
      <p class="text-gray-600 mb-4">Total Correct Answers</p>
      <div class="text-4xl font-bold text-blue-600" id="final-percent">
       0%
      </div>
     </div>
     <div class="bg-gray-50 border border-gray-200 rounded-xl p-6 mb-8">
      <p class="text-sm font-medium mb-3 text-gray-700">📊 Overall Performance</p>
      <p id="final-performance" class="text-lg font-semibold text-gray-900 mb-6"></p>
      <div class="text-left">
       <p class="text-sm font-medium mb-3 text-gray-700">Subject Breakdown:</p>
       <div id="results-summary"></div>
      </div>
     </div>
     <div class="flex flex-col sm:flex-row gap-3 justify-center flex-wrap"><button onclick="goHome();" class="px-6 py-3 rounded-lg bg-green-600 hover:bg-green-700 text-white font-medium">🏠 Back to Home</button> <button id="final-submit-btn" onclick="submitAllResults();" class="px-6 py-3 rounded-lg bg-orange-600 hover:bg-orange-700 text-white font-medium">📤 Submit All Results</button>
     </div>
    </div>
   </div>
  </div><!-- Footer -->
  <footer class="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200 px-6 py-3 text-center text-sm text-gray-600">
   Developed by <span class="font-semibold text-gray-900">JOEL P. RODRIGUEZ</span> • LPT, MAVEd
  </footer>
  <script>
    // Quiz Data - Compact format
    const Q = {
      math: { n: "🔢 Mathematics", q: [
        {q:"15 × 8 = ?",o:["100","120","130","125"],a:1},
        {q:"Area of 12cm × 5cm?",o:["60 sq cm","34 sq cm","17 sq cm","70 sq cm"],a:0},
        {q:"3/4 + 1/2 = ?",o:["4/6","5/4","1/4","2/4"],a:1},
        {q:"Round 4,567 to nearest 100?",o:["4,500","4,600","4,560","5,000"],a:1},
        {q:"Next: 2, 6, 18, 54?",o:["108","162","72","216"],a:1},
        {q:"24 marbles, 1/3 red = ?",o:["6","8","12","18"],a:1},
        {q:"25% of 80 = ?",o:["15","20","25","30"],a:1},
        {q:"48 ÷ 6 × 2 = ?",o:["4","8","16","12"],a:2},
        {q:"Square perimeter, side 9cm?",o:["18 cm","27 cm","36 cm","81 cm"],a:2},
        {q:"0.75 as fraction?",o:["75/100","3/4","7/10","15/20"],a:1},
        {q:"LCM of 4 and 6?",o:["2","12","24","10"],a:1},
        {q:"x + 7 = 15, x = ?",o:["7","8","22","9"],a:1},
        {q:"Right angle = ? degrees?",o:["45°","90°","180°","360°"],a:1},
        {q:"1,000 - 456 = ?",o:["544","554","444","654"],a:0},
        {q:"Triangle angles: 60° + 80° + ?",o:["40°","50°","60°","30°"],a:0},
        {q:"GCF of 18 and 24?",o:["3","6","12","2"],a:1},
        {q:"7/8 as decimal?",o:["0.78","0.875","0.87","0.785"],a:1},
        {q:"Faces in a cube?",o:["4","6","8","12"],a:1},
        {q:"3² + 4² = ?",o:["14","25","49","12"],a:1},
        {q:"Car travels 240km in 4 hours?",o:["50 km/h","60 km/h","70 km/h","80 km/h"],a:1}
      ]},
      english: { n: "📖 English", q: [
        {q:"She ___ to school daily",o:["go","goes","going","gone"],a:1},
        {q:"Plural of 'child'?",o:["childs","childes","children","childrens"],a:2},
        {q:"Which is a noun?",o:["quickly","happiness","beautiful","run"],a:1},
        {q:"Adjective in sentence?",o:["man","walked","tall","slowly"],a:2},
        {q:"Past tense of 'begin'?",o:["begined","begun","began","beginned"],a:2},
        {q:"___ are my friends",o:["Them","They","Their","Him"],a:1},
        {q:"He doesn't like pizza",o:["don't like","doesn't likes","doesn't like","not like"],a:2},
        {q:"Synonym for 'happy'?",o:["sad","joyful","angry","tired"],a:1},
        {q:"Antonym of 'hot'?",o:["warm","cold","burning","heated"],a:1},
        {q:"Adverb in 'She sings beautifully'?",o:["She","sings","beautifully","none"],a:2},
        {q:"Punctuation for questions?",o:["Period","Comma","Question mark","Exclamation"],a:2},
        {q:"Type: 'What a beautiful day!'?",o:["Declarative","Interrogative","Imperative","Exclamatory"],a:3},
        {q:"___ apple a day",o:["A","An","The","None"],a:1},
        {q:"Spelled correctly?",o:["recieve","receive","receve","receeve"],a:1},
        {q:"Comparative of 'good'?",o:["gooder","more good","better","best"],a:2},
        {q:"Preposition: 'book on table'?",o:["book","is","on","table"],a:2},
        {q:"'The dogs run fast' is?",o:["incorrect","wrong","correct","unclear"],a:2},
        {q:"Homophone of 'write'?",o:["wrong","right","wrote","writing"],a:1},
        {q:"That is ___ book (Maria)",o:["Maria","Marias","Maria's","Marias'"],a:2},
        {q:"Which is a conjunction?",o:["under","and","quickly","she"],a:1}
      ]},
      epp: { n: "🔧 EPP/TLE", q: [
        {q:"EPP stands for?",o:["Edukasyong Pantahanan","Elementary Primary","Educational Practical","Economic Planning"],a:0},
        {q:"Tool for measuring length?",o:["Hammer","Ruler","Screwdriver","Pliers"],a:1},
        {q:"Entrepreneurship means?",o:["Work for others","Start business","Be unemployed","Go to school"],a:1},
        {q:"Handicraft material?",o:["Cement","Abaca fiber","Steel","Gasoline"],a:1},
        {q:"First sewing step?",o:["Cutting","Measuring","Stitching","Finishing"],a:1},
        {q:"NOT a garden tool?",o:["Trowel","Rake","Stapler","Shovel"],a:2},
        {q:"Plant nutrient?",o:["Water","Sunlight","Nitrogen","Air"],a:2},
        {q:"Animal for egg production?",o:["Goat","Chicken","Pig","Cow"],a:1},
        {q:"Purpose of budgeting?",o:["Spend all","Plan income/expense","Borrow money","Avoid work"],a:1},
        {q:"Cloth joining stitch?",o:["Running","Back","Cross","All"],a:3},
        {q:"Recycling is?",o:["Throw trash","Burn waste","Reuse materials","Buy new"],a:2},
        {q:"Income source?",o:["Salary","Loan","Gift","Lottery"],a:0},
        {q:"Eye safety gear?",o:["Gloves","Goggles","Helmet","Boots"],a:1},
        {q:"Paper maché ingredient?",o:["Clay","Newspaper","Plastic","Metal"],a:1},
        {q:"Rainy season crop?",o:["Rice","Cactus","Wheat","Barley"],a:0},
        {q:"Business plan purpose?",o:["Waste time","Guide operations","Confuse","Avoid tax"],a:1},
        {q:"Textile product?",o:["Chair","Tablecloth","TV","Book"],a:1},
        {q:"Woodcutting tool?",o:["Saw","Pliers","Wrench","Screwdriver"],a:0},
        {q:"Composting is?",o:["Burn waste","Decompose organic","Throw food","Wash dishes"],a:1},
        {q:"Service business?",o:["Bakery","Salon","Grocery","Farm"],a:1}
      ]},
      mapeh: { n: "🎨 MAPEH", q: [
        {q:"MAPEH stands for?",o:["Music Arts PE Health","Math Arts Physics","Music Arch PE History","Media Arts Philosophy"],a:0},
        {q:"Musical scale notes?",o:["5","7","8","10"],a:1},
        {q:"Primary color?",o:["Orange","Green","Blue","Purple"],a:2},
        {q:"Adult resting heart rate?",o:["40-50","60-100","120-140","150-180"],a:1},
        {q:"String instrument?",o:["Flute","Drums","Violin","Trumpet"],a:2},
        {q:"Element for lightness/darkness?",o:["Line","Shape","Value","Texture"],a:2},
        {q:"Cardiovascular exercise?",o:["Stretch","Run","Lift","Sleep"],a:1},
        {q:"Vitamin from sunlight?",o:["A","B","C","D"],a:3},
        {q:"Tempo means?",o:["Loudness","Speed","Pitch","Harmony"],a:1},
        {q:"Melting clocks art?",o:["Impressionism","Surrealism","Cubism","Realism"],a:1},
        {q:"Daily water intake?",o:["2-3 liters","4-5 liters","8 glasses","15 glasses"],a:2},
        {q:"Shuttlecock sport?",o:["Tennis","Badminton","Volleyball","Basketball"],a:1},
        {q:"Forte in music?",o:["Soft","Loud","Fast","Slow"],a:1},
        {q:"Secondary color?",o:["Red","Blue","Yellow","Green"],a:3},
        {q:"Basketball players on court?",o:["4","5","6","7"],a:1},
        {q:"Most energy food group?",o:["Vegetables","Carbs","Dairy","Meat"],a:1},
        {q:"Art rhythm is?",o:["Repeated patterns","Colors","Lines","Sculptures"],a:0},
        {q:"PH folk dance?",o:["Waltz","Tinikling","Ballet","Tango"],a:1},
        {q:"Pumps blood?",o:["Lungs","Liver","Heart","Kidney"],a:2},
        {q:"High-pitched clef?",o:["Bass","Alto","Treble","Tenor"],a:2}
      ]},
      science: { n: "🔬 Science", q: [
        {q:"Center of atom?",o:["Electron","Proton","Nucleus","Neutron"],a:2},
        {q:"Red Planet?",o:["Venus","Jupiter","Mars","Saturn"],a:2},
        {q:"Plant food-making?",o:["Respiration","Photosynthesis","Digestion","Fermentation"],a:1},
        {q:"Water boiling point?",o:["50°C","75°C","100°C","212°C"],a:2},
        {q:"Blood filtering organ?",o:["Heart","Lungs","Kidneys","Stomach"],a:2},
        {q:"Pulls objects to Earth?",o:["Friction","Magnetism","Gravity","Electricity"],a:2},
        {q:"H₂O is?",o:["Oxygen","Hydrogen","Water","CO₂"],a:2},
        {q:"Definite shape/volume state?",o:["Solid","Liquid","Gas","Plasma"],a:0},
        {q:"Largest body organ?",o:["Heart","Liver","Skin","Brain"],a:2},
        {q:"Sun's energy type?",o:["Chemical","Nuclear","Solar","Mechanical"],a:2},
        {q:"Humans breathe out?",o:["Oxygen","Nitrogen","CO₂","Helium"],a:2},
        {q:"Study of living things?",o:["Chemistry","Physics","Biology","Geology"],a:2},
        {q:"Adult human bones?",o:["106","206","306","406"],a:1},
        {q:"Earth's satellite?",o:["Sun","Mars","Moon","Venus"],a:2},
        {q:"Animals laying eggs?",o:["Mammals","Reptiles","Fish","B and C"],a:3},
        {q:"Gold symbol?",o:["Go","Gd","Au","Ag"],a:2},
        {q:"Plant absorbs water from?",o:["Leaves","Stem","Roots","Flowers"],a:2},
        {q:"Speed of light?",o:["300 km/s","300,000 km/s","3,000 km/s","30,000 km/s"],a:1},
        {q:"Prevents scurvy vitamin?",o:["A","B","C","D"],a:2},
        {q:"Hardest substance?",o:["Gold","Iron","Diamond","Platinum"],a:2}
      ]},
      filipino: { n: "🇵🇭 Filipino", q: [
        {q:"Salitang magkasingkahulugan?",o:["Antonym","Synonym","Homonym","Acronym"],a:1},
        {q:"Tamang baybay: Pilipinas?",o:["Pilipinas","Philipinas","Pilipenas","Philippinas"],a:0},
        {q:"Pang-uri ay?",o:["Pangngalan","Pandiwa","Pang-abay","Naglalarawan"],a:3},
        {q:"Tamang pangungusap?",o:["Kumain ang bata","Bata ay kumain","Mansanas kinain","Lahat"],a:0},
        {q:"Kahulugan ng 'masipag'?",o:["Tamad","Matiyaga","Mabagal","Mahina"],a:1},
        {q:"Halimbawa ng pangngalan?",o:["Tumakbo","Maganda","Bahay","Mabilis"],a:2},
        {q:"Kasalungat ng 'mainit'?",o:["Malamig","Maalinsangan","Mabango","Malaki"],a:0},
        {q:"Pangungusap na nagtatanong?",o:["Pasalaysay","Patanong","Pautos","Padamdam"],a:1},
        {q:"Tamang pang-abay?",o:["Maganda","Mabilis","Tumakbo","Bahay"],a:1},
        {q:"'Nagdildil ng asin' kahulugan?",o:["Mahirap","Masaya","Mayaman","Malungkot"],a:0},
        {q:"Pandiwa sa 'Nagluluto si Nanay'?",o:["Nanay","Adobo","Nagluluto","Si"],a:2},
        {q:"Salitang magkasalungat?",o:["Synonym","Antonym","Homophone","Palindrome"],a:1},
        {q:"Patinig sa Filipino?",o:["3","5","7","8"],a:1},
        {q:"Tamang gamit ng 'ng' at 'nang'?",o:["Ng=pandiwa","Nang=pangngalan","Ng=pangngalan/nang=pang-abay","Pareho"],a:2},
        {q:"Pangungusap 'Ang ganda ng bulaklak!'?",o:["Pasalaysay","Patanong","Pautos","Padamdam"],a:3},
        {q:"Tamang kudlit?",o:["Kumain, ako","Kumain ako, ng","Kumain ako ng, kanin","Kumain ako ng kanin"],a:3},
        {q:"Pagbibigay kahulugan sa konteksto?",o:["Denotasyon","Konotasyon","Context clues","Etymology"],a:2},
        {q:"Pambansang bayani?",o:["Andres Bonifacio","Jose Rizal","Apolinario Mabini","Emilio Aguinaldo"],a:1},
        {q:"Layunin ng talumpati?",o:["Magpasaya","Magbigay info","Maglaro","Matulog"],a:1},
        {q:"Unang taludtod ng tula?",o:["Saknong","Taludtod","Sukat","Tugma"],a:1}
      ]},
      ap: { n: "🌏 Araling Panlipunan", q: [
        {q:"Kabisera ng Pilipinas?",o:["Cebu","Davao","Maynila","Quezon City"],a:2},
        {q:"Unang pangulo?",o:["Manuel Quezon","Emilio Aguinaldo","Jose Rizal","Andres Bonifacio"],a:1},
        {q:"Kalayaan idineklara?",o:["June 12, 1898","July 4, 1946","June 12, 1946","July 4, 1898"],a:0},
        {q:"Pinakamataas na bundok?",o:["Mt. Pulag","Mt. Apo","Mt. Pinatubo","Mt. Mayon"],a:1},
        {q:"Rehiyon sa Pilipinas?",o:["15","16","17","18"],a:2},
        {q:"Pinuno ng barangay?",o:["Mayor","Gobernador","Kapitan","Presidente"],a:2},
        {q:"Kontinente ng Pilipinas?",o:["Europa","Afrika","Asya","Amerika"],a:2},
        {q:"Pambansang bulaklak?",o:["Rosal","Sampaguita","Gumamela","Sunflower"],a:1},
        {q:"Sumulat ng 'Noli Me Tangere'?",o:["Andres Bonifacio","Jose Rizal","Apolinario Mabini","Marcelo H. del Pilar"],a:1},
        {q:"Pinakamalaking isla?",o:["Mindanao","Visayas","Luzon","Palawan"],a:2},
        {q:"Pambansang hayop?",o:["Agila","Kalabaw","Tarsier","Maya"],a:1},
        {q:"Ring of Fire?",o:["Lugar maraming sunog","Bulkan sa Pacific","Uri ng pagkain","Festival"],a:1},
        {q:"'Ama ng Wikang Pambansa'?",o:["Jose Rizal","Manuel L. Quezon","Andres Bonifacio","Emilio Aguinaldo"],a:1},
        {q:"Pinakamahabang ilog?",o:["Pasig","Cagayan","Agusan","Pampanga"],a:1},
        {q:"People Power Revolution?",o:["1983","1986","1989","1992"],a:1},
        {q:"Opisyal na pangalan?",o:["Philippine Islands","Republic of the Philippines","Philippine Archipelago","Philippines"],a:1},
        {q:"Nagtatag ng Katipunan?",o:["Jose Rizal","Andres Bonifacio","Emilio Aguinaldo","Apolinario Mabini"],a:1},
        {q:"Pangunahing hanapbuhay?",o:["Pagmimina","Pangingisda","Pagsasaka","Pagnenegosyo"],a:2},
        {q:"Dating pangalan ng Maynila?",o:["Tondo","Maynilad","Manila","Intramuros"],a:1},
        {q:"Termino ng Pangulo?",o:["4 taon","5 taon","6 taon","7 taon"],a:2}
      ]},
      values: { n: "💝 Values Education", q: [
        {q:"Layunin ng Values Education?",o:["Magandang marka","Moral/ethical character","Matuto ng wika","Laging masaya"],a:1},
        {q:"Nagpapakita ng integridad?",o:["Magsinungaling","Pagsasalita ng totoo","Pagsisimula ng away","Pagnanakaw"],a:1},
        {q:"Kahulugan ng respeto?",o:["Malasakit","Papahalagahan ang dignidad","Kompromiso","Takot"],a:1},
        {q:"Halimbawa ng malasakit?",o:["Alagaan ang kaibigan","Tulungan ang kasama","Gabayan ang matanda","Lahat"],a:3},
        {q:"Responsibilidad vs Karapatan?",o:["Pareho","Obligasyon vs Pribilehiyo","Mas mabuti","Hindi mahalaga"],a:1},
        {q:"Pagmamahal sa pamilya?",o:["Emotional support","Magsaya","Tugunan pangangailangan","Lahat"],a:3},
        {q:"Tunay na kaibigan?",o:["May pera","Kasama kapag masaya","Tumutulong anumang oras","May gadgets"],a:2},
        {q:"Pagpapakita ng dedikasyon?",o:["Bigyan ng lahat","Maraming gutom","Patuloy na pagsisikap","Magpahinga lang"],a:2},
        {q:"Ubuntu kahulugan?",o:["Bansa","Karunungan","Kami ay isa","Computer game"],a:2},
        {q:"Gamitin ang kapangyarihan?",o:["Para sa sarili","Para sa lahat","Mapagkamandehan","Para magsaya"],a:1},
        {q:"Tunay na yaman?",o:["Pera at gamit","Kalusugan/pagkakaisa/pagmamahal","Bahay","Sikat"],a:1},
        {q:"Matatag sa pagsubok?",o:["Sumuko","Magtiwala at magpasigasig","Magduda","Maglaro"],a:1},
        {q:"Tunay na tagumpay?",o:["Medalya","Mataas na marka","Mapaganda","Tuparin pangarap"],a:3},
        {q:"Malasakit sa kalikasan?",o:["Mag-recycle","Maghasik puno","Hindi pollute","Lahat"],a:3},
        {q:"Charity kahulugan?",o:["Magsimba","Tulong sa puso","Handog pera","Rebolusyon"],a:1},
        {q:"Kilalanin ang pagkakamali?",o:["Itago","Tanggapin","Kilalanin/mag-improve","Salitain iba"],a:2},
        {q:"Susi sa pagkakaisa?",o:["Labanan","Magtulungan","Matahimik","Magkasama pero different"],a:1},
        {q:"Kagandahan ng espiritu?",o:["Magandang mukha","Katapatan/malasakit","Maraming kasama","Malaking bahay"],a:1},
        {q:"Simula ng pagbabago?",o:["Hingin tulong","Kilalanin/magsikap","Magpanggap tula","Magpahinga"],a:1},
        {q:"Pinakamahalaga sa buhay?",o:["Pera at posisyon","Karakter at relasyon","Damit at ganda","Gadgets"],a:1},
        {q:"Honesty kahulugan?",o:["Matalino","Walang taksil/katapatan","Malakas","Masaya"],a:1},
        {q:"Pakikipagkaibigan ay?",o:["Panahon lang","Malalim na ugnayan","Negosyo","Laro"],a:1},
        {q:"Halaga ng pagpapahayag?",o:["Ingay lang","Magsalita ng kalooban","Maniwala","Sikretuhan"],a:1},
        {q:"Kalusugan mental ay?",o:["Walang lason","Emotional wellbeing","Masipag","Mataba"],a:1},
        {q:"Self-discipline kahulugan?",o:["Pagpapagsiksa","Pagkontrol ng sarili","Pagkain","Tulog"],a:1},
        {q:"Empathy ay pagkakaintindi?",o:["Sarili lang","Sa damdamin ng iba","Mapera","Maganda"],a:1},
        {q:"Leadership kahulugan?",o:["Pumanalo","Gabayan ang grupo","Malakas","Mayaman"],a:1},
        {q:"Paglingkod kahulugan?",o:["Magsikot","Tulong sa komunidad","Gumawa","Maglaro"],a:1},
        {q:"Banal na oras?",o:["Laro","Pakikipag-ugnayan sa Diyos","TV","Tulog"],a:1},
        {q:"Magandang konsensya?",o:["Walang problema","Walang pag-aalinlangan","Masaya","Mabilis"],a:1},
        {q:"Pagmamahal sa bayan?",o:["Hindi mahalaga","Alalay sa bansa","Pera","Laro"],a:1},
        {q:"Matalinong pagpili?",o:["Agarrado","Iniisip mabuti","Madali","Random"],a:1},
        {q:"Kagandahan ng katotohanan?",o:["Masakit","Nagbibigay ng kapayapaan","Maganda","Mahirap"],a:1},
        {q:"Pag-unawa sa kultura?",o:["Makipaglaban","Intindihin at pahalagahan","Labuhan","Itapon"],a:1},
        {q:"Tunay na kagalakan?",o:["Bili","Makabagong gadget","Sa paggawa ng kabutihan","Tulog"],a:2},
        {q:"Malasakit sa edad?",o:["Salita lang","Aksyon at pagtulong","Biro","Bisig"],a:1},
        {q:"Tunay na alaay?",o:["May hangganan","Walang hangganan at totoo","Para lang rito","Negosyo"],a:1},
        {q:"Pagkamalikhain ay?",o:["Pangako","Pagbuo ng bagay na maganda","Likas lang","Siyensya"],a:1},
        {q:"Pagtulong sa nangangailangan?",o:["Pangako lang","Abot-kamay na pagbabago","Malaki","Libre"],a:1},
        {q:"Wakas: Sino ako tunay?",o:["Kung ano gusto ko","Ang aking valor at aksyon","Libas lang","Hindi mahalaga"],a:1}
      ]}
    };

    // State
    let s = null, q = 0, a = [], t = 1800, n = '', c = '';
    let tm;
    const subjects = ['math', 'english', 'epp', 'mapeh', 'science', 'filipino', 'ap', 'values'];
    let currentSubjectIndex = 0;
    let lastResults = null;

    // Config
    const cfg = { main_title: "Enhanced Regional Achievement Test", school_year: "2025-2026" };
    
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig: cfg,
        onConfigChange: (nc) => { 
          Object.assign(cfg, nc);
          document.getElementById('main-title').textContent = cfg.main_title;
          document.getElementById('school-year-display').textContent = `School Year ${cfg.school_year}`;
        },
        mapToCapabilities: () => ({ recolorables: [], borderables: [], fontEditable: undefined, fontSizeable: undefined }),
        mapToEditPanelValues: (nc) => new Map([["main_title", nc.main_title], ["school_year", nc.school_year]])
      });
    }

    function handleLogin(e) {
      e.preventDefault();
      n = document.getElementById('full-name').value.trim();
      c = document.getElementById('student-code').value.trim();
      if (!n || !c) return;
      document.getElementById('login-screen').classList.add('hidden');
      document.getElementById('home-screen').classList.remove('hidden');
    }

    function startQuiz(subj) {
      s = subj;
      currentSubjectIndex = subjects.indexOf(subj);
      q = 0;
      a = new Array(Q[s].q.length).fill(null);
      t = Q[s].q.length <= 20 ? 1800 : 3600;
      document.getElementById('quiz-screen').classList.remove('hidden');
      document.getElementById('home-screen').classList.add('hidden');
      document.getElementById('results-screen').classList.add('hidden');
      document.getElementById('quiz-title').textContent = Q[s].n;
      renderQ();
      clearInterval(tm);
      tm = setInterval(() => { t--; updateT(); if (t <= 0) { clearInterval(tm); submitQ(); } }, 1000);
      updateT();
    }

    function renderQ() {
      const qu = Q[s].q[q];
      document.getElementById('question').textContent = `${q + 1}. ${qu.q}`;
      document.getElementById('q-num').textContent = q + 1;
      document.getElementById('q-total').textContent = Q[s].q.length;
      document.getElementById('progress').style.width = `${((q + 1) / Q[s].q.length) * 100}%`;
      
      const opts = qu.o.map((o, i) => {
        const isLongText = o.length > 60;
        const textSizeClass = isLongText ? 'text-sm' : 'text-base';
        return `
      <option-btn onclick="selA(${i});" class="option-btn w-full text-left p-4 rounded-lg bg-white border border-gray-300 text-gray-900 hover:bg-gray-50 ${a[q] === i ? 'selected bg-blue-100 border-blue-500' : ''}">
        <span class="font-bold mr-3 text-gray-700">${String.fromCharCode(65 + i)}.</span><span class="text-gray-900 ${textSizeClass}">${o}</span>
      </option-btn>
      `;
      }).join('');
      document.getElementById('options').innerHTML = opts;

      document.getElementById('prev-btn').disabled = q === 0;
      if (q === Q[s].q.length - 1) {
        document.getElementById('next-btn').classList.add('hidden');
        document.getElementById('submit-btn').classList.remove('hidden');
      } else {
        document.getElementById('next-btn').classList.remove('hidden');
        document.getElementById('submit-btn').classList.add('hidden');
      }

      // Update summary panel
      updateSummaryPanel();
    }

    function updateSummaryPanel() {
      const summary = document.getElementById('summary-content');
      let html = '';
      
      // Show answered/unanswered counts
      let answered = 0, unanswered = 0;
      for (let i = 0; i < Q[s].q.length; i++) {
        if (a[i] !== null) answered++;
        else unanswered++;
      }

      html += `
        <div class="bg-blue-50 border border-blue-200 rounded-lg p-3">
          <p class="text-sm text-gray-600">Progress</p>
          <p class="text-2xl font-bold text-blue-600">${answered}/${Q[s].q.length}</p>
          <p class="text-xs text-gray-600">Answered</p>
        </div>
      `;

      if (unanswered > 0) {
        html += `
          <div class="bg-amber-50 border border-amber-200 rounded-lg p-3">
            <p class="text-sm text-gray-600">Remaining</p>
            <p class="text-2xl font-bold text-amber-600">${unanswered}</p>
            <p class="text-xs text-gray-600">Unanswered</p>
          </div>
        `;
      }

      html += '<div class="border-t border-gray-200 pt-3 mt-3"><p class="text-xs font-semibold text-gray-700 mb-2">QUICK JUMP</p><div class="grid grid-cols-5 gap-1">';
      
      // Quick navigation buttons
      for (let i = 0; i < Q[s].q.length; i++) {
        const status = a[i] === null ? 'bg-gray-100 text-gray-600' : 'bg-green-100 text-green-700';
        const isCurrent = i === q ? 'ring-2 ring-blue-500 font-bold' : '';
        html += `<button onclick="jumpToQ(${i});" class="w-full py-1 text-xs rounded ${status} ${isCurrent} hover:opacity-80 transition">${i + 1}</button>`;
      }
      
      html += '</div></div>';
      
      summary.innerHTML = html;
      
      // Update all subjects summary
      updateAllSubjectsSummary();
    }

    function updateAllSubjectsSummary() {
      const allSubjectsDiv = document.getElementById('all-subjects-summary');
      let html = '';
      
      // Show each subject's status
      subjects.forEach((subj, idx) => {
        const completed = allResults.find(r => r.subject === Q[subj].n);
        const isCurrent = subj === s;
        const currentClass = isCurrent ? 'ring-2 ring-blue-500 bg-blue-50' : '';
        
        if (completed) {
          const icon = completed.percentage >= 80 ? '✅' : completed.percentage >= 60 ? '👍' : '📚';
          html += `<div class="flex justify-between items-center bg-green-50 rounded-lg p-2 border border-green-200">
            <span class="font-medium text-green-700">${icon} ${Q[subj].n}</span>
            <span class="font-bold text-green-600">${completed.percentage}%</span>
          </div>`;
        } else if (isCurrent) {
          html += `<div class="flex justify-between items-center bg-blue-50 rounded-lg p-2 border border-blue-300 ${currentClass}">
            <span class="font-medium text-blue-700">▶ ${Q[subj].n}</span>
            <span class="text-xs text-blue-600">In Progress</span>
          </div>`;
        } else {
          html += `<div class="flex justify-between items-center bg-gray-50 rounded-lg p-2 border border-gray-200">
            <span class="text-gray-600">${Q[subj].n}</span>
            <span class="text-xs text-gray-400">Not started</span>
          </div>`;
        }
      });
      
      allSubjectsDiv.innerHTML = html;
      
      // Update overall score
      const totalCorrect = allResults.reduce((acc, r) => acc + r.correct, 0);
      const totalQs = allResults.reduce((acc, r) => acc + r.total, 0);
      const totalQsAllSubjects = subjects.reduce((acc, s) => acc + Q[s].q.length, 0);
      const overallPct = totalQsAllSubjects > 0 ? Math.round((totalCorrect / totalQsAllSubjects) * 100) : 0;
      
      document.getElementById('overall-score').textContent = totalCorrect;
      document.getElementById('overall-total').textContent = '/ ' + totalQsAllSubjects;
      document.getElementById('overall-percentage').textContent = overallPct + '% Complete';
    }

    function jumpToQ(index) {
      q = index;
      renderQ();
    }

    function selA(i) {
      a[q] = i;
      renderQ();
    }

    function nextQ() { if (q < Q[s].q.length - 1) { q++; renderQ(); } }
    function prevQ() { if (q > 0) { q--; renderQ(); } }

    function updateT() {
      const m = Math.floor(t / 60), se = t % 60;
      const d = document.getElementById('timer');
      d.textContent = `${m.toString().padStart(2, '0')}:${se.toString().padStart(2, '0')}`;
      if (t <= 300) d.classList.add('timer-danger');
      else d.classList.remove('timer-danger');
    }

    function submitQ() {
      clearInterval(tm);
      const qu = Q[s].q;
      let cor = 0, wr = 0, skip = 0;
      a.forEach((ans, i) => {
        if (ans === null) skip++;
        else if (ans === qu[i].a) cor++;
        else wr++;
      });
      const pct = Math.round((cor / qu.length) * 100);
      
      lastResults = { subject: Q[s].n, score: cor, total: qu.length, percentage: pct, correct: cor, wrong: wr, skipped: skip };
      
      document.getElementById('quiz-screen').classList.add('hidden');
      document.getElementById('results-screen').classList.remove('hidden');
      document.getElementById('result-subject').textContent = Q[s].n;
      document.getElementById('score').textContent = cor;
      document.getElementById('total').textContent = qu.length;
      document.getElementById('percent').textContent = `${pct}%`;
      document.getElementById('correct').textContent = cor;
      document.getElementById('wrong').textContent = wr;
      document.getElementById('skipped').textContent = skip;
      document.getElementById('performance-text').textContent = getPerformanceSummary(pct);
      
      const icon = document.getElementById('result-icon');
      if (pct >= 80) { icon.textContent = '🏆'; createConfetti(); }
      else if (pct >= 60) icon.textContent = '🎉';
      else if (pct >= 40) icon.textContent = '💪';
      else icon.textContent = '📚';
    }

    function getPerformanceSummary(pct) {
      if (pct >= 90) return "🌟 Outstanding! You have mastered this subject. Keep up the excellent work!";
      if (pct >= 80) return "🎖️ Excellent! You have strong understanding. Minor improvements needed.";
      if (pct >= 70) return "👍 Good! You have solid grasp of the material. Review weaker areas.";
      if (pct >= 60) return "📚 Satisfactory. You passed, but focus on improvement.";
      if (pct >= 50) return "⚠️ Fair. You need more study and practice on key concepts.";
      return "❌ Needs Improvement. Review all topics and try again.";
    }

    function createConfetti() {
      const colors = ['#7c3aed', '#06b6d4', '#10b981', '#f59e0b', '#ef4444', '#ec4899'];
      for (let i = 0; i < 30; i++) {
        const c = document.createElement('div');
        c.className = 'confetti-piece';
        c.style.left = Math.random() * 100 + '%';
        c.style.top = '0';
        c.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
        c.style.animationDelay = Math.random() * 1 + 's';
        c.style.width = c.style.height = Math.random() * 10 + 5 + 'px';
        document.body.appendChild(c);
        setTimeout(() => c.remove(), 3000);
      }
    }

    function reviewAnswers() {
      const qu = Q[s].q;
      let html = '';
      qu.forEach((question, i) => {
        const userAns = a[i];
        const correctAns = question.a;
        const isCorrect = userAns === correctAns;
        const status = userAns === null ? '⏭️ Skipped' : isCorrect ? '✅ Correct' : '❌ Wrong';
        const statusColor = userAns === null ? 'text-amber-400' : isCorrect ? 'text-emerald-400' : 'text-rose-400';
        
        const reviewContent = `
          <div class="bg-white/5 rounded-lg p-4 border border-white/10">
            <p class="font-semibold mb-2"><span class="${statusColor}">${status}</span> • Q${i + 1}: ${question.q}</p>
            <p class="text-sm text-white/80 mb-2"><span class="font-medium">Your answer:</span> ${userAns === null ? 'Not answered' : question.o[userAns]}</p>
            <p class="text-sm text-emerald-300"><span class="font-medium">Correct answer:</span> ${question.o[correctAns]}</p>
          </div>
        `;
      });
      document.getElementById('review-content').innerHTML = html;
      document.getElementById('review-modal').classList.remove('hidden');
    }

    function closeReview() {
      document.getElementById('review-modal').classList.add('hidden');
    }

    function showSubmitForm() {
      document.getElementById('submit-status').textContent = '';
      document.getElementById('teacher-email').value = '';
      document.getElementById('teacher-message').value = '';
      document.getElementById('submit-modal').classList.remove('hidden');
    }

    function closeSubmitForm() {
      document.getElementById('submit-modal').classList.add('hidden');
    }

    function submitToTeacher(e) {
      e.preventDefault();
      const email = document.getElementById('teacher-email').value.trim();
      const message = document.getElementById('teacher-message').value.trim();
      const statusEl = document.getElementById('submit-status');
      
      if (!email) {
        statusEl.textContent = '⚠️ Please enter teacher email';
        statusEl.classList.add('text-rose-400');
        return;
      }

      statusEl.textContent = '📤 Preparing submission...';
      statusEl.classList.remove('text-rose-400');
      
      // Simulate submission
      setTimeout(() => {
        const resultsText = `
========================================
      📋 QUIZ RESULT SUBMISSION
========================================

Student Name: ${n}
Student Code: ${c}
Subject: ${lastResults.subject}
Score: ${lastResults.correct}/${lastResults.total} (${lastResults.percentage}%)

📊 Performance Summary:
${getPerformanceSummary(lastResults.percentage)}

Correct Answers: ${lastResults.correct}
Wrong Answers: ${lastResults.wrong}
Skipped: ${lastResults.skipped}

${message ? `📝 Message: ${message}` : ''}

========================================
        `;

        statusEl.innerHTML = '✅ Results prepared! Copy and share with your teacher:';
        statusEl.classList.add('text-emerald-400');
        
        const copyBtn = document.createElement('button');
        copyBtn.type = 'button';
        copyBtn.textContent = '📋 Copy Results';
        copyBtn.className = 'mt-2 px-4 py-2 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white font-medium text-sm';
        copyBtn.onclick = () => {
          navigator.clipboard.writeText(resultsText);
          copyBtn.textContent = '✓ Copied!';
          setTimeout(() => copyBtn.textContent = '📋 Copy Results', 2000);
        };
        statusEl.parentNode.appendChild(copyBtn);
      }, 800);
    }

    function submitAllResults() {
      document.getElementById('teacher-email').value = '';
      document.getElementById('teacher-message').value = '';
      document.getElementById('submit-status').textContent = '';
      document.getElementById('final-summary-screen').classList.add('hidden');
      document.getElementById('submit-modal').classList.remove('hidden');
      
      // Update modal title for all results
      const modalTitle = document.querySelector('#submit-modal h3');
      modalTitle.textContent = '📤 Submit All Results to Teacher';
    }

    function submitAllToTeacher(e) {
      e.preventDefault();
      const email = document.getElementById('teacher-email').value.trim();
      const message = document.getElementById('teacher-message').value.trim();
      const statusEl = document.getElementById('submit-status');
      
      if (!email) {
        statusEl.textContent = '⚠️ Please enter teacher email';
        statusEl.classList.add('text-rose-400');
        return;
      }

      statusEl.textContent = '📤 Preparing submission...';
      statusEl.classList.remove('text-rose-400');
      
      // Simulate submission
      setTimeout(() => {
        const totalCorrect = allResults.reduce((acc, r) => acc + r.correct, 0);
        const totalQuestions = allResults.reduce((acc, r) => acc + r.total, 0);
        const overallPercentage = Math.round((totalCorrect / totalQuestions) * 100);
        
        let subjectsBreakdown = '';
        allResults.forEach(r => {
          subjectsBreakdown += `\n${r.subject}: ${r.correct}/${r.total} (${r.percentage}%)`;
        });
        
        const resultsText = `
========================================
    📋 COMPLETE ASSESSMENT SUBMISSION
========================================

Student Name: ${n}
Student Code: ${c}
Assessment Date: ${new Date().toLocaleDateString()}

📊 OVERALL RESULTS:
Total Score: ${totalCorrect}/${totalQuestions}
Overall Percentage: ${overallPercentage}%
${getPerformanceSummary(overallPercentage)}

📚 SUBJECT BREAKDOWN:${subjectsBreakdown}

${message ? `\n📝 Message: ${message}` : ''}

========================================
        `;

        statusEl.innerHTML = '✅ All results prepared! Copy and share with your teacher:';
        statusEl.classList.add('text-emerald-400');
        
        const copyBtn = document.createElement('button');
        copyBtn.type = 'button';
        copyBtn.textContent = '📋 Copy All Results';
        copyBtn.className = 'mt-2 px-4 py-2 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white font-medium text-sm';
        copyBtn.onclick = () => {
          navigator.clipboard.writeText(resultsText);
          copyBtn.textContent = '✓ Copied!';
          setTimeout(() => copyBtn.textContent = '📋 Copy All Results', 2000);
        };
        statusEl.parentNode.appendChild(copyBtn);
      }, 800);
    }

    function retryQ() { startQuiz(s); }
    function goHome() { 
      clearInterval(tm); 
      allResults = [];
      currentSubjectIndex = 0;
      document.getElementById('home-screen').classList.remove('hidden'); 
      document.getElementById('results-screen').classList.add('hidden');
      document.getElementById('final-summary-screen').classList.add('hidden');
      document.getElementById('submit-modal').classList.add('hidden');
    }
    
    function nextSubject() {
      currentSubjectIndex++;
      if (currentSubjectIndex < subjects.length) {
        // Close modals and go to next subject
        document.getElementById('review-modal').classList.add('hidden');
        document.getElementById('submit-modal').classList.add('hidden');
        startQuiz(subjects[currentSubjectIndex]);
      } else {
        // All subjects completed - show final summary
        showFinalSummary();
      }
    }

    let allResults = [];

    function submitQ() {
      clearInterval(tm);
      const qu = Q[s].q;
      let cor = 0, wr = 0, skip = 0;
      a.forEach((ans, i) => {
        if (ans === null) skip++;
        else if (ans === qu[i].a) cor++;
        else wr++;
      });
      const pct = Math.round((cor / qu.length) * 100);
      
      lastResults = { subject: Q[s].n, score: cor, total: qu.length, percentage: pct, correct: cor, wrong: wr, skipped: skip };
      allResults.push(lastResults);
      
      document.getElementById('quiz-screen').classList.add('hidden');
      document.getElementById('results-screen').classList.remove('hidden');
      document.getElementById('result-subject').textContent = Q[s].n;
      document.getElementById('score').textContent = cor;
      document.getElementById('total').textContent = qu.length;
      document.getElementById('percent').textContent = `${pct}%`;
      document.getElementById('correct').textContent = cor;
      document.getElementById('wrong').textContent = wr;
      document.getElementById('skipped').textContent = skip;
      document.getElementById('performance-text').textContent = getPerformanceSummary(pct);
      
      const icon = document.getElementById('result-icon');
      if (pct >= 80) { icon.textContent = '🏆'; createConfetti(); }
      else if (pct >= 60) icon.textContent = '🎉';
      else if (pct >= 40) icon.textContent = '💪';
      else icon.textContent = '📚';

      // Update next subject button text
      if (currentSubjectIndex < subjects.length - 1) {
        const nextSubjectName = Q[subjects[currentSubjectIndex + 1]].n;
        document.getElementById('next-subject-btn').textContent = `⏭️ Next: ${nextSubjectName}`;
      } else {
        document.getElementById('next-subject-btn').textContent = '✅ Complete All';
      }
    }

    function showFinalSummary() {
      document.getElementById('results-screen').classList.add('hidden');
      document.getElementById('final-summary-screen').classList.remove('hidden');
      
      const totalScores = allResults.reduce((acc, r) => acc + r.correct, 0);
      const totalQuestions = allResults.reduce((acc, r) => acc + r.total, 0);
      const overallPercentage = Math.round((totalScores / totalQuestions) * 100);
      
      document.getElementById('final-score').textContent = totalScores;
      document.getElementById('final-total').textContent = totalQuestions;
      document.getElementById('final-percent').textContent = `${overallPercentage}%`;
      document.getElementById('final-performance').textContent = getPerformanceSummary(overallPercentage);
      
      // Create summary table
      let html = '<div class="space-y-2">';
      allResults.forEach(r => {
        const pct = r.percentage;
        const status = pct >= 80 ? '✅' : pct >= 60 ? '👍' : pct >= 40 ? '📚' : '⚠️';
        html += `
          <div class="flex justify-between items-center bg-white/10 rounded-lg p-3 border border-white/10">
            <div class="flex-1">
              <p class="font-medium">${status} ${r.subject}</p>
              <p class="text-sm text-white/60">${r.correct}/${r.total} correct</p>
            </div>
            <div class="text-right">
              <p class="text-lg font-bold">${r.percentage}%</p>
            </div>
          </div>
        `;
      });
      html += '</div>';
      document.getElementById('results-summary').innerHTML = html;
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d7616b690fcb48c',t:'MTc3MjY4MTkxNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
