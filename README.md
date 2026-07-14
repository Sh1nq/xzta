<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>แบบทดสอบ เวชศาสตร์นิวเคลียร์</title>
<style>
  :root{
    --ink:#132a2e;
    --bg:#f3f7f6;
    --panel:#ffffff;
    --line:#dbe6e4;
    --teal:#0f6d63;
    --teal-dark:#0a4f48;
    --teal-soft:#e4f1ee;
    --amber:#b8722a;
    --red:#b53f3f;
    --green:#1f7a4d;
    --shadow: 0 1px 2px rgba(15,45,42,.06), 0 8px 24px rgba(15,45,42,.05);
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:"Sarabun","Noto Sans Thai","Segoe UI",sans-serif;
    line-height:1.6;
  }
  .wrap{
    max-width:880px;
    margin:0 auto;
    padding:28px 18px 90px;
  }
  header.hero{
    background:linear-gradient(135deg,var(--teal-dark),var(--teal));
    color:#eef8f6;
    border-radius:18px;
    padding:34px 28px;
    margin-bottom:28px;
    box-shadow:var(--shadow);
    position:relative;
    overflow:hidden;
  }
  header.hero::after{
    content:"";
    position:absolute;
    right:-40px; top:-40px;
    width:180px; height:180px;
    border-radius:50%;
    background:rgba(255,255,255,.08);
  }
  header.hero h1{
    margin:0 0 6px;
    font-size:1.6rem;
    letter-spacing:.2px;
  }
  header.hero p{
    margin:0;
    color:#cfe9e3;
    font-size:.95rem;
  }
  .meta-bar{
    display:flex;
    flex-wrap:wrap;
    gap:10px;
    margin-top:18px;
  }
  .meta-chip{
    background:rgba(255,255,255,.14);
    border:1px solid rgba(255,255,255,.25);
    border-radius:999px;
    padding:6px 14px;
    font-size:.82rem;
  }

  .toc{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:14px;
    padding:16px 18px;
    margin-bottom:26px;
    box-shadow:var(--shadow);
  }
  .toc h2{
    font-size:.95rem;
    margin:0 0 10px;
    color:var(--teal-dark);
    text-transform:uppercase;
    letter-spacing:.08em;
  }
  .toc ol{
    margin:0; padding-left:20px;
    columns:2;
    gap:24px;
    font-size:.9rem;
  }
  .toc a{
    color:var(--ink);
    text-decoration:none;
    border-bottom:1px dotted transparent;
  }
  .toc a:hover{ border-bottom-color:var(--teal); color:var(--teal-dark);}

  section.category{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:16px;
    padding:22px 22px 8px;
    margin-bottom:24px;
    box-shadow:var(--shadow);
    scroll-margin-top:16px;
  }
  section.category h2{
    font-size:1.15rem;
    color:var(--teal-dark);
    margin:0 0 4px;
    padding-bottom:12px;
    border-bottom:2px solid var(--teal-soft);
    display:flex;
    align-items:baseline;
    justify-content:space-between;
    gap:10px;
  }
  section.category h2 .count{
    font-size:.78rem;
    font-weight:400;
    color:#5c7d78;
    white-space:nowrap;
  }

  .question{
    padding:18px 0;
    border-bottom:1px solid var(--line);
  }
  .question:last-of-type{ border-bottom:none; }

  .qtext{
    font-weight:600;
    margin-bottom:12px;
    display:flex;
    gap:8px;
  }
  .qtext .qnum{
    color:var(--teal);
    font-weight:700;
    min-width:1.6em;
  }

  .options{
    display:flex;
    flex-direction:column;
    gap:6px;
    margin-left:1.6em;
  }
  .option{
    display:flex;
    align-items:flex-start;
    gap:10px;
    padding:9px 12px;
    border-radius:10px;
    border:1px solid transparent;
    cursor:pointer;
    transition:background .15s, border-color .15s;
  }
  .option:hover{ background:var(--teal-soft); }
  .option input{
    margin-top:3px;
    accent-color:var(--teal);
    flex-shrink:0;
  }
  .option .otext{ font-size:.96rem; }
  .option .olabel{ font-weight:600; color:var(--teal-dark); margin-right:2px;}

  .option.correct{
    background:#e7f6ec;
    border-color:var(--green);
  }
  .option.incorrect{
    background:#fbeaea;
    border-color:var(--red);
  }
  .option.disabled{ cursor:default; }

  .result-tag{
    display:inline-block;
    margin-left:1.6em;
    margin-top:6px;
    font-size:.82rem;
    font-weight:600;
    padding:3px 10px;
    border-radius:999px;
  }
  .result-tag.ok{ background:#e2f5e9; color:var(--green); }
  .result-tag.no{ background:#fbe7e7; color:var(--red); }
  .result-tag.blank{ background:#f1ecdf; color:var(--amber); }

  .submit-bar{
    position:sticky;
    bottom:0;
    left:0; right:0;
    background:linear-gradient(180deg, rgba(243,247,246,0), var(--bg) 30%);
    padding:20px 0 6px;
    display:flex;
    justify-content:center;
    z-index:5;
  }
  .submit-btn{
    background:var(--teal);
    color:#fff;
    border:none;
    font-family:inherit;
    font-size:1rem;
    font-weight:700;
    padding:14px 40px;
    border-radius:999px;
    cursor:pointer;
    box-shadow:0 10px 24px rgba(15,109,99,.3);
    transition:transform .1s, background .15s;
  }
  .submit-btn:hover{ background:var(--teal-dark); }
  .submit-btn:active{ transform:scale(.98); }
  .submit-btn:disabled{ background:#9db9b5; cursor:default; box-shadow:none;}

  .score-panel{
    background:var(--panel);
    border:2px solid var(--teal);
    border-radius:16px;
    padding:24px 26px;
    margin-bottom:26px;
    box-shadow:var(--shadow);
    text-align:center;
  }
  .score-panel .big{
    font-size:2.4rem;
    font-weight:800;
    color:var(--teal-dark);
    margin:6px 0;
  }
  .score-panel .sub{ color:#5c7d78; font-size:.92rem; }
  .score-breakdown{
    margin-top:16px;
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:10px;
    text-align:left;
  }
  .score-breakdown .item{
    background:var(--teal-soft);
    border-radius:10px;
    padding:10px 12px;
    font-size:.85rem;
  }
  .score-breakdown .item b{ color:var(--teal-dark); display:block; font-size:.95rem; }

  .reset-btn{
    background:transparent;
    color:var(--teal-dark);
    border:1px solid var(--teal);
    font-family:inherit;
    font-size:.88rem;
    font-weight:600;
    padding:9px 20px;
    border-radius:999px;
    cursor:pointer;
    margin-top:14px;
  }
  .reset-btn:hover{ background:var(--teal-soft); }

  .unanswered-note{
    text-align:center;
    color:var(--amber);
    font-size:.85rem;
    margin-top:8px;
    min-height:1.2em;
  }

  @media (max-width:600px){
    .toc ol{ columns:1; }
    section.category{ padding:18px 16px 4px; }
    header.hero{ padding:26px 20px; }
  }
</style>
</head>
<body>
<div class="wrap">

  <header class="hero">
    <h1>แบบทดสอบ หมวดวิชาชีพสาขาเวชศาสตร์นิวเคลียร์</h1>
    <p>Physics · Instrumentation · Imaging Technique · Radiopharmacy · Clinical Study · Radiation Protection</p>
    <div class="meta-bar">
      <span class="meta-chip" id="chip-total">รวม — ข้อ</span>
      <span class="meta-chip" id="chip-sections">— หมวดวิชา</span>
      <span class="meta-chip">เลือกคำตอบแล้วกดตรวจคำตอบด้านล่าง</span>
    </div>
  </header>

  <nav class="toc">
    <h2>สารบัญหมวดวิชา</h2>
    <ol id="toc-list"></ol>
  </nav>

  <div id="score-container"></div>

  <form id="quiz-form"></form>

  <div class="submit-bar">
    <button class="submit-btn" id="submit-btn" type="button">ตรวจคำตอบ</button>
  </div>
  <div class="unanswered-note" id="unanswered-note"></div>

</div>

<script>
const quizData = [
{
  section: "Physics in Nuclear Medicine",
  questions: [
    { q:"นิวไคลด์ที่เป็น isomer กัน หมายถึงอะไร", options:{
        ก:"มีจำนวนโปรตอนเท่ากัน",
        ข:"มีจำนวนนิวตรอนเท่ากัน",
        ค:"มีจำนวนโปรตอนรวมกับนิวตรอนเท่ากัน",
        ง:"ต่างนิวไคลด์กัน แต่มีระดับพลังงานเท่ากัน",
        จ:"เป็นนิวไคลด์เดียวกัน แต่มีระดับพลังงานต่างกัน"
      }, answer:"จ"},
    { q:"นิวไคลด์ที่มีจำนวนโปรตอนมากเกินไป จะเกิดการสลายตัวแบบใด", options:{
        ก:"Beta minus", ข:"Beta plus", ค:"Alpha", ง:"Isomeric transition", จ:"Internal conversion"
      }, answer:"ข"},
    { q:"รังสีใดใช้ในการรักษาผู้ป่วยทางเวชศาสตร์นิวเคลียร์", options:{
        ก:"Beta ray", ข:"Gamma ray", ค:"X-ray", ง:"Neutron", จ:"Positron"
      }, answer:"ก"},
    { q:"ภายหลังจากการเกิด characteristic x-ray สิ่งที่มีโอกาสเกิดติดตามมาคืออะไร", options:{
        ก:"Compton electron", ข:"Photoelectron", ค:"Conversion electron", ง:"Auger electron", จ:"Gamma ray"
      }, answer:"ง"},
    { q:"เมื่อเกิดการเปลี่ยนแปลงภายในนิวเคลียส สิ่งที่มีโอกาสเกิดตามมาคืออะไร", options:{
        ก:"Auger electron", ข:"Characteristic X-ray", ค:"Conversion electron", ง:"Annihilation photon", จ:"Photoelectron"
      }, answer:"ค"},
    { q:"กระบวนการใดที่ทำให้เกิดคู่ไอออน เมื่อรังสีผ่านมากระทบกับวัตถุตัวกลาง", options:{
        ก:"Excitation", ข:"Ionization", ค:"Decay", ง:"Recombination", จ:"Annihilation"
      }, answer:"ข"},
    { q:"Interaction ของรังสีแกมมากับวัตถุตัวกลาง มีอะไรบ้าง", options:{
        ก:"Photoelectric Effect และ Compton Scattering",
        ข:"Compton Scattering และ Pair production",
        ค:"Ionization และ Excitation",
        ง:"Photoelectric Effect, Compton Scattering และ Pair production",
        จ:"Ionization, Excitation และ Pair production"
      }, answer:"ง"},
    { q:"คุณสมบัติของรังสีเบต้าที่ใช้ทำลายก้อนมะเร็งคือข้อใด", options:{
        ก:"พลังงานต่ำ", ข:"มวลต่ำ", ค:"อำนาจทะลุทะลวงต่ำ", ง:"มีความจำเพาะเจาะจงสูง", จ:"LET ต่ำ"
      }, answer:"ค"},
    { q:"99mTc ให้รังสีแกมมาพลังงานเท่าใด", options:{
        ก:"364 keV", ข:"140 keV", ค:"181 keV", ง:"159 keV", จ:"392 keV"
      }, answer:"ข"},
    { q:"ข้อใดไม่ใช่คุณสมบัติของสารกัมมันตรังสีที่ใช้ในการตรวจถ่ายภาพอวัยวะ", options:{
        ก:"เวลาครึ่งอายุสั้น", ข:"ให้รังสีเบต้า", ค:"ให้รังสีแกมมา 100-300 KeV", ง:"ทำปฏิกิริยาทางเคมีได้ง่าย", จ:"แตกตัวได้ง่าย"
      }, answer:"ข"}
  ]
},
{
  section: "Instrumentation",
  questions: [
    { q:"หัววัดรังสีที่นิยมใช้ในเวชศาสตร์นิวเคลียร์คือข้อใด", options:{
        ก:"Scintillation detector", ข:"Geiger muller detector", ค:"Proportional detector", ง:"Semiconductor detector", จ:"Ionization detector"
      }, answer:"ก"},
    { q:"หัววัดรังสีแบบใดที่มี energy resolution ดีที่สุด", options:{
        ก:"Scintillation detector", ข:"Semiconductor detector", ค:"Proportional detector", ง:"Ionization detector", จ:"Geiger muller detector"
      }, answer:"ข"},
    { q:"หัววัดรังสีแบบใดนิยมใช้กับเครื่องสำรวจรังสี", options:{
        ก:"Semiconductor detector", ข:"Scintillation detector", ค:"Gas-filled detector", ง:"Liquid scintillation detector", จ:"Proportional detector"
      }, answer:"ค"},
    { q:"Liquid scintillation counting system ใช้วัดรังสีใด", options:{
        ก:"รังสีแกมมาพลังงานสูง", ข:"รังสีเบต้า", ค:"รังสีอัลฟา", ง:"อนุภาค", จ:"นิวตรอน"
      }, answer:"ข"},
    { q:"หลักการทำงานของ Photomultiplier tube คืออะไร", options:{
        ก:"ขยายและปรับแต่งขนาดของสัญญาณ",
        ข:"เปลี่ยนรังสีแกมมาให้เป็นสัญญาณไฟฟ้า",
        ค:"เลือกวิเคราะห์สัญญาณที่มีความสูงอยู่ในช่วงที่กำหนดไว้",
        ง:"เปลี่ยนโฟตอนแสงให้เป็นสัญญาณไฟฟ้า",
        จ:"แปลงสัญญาณอนาลอกให้เป็นสัญญาณดิจิตอล"
      }, answer:"ง"},
    { q:"Pulse height analyzers ทำหน้าที่ใด", options:{
        ก:"ขยายสัญญาณ ที่มาจากหัววัดรังสี",
        ข:"เปลี่ยนโฟตอนแสงให้เป็นสัญญาณไฟฟ้า",
        ค:"เปลี่ยนรังสีแกมมาให้เป็นโฟตอนแสง",
        ง:"แปลงสัญญาณอนาลอกให้เป็นสัญญาณดิจิตอล",
        จ:"เลือกวิเคราะห์สัญญาณที่มาจาก Amplifier ที่มีความสูงอยู่ในช่วงที่กำหนดไว้"
      }, answer:"จ"},
    { q:"ความสามารถของหัววัดรังสีในการแยก 2 พลังงานออกจากกันได้เรียกว่าอะไร", options:{
        ก:"Energy differentiation", ข:"Energy resolution", ค:"Energy correlation", ง:"Energy correction", จ:"Energy calibration"
      }, answer:"ข"},
    { q:"ข้อใดจัดเป็น random error ในงานเวชศาสตร์นิวเคลียร์", options:{
        ก:"การติดฉลากชื่อสารกัมมันตรังสีไม่ถูกต้อง",
        ข:"ความแปรปรวนของการสลายตัวของสารกัมมันตรังสี",
        ค:"การตั้งหน้าต่างพลังงานผิดพลาด",
        ง:"การตั้งเวลาในการนับวัดผิดพลาด",
        จ:"เครื่องมือทำงานบกพร่อง"
      }, answer:"ข"},
    { q:"ในการวัดรังสีจาก standard source ที่มีความแรงรังสีเท่ากับ 25.0 mCi วัดรังสีทั้งหมด 10 ครั้ง ได้ค่าเฉลี่ยเท่ากับ 24.0 mCi จงหา accuracy ของเครื่องวัด", options:{
        ก:"2%", ข:"4%", ค:"7%", ง:"8%", จ:"10%"
      }, answer:"ข"},
    { q:"จากการวัดรังสีได้ค่านับวัดเท่ากับ 10000 มี percentage uncertainty เท่าใด", options:{
        ก:"0.01", ข:"0.1", ค:"1.0", ง:"10.0", จ:"100.05"
      }, answer:"ค"},
    { q:"ผลึกเรืองแสงที่นิยมใช้ในเครื่อง gamma camera คือข้อใด", options:{
        ก:"BGO", ข:"LSO", ค:"NaI(Tl)", ง:"CsI(Tl)", จ:"GSO"
      }, answer:"ค"},
    { q:"ลำดับของส่วนประกอบต่าง ๆ ของเครื่อง gamma camera ที่ถูกต้องคือข้อใด", options:{
        ก:"Collimator, NaI(Tl) crystal, light guide, PM tube",
        ข:"Collimator, light guide, NaI(Tl), PM tube",
        ค:"NaI(Tl) crystal, collimator, light guide, PM tube",
        ง:"NaI(Tl) crystal, light guide, collimator, PM tube",
        จ:"NaI(Tl) crystal, PM tube, collimator, light guide"
      }, answer:"ก"},
    { q:"Collimator ของเครื่อง gamma camera ที่นิยมนำมาใช้มากที่สุดคือข้อใด", options:{
        ก:"Parallel hole collimator", ข:"Diverging collimator", ค:"Converging collimator", ง:"Pinhole collimator", จ:"Fan beam collimator"
      }, answer:"ก"},
    { q:"Collimator ที่เหมาะสมในการถ่ายภาพโดยใช้ Ga-67 คือข้อใด", options:{
        ก:"Low energy collimator", ข:"Medium energy collimator", ค:"High energy collimator", ง:"High resolution collimator", จ:"Pinhole collimator"
      }, answer:"ข"},
    { q:"เหตุใด NaI(Tl) จึงเรืองแสงได้ที่อุณหภูมิห้อง", options:{
        ก:"เป็นผลึกใส",
        ข:"มี I เป็นสารช่วยให้เรืองแสงได้ง่าย",
        ค:"มี Na ช่วยให้เรืองแสงได้",
        ง:"มี Tl ช่วยให้เรืองแสงได้",
        จ:"มีความชื้นสูง"
      }, answer:"ง"},
    { q:"Low-energy high resolution (LEHR) กับ Low-energy high sensitivity (LEHS) collimator ต่างกันอย่างไร", options:{
        ก:"LEHR มี septum หนากว่า LEHS",
        ข:"LEHR มีความยาวของรูยาวกว่า LEHS",
        ค:"LEHR มีความยาวของรูสั้นกว่า LEHS",
        ง:"LEHR มี septum บางกว่า LEHS",
        จ:"ไม่แตกต่างกัน"
      }, answer:"ข"},
    { q:"Collimator ข้อใดไม่เหมาะสมกับการถ่ายภาพด้วย Tc-99m", options:{
        ก:"Low-energy general purpose (LEGP)", ข:"Low-energy high resolution (LEHR)", ค:"Diverging", ง:"High-energy all purpose (HEAP)", จ:"Pinhole"
      }, answer:"ง"},
    { q:"ข้อใดไม่ใช่การควบคุมคุณภาพของเครื่อง Gamma camera", options:{
        ก:"Uniformity", ข:"Energy resolution", ค:"Center of rotation", ง:"Spatial resolution", จ:"Sensitivity"
      }, answer:"ข"},
    { q:"พลังงานของรังสีแกมมาที่ได้จากปฏิกิริยา Annihilation เท่ากับข้อใด", options:{
        ก:"0.511 keV", ข:"5.11 keV", ค:"51.1 keV", ง:"511 keV", จ:"5110 keV"
      }, answer:"ง"},
    { q:"ข้อใดไม่ใช่การควบคุมคุณภาพของเครื่อง Dose calibrator", options:{
        ก:"Precision", ข:"Accuracy", ค:"Linearity", ง:"Uniformity", จ:"Geometry"
      }, answer:"ง"},
    { q:"นิวไคลด์รังสีที่ไม่ใช้ในการตรวจสอบ Precision และ Accuracy ของเครื่อง Dose calibrator คือข้อใด", options:{
        ก:"57Co", ข:"133Ba", ค:"137Cs", ง:"11C", จ:"60Co"
      }, answer:"ง"},
    { q:"เครื่องมือที่ใช้วัดรังสีเบต้าคือข้อใด", options:{
        ก:"Gamma camera", ข:"Single photon emission computed tomography", ค:"Liquid scintillation counter", ง:"Positron emission tomography", จ:"Bone densitometer"
      }, answer:"ค"},
    { q:"ข้อใดเป็นข้อดีของการสร้างภาพแบบ ordered subset expectation maximization (OSEM)", options:{
        ก:"ใช้เวลาในการถ่ายภาพน้อยลง",
        ข:"ไม่ต้องใช้ matrix size ขนาดเล็ก",
        ค:"สามารถแก้ไขปัจจัยที่มีผลต่อคุณภาพของภาพได้ดี",
        ง:"สามารถประมวลผลได้เร็ว",
        จ:"เป็นวิธีการไม่ซับซ้อน"
      }, answer:"ค"},
    { q:"Photon attenuation ทำให้เกิดปัญหาในภาพ SPECT มากที่สุดที่บริเวณใด", options:{
        ก:"Head", ข:"Thorax", ค:"Abdomen", ง:"Thigh", จ:"Feet"
      }, answer:"ค"},
    { q:"ข้อใดเป็นข้อเสียของการสร้างภาพแบบ filtered backprojection (FBP)", options:{
        ก:"ใช้เวลาในการประมวลผลสั้น", ข:"ใช้งานง่าย", ค:"มีปัญหาในการแก้ไขเกี่ยวกับ photon attenuation", ง:"ได้ภาพถ่ายที่มีความไม่สม่ำเสมอ", จ:"ต้องใช้คอมพิวเตอร์ที่มีประสิทธิภาพสูง"
      }, answer:"ค"},
    { q:"Sinogram มีความสัมพันธ์กับ projection ในข้อใด", options:{
        ก:"เป็นสิ่งเดียวกัน",
        ข:"sinogram เป็นการนำเอาภาพ projection มาแสดงในแนวแกน y",
        ค:"เป็นภาพ sine wave ที่เปลี่ยนไปตามมุมที่หัววัดหมุนรอบ",
        ง:"sinogram คือการแสดงภาพ โดยภาพ projection ในแนวแกน x ที่สัมพันธ์กับมุมที่เปลี่ยนไป (แกน y)",
        จ:"sinogram เป็นการแสดงภาพ cosine wave"
      }, answer:"ง"},
    { q:"เครื่องมือใดที่ใช้ในการตรวจดูการทำงานของอวัยวะเป็นหลัก", options:{
        ก:"Gamma camera", ข:"X-ray", ค:"Ultrasound", ง:"MRI", จ:"CT scan"
      }, answer:"ก"},
    { q:"การตรวจเพื่อวินิจฉัยโรคกระดูกพรุน ปัจจุบันนิยมใช้เครื่องมือใด", options:{
        ก:"X-ray", ข:"Ultrasound", ค:"CT scan", ง:"Gamma camera", จ:"Dual energy X-ray absorptiometry (DEXA)"
      }, answer:"จ"}
  ]
},
{
  section: "Imaging Technique",
  questions: [
    { q:"ในการถ่ายภาพโดยใช้ I-131, 20% energy window หมายถึงการตั้งช่วง Lower level discriminator และ upper level discriminator ในช่วงใด (I-131 มีพลังงานแกมมาเป็น 364 keV)", options:{
        ก:"300 keV ถึง 500 keV", ข:"344 keV ถึง 384 keV", ค:"327 keV ถึง 400 keV", ง:"320 keV ถึง 380 keV", จ:"291 keV ถึง 437 keV"
      }, answer:"ค"},
    { q:"เครื่อง gamma camera มีขนาดเส้นผ่าศูนย์กลาง 40 cm ถ้าใช้ matrix size เป็น 128x128 จงหาขนาด pixel size โดยประมาณ", options:{
        ก:"1.60 mm", ข:"3.12 mm", ค:"4.20 mm", ง:"5.20 mm", จ:"6.25 mm"
      }, answer:"ข"},
    { q:"ในการตรวจแบบ dynamic เช่น การตรวจ renogram ด้วย Tc-99m DTPA ข้อใดเหมาะสมที่สุด", options:{
        ก:"Low energy general purpose collimator, matrix size 256x256",
        ข:"Low energy general purpose collimator, matrix size 128x128",
        ค:"High energy general purpose collimator, matrix size 64x64",
        ง:"Low energy high resolution collimator, matrix size 256x256",
        จ:"High energy general purpose collimator, matrix size 256x256"
      }, answer:"ข"},
    { q:"การควบคุมคุณภาพของเครื่อง gamma camera ที่จำเป็นต้องทำทุกเช้าก่อนตรวจผู้ป่วยคือ", options:{
        ก:"Spatial resolution", ข:"Flood field uniformity", ค:"Count-rate performance", ง:"Spatial linearity", จ:"System sensitivity"
      }, answer:"ข"},
    { q:"ข้อใดมี Integral Uniformity (IU) ที่บริเวณ central field of view ของเครื่อง gamma camera ดีที่สุด", options:{
        ก:"20%", ข:"15%", ค:"10%", ง:"5%", จ:"2%"
      }, answer:"จ"},
    { q:"จงคำนวณค่า sensitivity ของเครื่อง gamma camera จากการวัด Tc-99m 2.0 mCi ในเวลา 2 นาที ได้ค่านับวัดเป็น 10000", options:{
        ก:"2,500 cps/mCi", ข:"2,500 cpm/mCi", ค:"5,000 cpm/mCi", ง:"5,000 cps/mCi", จ:"20,000 cpm/mCi"
      }, answer:"ข"},
    { q:"ในการถ่ายรูปแบบ static เช่น Lung scan ควรตั้ง matrix size เป็น", options:{
        ก:"32x32", ข:"64x64", ค:"128x256", ง:"256x256", จ:"256x512"
      }, answer:"ง"},
    { q:"ข้อใดที่ผู้ปฏิบัติงานไม่จำเป็นต้องใช้ในขณะเตรียมเภสัชรังสี", options:{
        ก:"สวมถุงมือ", ข:"สวมเสื้อคลุม", ค:"สวมเสื้อตะกั่ว", ง:"ใช้ syringe shield", จ:"ใช้ปากคีบช่วยเมื่อหยิบขวดยารังสี"
      }, answer:"ค"},
    { q:"Tc-99m มีความแรงรังสีเป็น 20.0 mCi/ml ที่เวลา 8.00 น. ถ้าต้องการ 10 mCi เพื่อนำมาฉีดผู้ป่วย เวลา 14.00 น. ต้องเตรียม Tc-99m ปริมาตรประมาณเท่าใด", options:{
        ก:"0.4 ml", ข:"0.5 ml", ค:"1.0 ml", ง:"1.5 ml", จ:"2.0 ml"
      }, answer:"ค"},
    { q:"ในการตรวจผู้ป่วยด้วยเครื่อง gamma camera เจ้าหน้าที่รังสีเทคนิคควรปฏิบัติอย่างไร", options:{
        ก:"นั่งอยู่ใกล้เตียงเพื่อเป็นกำลังใจแก่ผู้ป่วย",
        ข:"อธิบายขั้นตอนของการตรวจแก่ผู้ป่วยก่อนทำการตรวจ",
        ค:"ดูแลผู้ป่วยที่ระยะใกล้เท่าที่จำเป็นหลังจากนั้นจึงถอยมาดูแลในระยะห่าง",
        ง:"ควรอยู่นอกห้องเพราะผู้ป่วยมีปริมาณรังสีสูง",
        จ:"ข้อ ข. และ ค."
      }, answer:"จ"},
    { q:"ข้อใดถูกต้องที่สุดในการตรวจ bone scan", options:{
        ก:"ใช้ High energy collimator และหัววัดชิดกับผู้ป่วย",
        ข:"ใช้ Low energy general purpose collimator และหัววัดห่างกับผู้ป่วย",
        ค:"ใช้ Low energy high resolution collimator และหัววัดชิดกับผู้ป่วย",
        ง:"ใช้ Low energy high resolution collimator และหัววัดห่างกับผู้ป่วย",
        จ:"ใช้ Low energy general purpose collimator และหัววัดชิดกับผู้ป่วย"
      }, answer:"ค"},
    { q:"ข้อใดถูกต้องเกี่ยวกับ star artifact", options:{
        ก:"เกิดจากการเคลื่อนไหวของผู้ป่วยขณะเก็บข้อมูล",
        ข:"เกิดจากการเก็บข้อมูลแบบ continuous",
        ค:"เกิดจากหัววัดรังสีไม่ uniform",
        ง:"ขจัดได้โดยใช้วิธี simple backprojection",
        จ:"ขจัดได้และลดการ blur โดยใช้ ramp filter"
      }, answer:"จ"},
    { q:"Bull's eye artifact ของภาพ SPECT จากการถ่าย point source เกิดจากอะไร", options:{
        ก:"pixel size error", ข:"COR shifting", ค:"ADC failure", ง:"system non-uniformity", จ:"movement"
      }, answer:"ข"},
    { q:"ข้อใดไม่เกี่ยวข้องกับ PET", options:{
        ก:"coincidence circuit", ข:"photon energy 511 keV", ค:"nuclear reactor", ง:"2D และ 3D acquisition", จ:"line of response (LOR)"
      }, answer:"ค"},
    { q:"หัววัดรังสีของเครื่อง gamma camera ขนาดเส้นผ่าศูนย์กลาง 35 ซม. จะให้ค่า resolution ดีที่สุดที่ค่า matrix size ขนาด", options:{
        ก:"32x32", ข:"64x64", ค:"128x128", ง:"256x256", จ:"512x512"
      }, answer:"ค"},
    { q:"จุดที่เล็กที่สุดใน Digital Image คือ", options:{
        ก:"Nibble", ข:"voxel", ค:"pixel", ง:"byte", จ:"bit"
      }, answer:"ค"},
    { q:"การใช้ 99mTc-MIBI ถ่ายภาพเพื่อค้นหา parathyroid adenoma นิยมใช้เทคนิคใด", options:{
        ก:"Dynamic เป็นเวลา 1 นาที", ข:"Dynamic เป็นเวลา 5 นาที", ค:"Static image ที่เวลา 30 นาทีหลังฉีด", ง:"Static image ที่เวลา 1 ชั่วโมงหลังฉีด", จ:"Static image ที่เวลา 10 นาทีและ 2 ชั่วโมงหลังฉีด"
      }, answer:"จ"},
    { q:"18F-FDG เป็นสารเภสัชรังสีที่ใช้ตรวจหาก้อนมะเร็งได้ดีเพราะเหตุผลใด", options:{
        ก:"เซลล์มะเร็งใช้น้ำตาลได้มากกว่าเซลล์ปกติ",
        ข:"18F เป็น positron emitter",
        ค:"FDG เป็นน้ำตาลที่พบในก้อนมะเร็ง",
        ง:"การสร้างภาพด้วยเครื่อง SPECT จะให้ Sensitivity สูง",
        จ:"ใช้ได้กับเครื่อง PET-CT เท่านั้น"
      }, answer:"ก"},
    { q:"เทคนิคการถ่ายภาพใดที่ใช้ประเมิน Testicular torsion", options:{
        ก:"ใช้เฉพาะ Dynamic image ใน 1 นาทีแรกเพื่อดู blood flow",
        ข:"ใช้เฉพาะ Static image ที่ 5 นาทีเพื่อดู blood pool",
        ค:"ใช้เฉพาะ Static image ที่ 120 นาที เพื่อดู testicular uptake",
        ง:"ใช้ทั้ง Dynamic image ใน 1 นาทีแรกและ Serial static images หลังจากนั้น",
        จ:"ใช้เฉพาะ Serial static images หลัง 5 นาที"
      }, answer:"ง"},
    { q:"การทำ nine-point smooth เพื่อปรับภาพดิจิตอลใช้ค่านับวัดจากจำนวน matrix เท่าใด", options:{
        ก:"1x9", ข:"9x9", ค:"3x6", ง:"3x3", จ:"5x4"
      }, answer:"ง"},
    { q:"การทำ attenuation correction มีวัตถุประสงค์เพื่ออะไร", options:{
        ก:"แก้ไขการขยับของอวัยวะระหว่างการถ่ายภาพ",
        ข:"ปรับเพื่อชดเชยการดูดกลืนรังสีโดยคอลลิเมเตอร์",
        ค:"ลดค่านับวัดที่มากเกินจริงเนื่องจากการเกิด pulse pileup",
        ง:"ปรับค่านับวัดที่ถูกลดทอนไปเพราะการเดินทางของรังสีผ่านตัวกลางต่างๆ",
        จ:"ปรับแก้การสลายตัวของนิวไคลด์รังสีที่ใช้"
      }, answer:"ง"},
    { q:"เครื่องถ่ายภาพแบบ PET-CT ที่มี gantry เดียวกัน มีข้อดีคือข้อใด", options:{
        ก:"มีสถิติของการนับวัดที่ดีกว่า",
        ข:"แก้ปัญหาการซ้อนภาพ PET กับ CT ที่ไม่ตรงกันได้",
        ค:"ประหยัดค่าใช้จ่ายมากกว่า",
        ง:"ผู้ป่วยได้รับรังสีน้อยลง",
        จ:"แก้ปัญหา non-uniformity ได้"
      }, answer:"ข"},
    { q:"สารกัมมันตรังสีในข้อใดต่อไปนี้ที่ไม่เหมาะกับการนำมาสร้างภาพด้วย SPECT", options:{
        ก:"Tl-201", ข:"P-32", ค:"I-131", ง:"Tc-99m", จ:"In-111"
      }, answer:"ข"},
    { q:"ในการตรวจ Bone scan โดยใช้ Low energy high-resolution collimator นั้น จะมีผลอย่างไรเมื่อเปรียบเทียบกับการใช้ Low energy all purpose collimator", options:{
        ก:"Sensitivity เพิ่มขึ้น", ข:"Resolution เพิ่มขึ้น", ค:"ลดระยะเวลาในการถ่ายภาพ", ง:"Image contrast เพิ่มขึ้น", จ:"ไม่มีอะไรเปลี่ยนแปลง"
      }, answer:"ข"},
    { q:"ข้อใดต่อไปนี้ไม่ใช่การควบคุมคุณภาพของ SPECT", options:{
        ก:"Center of rotation", ข:"Geometric efficiency", ค:"Intrinsic uniformity", ง:"High count rate performance", จ:"System sensitivity"
      }, answer:"ข"},
    { q:"ข้อใดต่อไปนี้กล่าวไม่ถูกต้องเกี่ยวกับการถ่ายภาพ thyroid gland", options:{
        ก:"สามารถดูขนาดและตำแหน่งของ thyroid gland ได้",
        ข:"ผู้ป่วยสามารถกลืนน้ำลายได้ระหว่างการตรวจ",
        ค:"สามารถใช้ 131I หรือ 99mTc",
        ง:"วาง radioactive marker บริเวณ xiphoid process",
        จ:"สามารถใช้ Pinhole collimator"
      }, answer:"ง"},
    { q:"สารเภสัชรังสีใดต่อไปนี้ไม่สามารถนำมาตรวจหัวใจได้", options:{
        ก:"99mTc-RBC", ข:"99mTc-MIBI", ค:"99mTc-tetrofosmin", ง:"99mTc-MAA", จ:"Tl-201"
      }, answer:"ง"},
    { q:"สารเภสัชรังสีที่นิยมใช้ในการตรวจสแกนกระดูกคือข้อใด", options:{
        ก:"99mTc-MDP", ข:"18F-FDG", ค:"99mTc-MIBI", ง:"99mTc-MAA", จ:"131I"
      }, answer:"ก"},
    { q:"High pass Filter ที่ใช้ในการ reconstruction ภาพของเครื่อง SPECT คือข้อใด", options:{
        ก:"Parzen filter", ข:"Hamming filter", ค:"Butterworth filter", ง:"Ramp filter", จ:"Metz filter"
      }, answer:"ง"},
    { q:"ข้อความใดไม่ถูกต้องในการถ่ายภาพสแกนทางเดินน้ำดี (Hepatobiliary scan)", options:{
        ก:"ถ่ายภาพจนเห็นสารเภสัชรังสีในถุงน้ำดีและลำไส้",
        ข:"ถ่ายภาพ dynamic หรือ static ในท่า anterior view",
        ค:"ถ่ายภาพ right lateral view เพื่อแยกไตออกจากลำไส้",
        ง:"ผู้ป่วยไม่ต้องอดอาหารและน้ำ",
        จ:"ตำแหน่งของหัวใจควรอยู่ในภาพ"
      }, answer:"ง"},
    { q:"ข้อใดไม่ถูกต้องในการทำ radionuclide renography", options:{
        ก:"ผู้ป่วยนอนหงายใต้ gamma detector",
        ข:"ฉีดสารเภสัชรังสีเข้าหลอดเลือดดำแบบ Bolus",
        ค:"บันทึกภาพทันทีที่ฉีดสารเภสัชรังสี",
        ง:"สามารถใช้ Tc-99m MAG-3 หรือ Tc-99m DTPA ในการตรวจ",
        จ:"ใช้เวลาตรวจประมาณ 30 นาที"
      }, answer:"ก"}
  ]
},
{
  section: "Radiopharmaceuticals (Radiopharm)",
  questions: [
    { q:"สารกัมมันตรังสีในข้อใดเป็นสารกัมมันตรังสีในอุดมคติที่ใช้ในการถ่ายภาพทางเวชศาสตร์นิวเคลียร์", options:{
        ก:"Tc-99m, I-131", ข:"Tc-99m, I-123", ค:"Ga-67, I-123", ง:"I-131, Tl-201", จ:"I-131, Sm-153"
      }, answer:"ข"},
    { q:"ป้ายที่ขวดของสารเภสัชรังสีเขียนว่า 7000 MBq/ml เราเรียกค่านี้ว่า", options:{
        ก:"Sensitivity", ข:"Concentration", ค:"Radiochemical activity", ง:"Radiopharmaceutical activity", จ:"Immunoreactivity"
      }, answer:"ข"},
    { q:"Radiochemical impurity ของสารเภสัชรังสีถ้าสูงเกินกำหนด เมื่อฉีดให้ผู้ป่วยแล้วจะทำให้เกิดผลในข้อใด", options:{
        ก:"ผู้ป่วยได้รับอันตรายจากรังสีเกินกำหนด",
        ข:"ผู้ปฏิบัติงานได้รับอันตรายจากรังสีเกินกำหนด",
        ค:"ผู้ป่วยจะเกิดอาการไข้",
        ง:"ภาพที่ได้จะเกิด non-uniformity",
        จ:"นิวไคลด์รังสีบางส่วนเข้าไปสะสมในอวัยวะอื่นที่ไม่ใช่อวัยวะเป้าหมาย"
      }, answer:"จ"},
    { q:"ข้อใดต่อไปนี้ถูกต้องเกี่ยวกับเครื่อง cyclotron", options:{
        ก:"ในเครื่อง cyclotron เมื่อรัศมีวงโคจรของอนุภาคเพิ่มขึ้น อนุภาคจะมีความเร็วสูงขึ้น",
        ข:"ในเครื่อง cyclotron อาศัย deflector ช่วยในการเร่งอนุภาค",
        ค:"I-131 ผลิตจากเครื่อง cyclotron",
        ง:"เครื่อง cyclotron ไม่ต้องอาศัยสนามแม่เหล็ก",
        จ:"อนุภาคในเครื่อง cyclotron เคลื่อนที่เป็นเส้นโค้งได้เพราะแรงของสนามไฟฟ้า"
      }, answer:"ก"},
    { q:"ในการถ่ายภาพด้วย 99mTc-MDP และเห็น uptake ของสารเภสัชรังสีที่ต่อมน้ำลายแสดงว่ามีสาเหตุจากข้อใด", options:{
        ก:"ให้สารเภสัชรังสีแก่ผู้ป่วยมากเกิน",
        ข:"ผู้ป่วยเป็น lymphangitis",
        ค:"มี free Tc-99m pertechnetate",
        ง:"ใช้เวลาในการถ่ายภาพไม่เพียงพอ",
        จ:"ถ่ายภาพทันทีหลังจากได้รับ 99mTc-MDP"
      }, answer:"ค"},
    { q:"นิวไคลด์ที่ไม่ได้มาจากการผลิตด้วยเครื่อง cyclotron คือข้อใด", options:{
        ก:"Carbon-11", ข:"Nitrogen-13", ค:"Oxygen-15", ง:"Fluorine-18", จ:"Molybdenum-99"
      }, answer:"จ"},
    { q:"การเกิดปฏิกิริยา Fission สามารถพบได้ในการผลิตสารกัมมันตภาพรังสีด้วยอะไร", options:{
        ก:"Cyclotron", ข:"Nuclear reactor", ค:"Radionuclide generator", ง:"การสลายตัวตามธรรมชาติ", จ:"Linear accelerator"
      }, answer:"ข"},
    { q:"สารที่ใช้ elute 99mTc จาก Mo-99/Tc-99m generator คือสารใด", options:{
        ก:"Hydrochloric acid", ข:"Sodium hydroxide", ค:"น้ำบริสุทธิ์", ง:"Normal saline", จ:"น้ำแร่"
      }, answer:"ง"},
    { q:"การทดสอบความบริสุทธิ์ทางนิวไคลด์รังสี (Radionuclidic purity) ของ Mo-99/Tc-99m generator เพื่อทดสอบการปนเปื้อนของอะไร", options:{
        ก:"Al3+", ข:"99mTc", ค:"99Mo", ง:"99Tc", จ:"99mTcO4"
      }, answer:"ค"},
    { q:"สารเภสัชรังสี 100 mCi เมื่อตั้งทิ้งไว้ 24 ชั่วโมง วัดปริมาณรังสีได้เพียง 6.25 mCi สารนี้คือข้อใด", options:{
        ก:"Tl-201", ข:"Tc-99m pertechnetate", ค:"I-131 Lipiodol", ง:"Sr-87m", จ:"Molybdenum-99"
      }, answer:"ข"},
    { q:"สารกัมมันตรังสีที่ใช้แพร่หลายในการทำ PET scan คือข้อใด", options:{
        ก:"F-18", ข:"Tc-99m", ค:"Tl-201", ง:"I-131", จ:"Ga-67"
      }, answer:"ก"},
    { q:"กลไกใดที่ต่อมไทรอยด์ใช้ในการดูดจับ I-131", options:{
        ก:"Adsorption", ข:"Active transport", ค:"Capillary blockage", ง:"Phagocytosis", จ:"Receptor binding"
      }, answer:"ข"},
    { q:"กลไกใดที่ใช้ในการตรวจ Lung perfusion scan", options:{
        ก:"Adsorption", ข:"Active transport", ค:"Capillary blockage", ง:"Phagocytosis", จ:"Receptor binding"
      }, answer:"ค"}
  ]
},
{
  section: "Clinical Study",
  questions: [
    { q:"อวัยวะใดไม่ดูดจับ Tc-99m pertechnetate", options:{
        ก:"ปอด", ข:"ต่อมไทรอยด์", ค:"เยื่อบุกระเพาะอาหาร", ง:"Choroid plexus", จ:"ต่อมน้ำลาย"
      }, answer:"ก"},
    { q:"หลังจากฉีดยา Tc-99m MDP ยาส่วนหนึ่งไปจับที่กระดูก ยาที่เหลือจะถูกขับออกทางอวัยวะใด", options:{
        ก:"ลำไส้ใหญ่", ข:"ไต", ค:"ทางเดินน้ำดี", ง:"ต่อมน้ำลาย", จ:"ปอด"
      }, answer:"ข"},
    { q:"ในการทำสแกนกระดูก หลังจากฉีดสารเภสัชรังสี เพื่อให้ได้ภาพคมชัด ผู้ป่วยต้องปฏิบัติตัวอย่างไร", options:{
        ก:"ออกกำลังกาย", ข:"นอนพักผ่อน", ค:"ดื่มน้ำมากๆ", ง:"รับประทานยาระงับประสาทอย่างอ่อน", จ:"อ่านหนังสือ"
      }, answer:"ค"},
    { q:"ความผิดปกติใดที่ไม่พบในการถ่ายสแกนกระดูก", options:{
        ก:"มะเร็ง", ข:"กระดูกอักเสบ", ค:"กระดูกหัก แตก ร้าว", ง:"วัตถุแปลกปลอมปิดกั้นรังสี", จ:"กระดูกพรุน"
      }, answer:"จ"},
    { q:"ข้อใดถูกต้องในการสแกนกระดูก", options:{
        ก:"กระดูกของเด็กจะดูดจับสารรังสีได้ดีกว่าผู้สูงอายุ",
        ข:"ผู้ป่วยต้องงดอาหารและน้ำหลังจากฉีดสารรังสี",
        ค:"ในรายที่สงสัยกระดูกหักต้องทำสแกนกระดูกก่อนการตรวจอย่างอื่น",
        ง:"Hot lesion ในภาพสแกน แสดงว่าผู้ป่วยเป็นมะเร็งแบบแพร่กระจาย",
        จ:"ถ่ายภาพสแกนกระดูกทันทีหลังจากฉีดสารเภสัชรังสี"
      }, answer:"ก"},
    { q:"ตามคำจำกัดความของ WHO ค่า T-score เท่าใด แสดงว่ามีภาวะ osteoporosis", options:{
        ก:"T-score = -1.0", ข:"T-score = -1.7", ค:"T-score = -2.0", ง:"T-score = -2.2", จ:"T-score = -3.0"
      }, answer:"จ"},
    { q:"ผู้ใดไม่มีความเสี่ยงที่จะเป็นโรคกระดูกพรุน", options:{
        ก:"สตรีวัยหมดประจำเดือน", ข:"ผู้ชายสูงวัย", ค:"ผู้ที่สูบบุหรี่จัด", ง:"ผู้ที่ใช้ยา steroid เป็นประจำ", จ:"นักกีฬา"
      }, answer:"จ"},
    { q:"ในการตรวจ Myocardial perfusion SPECT exercise stress test ในผู้ป่วยชายอายุ 70 ปี เพื่อให้ผลถูกต้องแม่นยำ ก่อนฉีดสารเภสัชรังสีควรให้ชีพจรของผู้ป่วยมีอัตราอย่างน้อยที่สุดเท่าไร", options:{
        ก:"127 bpm", ข:"137 bpm", ค:"148 bpm", ง:"159 bpm", จ:"160 bpm"
      }, answer:"ก"},
    { q:"บริเวณที่กล้ามเนื้อหัวใจมีเลือดไปเลี้ยงไม่พอ ภาพ stress-rest myocardial perfusion SPECT จะมีลักษณะอย่างไร", options:{
        ก:"Perfusion ลดลงทั้งคู่",
        ข:"Perfusion ลดลงเฉพาะในภาพ stress",
        ค:"Perfusion เพิ่มขึ้นเฉพาะในภาพ stress",
        ง:"Perfusion เพิ่มขึ้นในภาพ stress และลดลงในภาพ rest",
        จ:"Perfusion เพิ่มขึ้นทั้งคู่"
      }, answer:"ข"},
    { q:"ข้อใดที่ไม่ใช่ข้อมูลที่ได้จากการตรวจ ECG gated blood pool study", options:{
        ก:"ขนาดของหลอดเลือดหัวใจที่ตีบ (coronary stenosis)",
        ข:"ลักษณะการบีบตัวของกล้ามเนื้อหัวใจ (wall motion)",
        ค:"ค่า Ejection fraction (EF)",
        ง:"ค่า EDV and ESV",
        จ:"Aneurysm"
      }, answer:"ก"},
    { q:"ผู้ป่วยควรอยู่ในท่าใด ขณะฉีด Tc-99m MAA", options:{
        ก:"นั่ง", ข:"นอนหงาย", ค:"นอนคว่ำ", ง:"ยืน", จ:"ท่าใดก็ได้"
      }, answer:"ข"},
    { q:"ลักษณะ V/Q scan ที่บ่งถึง acute pulmonary embolism คือข้อใด", options:{
        ก:"มี segmental defect ในภาพ ventilation แต่ปรกติในภาพ perfusion",
        ข:"มี non-segmental defect ในภาพ ventilation แต่ปรกติในภาพ perfusion",
        ค:"มี segmental defect ในภาพ perfusion แต่ปรกติในภาพ ventilation",
        ง:"มี segmental perfusion defect ตรงกับ ventilation defect",
        จ:"มี segmental perfusion defect ตรงกับ ventilation defect และภาพ x-ray ผิดปกติ"
      }, answer:"ค"},
    { q:"ในภาพสแกนอวัยวะใดๆ ด้วย technetium compound ถ้าเห็นต่อมไทรอยด์ ท่านคิดว่าเกิดจากสาเหตุใด", options:{
        ก:"การแตกตัวของเภสัชรังสี", ข:"Right to left shunt", ค:"ใช้ high voltage ไม่ถูกต้อง", ง:"ผู้ป่วยไม่ได้งดอาหารและน้ำ", จ:"ถ่ายภาพสแกนเร็วเกินไป"
      }, answer:"ก"},
    { q:"สารเภสัชรังสีใดที่ไม่ใช้ในการตรวจ Lung ventilation scan", options:{
        ก:"Technegas", ข:"Xenon-133", ค:"Iodine-123", ง:"Tc-99m phytate aerosol", จ:"Tc-99m DTPA aerosol"
      }, answer:"ง"},
    { q:"การทำ venogram ร่วมกับ perfusion scan ควรใช้สารเภสัชรังสีชนิดใด", options:{
        ก:"Tc-99m RBC", ข:"Tc-99m phytate", ค:"Tc-99m MAA", ง:"Tc-99m DTPA", จ:"Tc-99m Sulfur colloid"
      }, answer:"ค"},
    { q:"Tc-99m/Tl-201 subtraction technique มีประโยชน์ในการตรวจอวัยวะใด", options:{
        ก:"Heart", ข:"Liver", ค:"Thyroid gland", ง:"Parathyroid gland", จ:"Salivary gland"
      }, answer:"ง"},
    { q:"ใน radioimmunoassay (RIA) ใช้สารกัมมันตรังสีติดฉลากกับตัวใด", options:{
        ก:"Standard", ข:"Antigen", ค:"Antibody", ง:"QC sample", จ:"Buffer"
      }, answer:"ข"},
    { q:"ใน Immunoradiometric assay (IRMA) ใช้สารกัมมันตรังสีติดฉลากกับตัวใด", options:{
        ก:"Standard", ข:"Antigen", ค:"Antibody", ง:"QC sample", จ:"Buffer"
      }, answer:"ค"},
    { q:"การตรวจใดที่ไม่จำเป็นต้องมีการป้องกันอันตรายจากรังสี", options:{
        ก:"เอกซเรย์นิ้วเท้า", ข:"ถ่ายภาพ CT สมอง", ค:"ถ่ายภาพสแกนกระดูกข้อมือ", ง:"ทำ Technetium thyroid scan ในผู้ใหญ่", จ:"ตรวจอัลตราซาวด์ช่องท้องของหญิงมีครรภ์ 3 เดือนแรก"
      }, answer:"จ"},
    { q:"ขณะถ่ายภาพสแกนที่ใดภายในห้องตรวจมีรังสีสูงสุด", options:{
        ก:"ในถังขยะ", ข:"พื้นห้อง", ค:"เพดานห้องเหนือเตียงผู้ป่วย", ง:"ในตัวผู้ป่วย", จ:"เครื่องควบคุมการถ่ายภาพ"
      }, answer:"ง"},
    { q:"โรคใดที่ไม่สามารถรักษาด้วยสารเภสัชรังสี", options:{
        ก:"Hyperthyroidism", ข:"Thyroid cancer", ค:"Severe bone pain from cancer metastases", ง:"Neuroblastoma", จ:"Myocardial ischemia"
      }, answer:"จ"},
    { q:"ข้อห้ามในการใช้ไอโอดีน-131 รักษาโรคคือข้อใด", options:{
        ก:"ผู้ป่วยสูงอายุ", ข:"ผู้ป่วยมีประวัติแพ้อาหารทะเล", ค:"ผู้ป่วยเป็นโรคภูมิแพ้", ง:"ผู้ป่วยกำลังตั้งครรภ์", จ:"ไม่มีข้อห้ามใดๆ"
      }, answer:"ง"},
    { q:"ในการทำ 24 hour thyroid uptake ก่อนการรักษาคอพอกเป็นพิษด้วยไอโอดีน-131 ผู้ป่วยควรหยุดยา antithyroid drug อย่างน้อยกี่วัน", options:{
        ก:"1-3", ข:"7-10", ค:"11-14", ง:"15-20", จ:"21-25"
      }, answer:"ข"},
    { q:"I-131 Total body scan มีประโยชน์ในการติดตามการรักษาโรคใด", options:{
        ก:"Anaplastic thyroid carcinoma", ข:"Medullary thyroid carcinoma", ค:"Papillary thyroid carcinoma", ง:"Lymphoma", จ:"Hyperthyroidism"
      }, answer:"ค"},
    { q:"Captopril renal scan and renogram ใช้ตรวจผู้ป่วยในรายที่สงสัยภาวะใด", options:{
        ก:"มีนิ่วอุดตันในทางเดินปัสสาวะ", ข:"ไตข้างหนึ่งข้างใดทำงานผิดปกติ", ค:"มี vesicoureteric reflux", ง:"มี renal artery stenosis", จ:"มี acute rejection of transplanted kidney"
      }, answer:"ง"},
    { q:"สารเภสัชรังสีใดที่ใช้ตรวจผู้ป่วยที่สงสัยว่ามีเลือดออกในช่องท้อง", options:{
        ก:"Tc-99m MIBI", ข:"Tc-99m DISIDA", ค:"Tc-99m DTPA", ง:"Tc-99m RBC", จ:"Tc-99m MAA"
      }, answer:"ง"},
    { q:"ผู้ป่วยที่มีเลือดออกทางอุจจาระ สงสัยว่าจะมี Meckel's diverticulum ควรทำการตรวจด้วยวิธีใด", options:{
        ก:"Tc-99m pertechnetate anterior abdominal scan",
        ข:"Tc-99m RBC anterior abdominal scan",
        ค:"I-131 Whole body scan",
        ง:"Tl-201 Intestinal perfusion SPECT",
        จ:"Tc-99m MAA intra-arterial injection imaging"
      }, answer:"ก"},
    { q:"Radiopharmaceutical impurity สามารถตรวจพบได้โดยวิธีใด", options:{
        ก:"Dose calibration", ข:"Gamma ray spectral analysis", ค:"Chromatography", ง:"Colorimeter", จ:"Survey meter"
      }, answer:"ค"},
    { q:"ข้อใดไม่ใช่ตัวอย่างการรักษาโรคด้วยสารเภสัชรังสี", options:{
        ก:"Hyperthyroidism by I-131", ข:"Neuroblastoma by I-131 MIBG", ค:"Thyroid cancer by I-131", ง:"Hepatoma by I-123 Lipiodol", จ:"Colorectal cancer by F-18 FDG"
      }, answer:"จ"},
    { q:"เมื่อสงสัยว่าผู้ป่วยมี recurrent ของ well differentiated thyroid carcinoma ควรเจาะเลือดหาค่าใด", options:{
        ก:"Serum AFP", ข:"Serum CEA", ค:"Serum alkaline phosphatase", ง:"Serum thyroglobulin", จ:"Serum thyroxin"
      }, answer:"ง"},
    { q:"Multiple hot spots ที่พบในภาพ perfusion lung images เกิดจากสาเหตุใด", options:{
        ก:"ฉีดสารเภสัชรังสีเร็วเกินไป",
        ข:"มีสาร Tc-99m phytate ปนเปื้อน",
        ค:"ฉีดสารเภสัชรังสีในขณะที่ผู้ป่วยนั่ง",
        ง:"มี Multiple pulmonary metastases",
        จ:"มีเลือดผู้ป่วยย้อนกลับมาผสมกับสารเภสัชรังสีใน syringe ก่อนฉีด"
      }, answer:"จ"},
    { q:"ข้อความใดไม่ถูกต้องเกี่ยวกับ Renal scan and renogram", options:{
        ก:"First phase of renal curve (30-60 second) ประเมิน renal blood flow",
        ข:"Uptake phase ประเมิน renal function",
        ค:"Second phase ประเมิน cortical and collecting system clearance",
        ง:"Peak activity ของไตทั้งสองข้าง ปรกติจะไม่เกิน 5 นาที",
        จ:"Lasix ใช้ฉีดนาทีที่ 15 เพื่อ exclude complete renal outflow tract obstruction"
      }, answer:"ค"},
    { q:"สารเภสัชรังสีที่ใช้ในการสแกน Salivary gland คือข้อใด", options:{
        ก:"Tc-99m Pertechnetate", ข:"Tc-99m MIBI", ค:"Tc-99m DISIDA", ง:"Tc-99m MDP", จ:"Tc-99m ECD"
      }, answer:"ก"},
    { q:"Tc-99m DTPA เป็นสารเภสัชรังสีที่ไม่ใช้ในการตรวจในข้อใด", options:{
        ก:"Renal imaging", ข:"Lung ventilation imaging", ค:"Brain imaging", ง:"Bone imaging", จ:"Vascular imaging"
      }, answer:"ง"}
  ]
},
{
  section: "Protection in Nuclear Medicine",
  questions: [
    { q:"อุปกรณ์ในข้อใดต่อไปนี้ที่ไม่เหมาะสมสำหรับผู้ปฏิบัติงานในการใช้ป้องกันรังสีขณะฉีดสารเภสัชรังสีให้กับผู้ป่วย", options:{
        ก:"syringe shield", ข:"lead eyeglasses", ค:"glove", ง:"lead apron", จ:"Contact lens"
      }, answer:"จ"},
    { q:"ผู้ป่วยที่ได้รับไอโอดีนรังสีปริมาณเท่าไร ต้องนอนโรงพยาบาลในหอผู้ป่วยที่แยกออกจากหอผู้ป่วยอื่น", options:{
        ก:"มากกว่า 5 mCi", ข:"มากกว่า 10 mCi", ค:"มากกว่า 20 mCi", ง:"มากกว่า 30 mCi", จ:"ต้องนอนโรงพยาบาลทุกคน ไม่ว่าจะได้รับปริมาณเท่าไรก็ตาม"
      }, answer:"ง"},
    { q:"ข้อใดต่อไปนี้เป็นหน่วยวัด Absorbed dose", options:{
        ก:"Curies", ข:"Becquerel", ค:"Gray", ง:"rem", จ:"Sievert"
      }, answer:"ค"},
    { q:"ข้อใดมีผลน้อยที่สุด ในการป้องกันอันตรายจากรังสีในงานด้านเวชศาสตร์นิวเคลียร์", options:{
        ก:"ระยะทาง", ข:"ระยะเวลา", ค:"วัสดุกำบัง", ง:"ความแรงของสารกัมมันตรังสี", จ:"เสื้อคลุม"
      }, answer:"จ"},
    { q:"บุคคลในข้อใดต่อไปมีโอกาสที่จะเกิดการปนเปื้อนจากสารรังสีมากที่สุด", options:{
        ก:"นายก ไม่รับประทานอาหารและเครื่องดื่มในขณะปฏิบัติงานในห้องเตรียมสารเภสัชรังสี",
        ข:"นายข สวมเสื้อคลุมและถุงมือทุกครั้งในขณะปฏิบัติงานในห้องเตรียมสารเภสัชรังสี",
        ค:"นายค ใช้ปากดูดหลอดแก้วเพื่อดูดสารเภสัชรังสีในขณะปฏิบัติงานในห้องเตรียมสารเภสัชรังสี",
        ง:"นายง เตรียมสารเภสัชรังสีชนิดที่ระเหยได้ในตู้ปลอดเชื้อ (Biohazard)",
        จ:"นายจ ใช้อุปกรณ์ปากคีบ (Forceps) ในการจับขวดสารเภสัชรังสี"
      }, answer:"ค"},
    { q:"วัตถุประสงค์หลักในการทดสอบด้วย Wipe testing คือข้อใด", options:{
        ก:"เพื่อวัดการปนเปื้อนสารเภสัชรังสี", ข:"เพื่อวัดปริมาณสารเภสัชรังสี", ค:"เพื่อวัดชนิดของสารเภสัชรังสี", ง:"เพื่อวัดความแรงของสารเภสัชรังสี", จ:"เพื่อวัดการสลายตัวของสารเภสัชรังสี"
      }, answer:"ก"},
    { q:"ข้อใดต่อไปนี้ไม่ถือเป็นกากกัมมันตรังสีชนิดของแข็ง (Solid waste)", options:{
        ก:"ขวดแก้วใส่สารเภสัชรังสีที่ใช้หมดแล้ว", ข:"เข็มฉีดยาที่ผ่านการใช้ฉีดสารเภสัชรังสีให้ผู้ป่วย", ค:"ปัสสาวะของผู้ป่วยที่ได้รับสารเภสัชรังสี", ง:"กระดาษทิชชูที่เปื้อนสารเภสัชรังสี", จ:"Tc-99m generator"
      }, answer:"ค"},
    { q:"บุคคลในข้อใดต่อไปนี้ควรงดรับการรักษาด้วยสารกัมมันตรังสีมากที่สุด", options:{
        ก:"หญิงวัยหมดประจำเดือน", ข:"ผู้ป่วยโรคมะเร็งต่อมไทรอยด์", ค:"ผู้ป่วยที่มีโรคประจำตัว", ง:"ผู้ที่กำลังจะแต่งงาน", จ:"หญิงมีครรภ์"
      }, answer:"จ"},
    { q:"ข้อใดต่อไปนี้ไม่ใช่สาเหตุของการปนเปื้อนทางสารรังสี", options:{
        ก:"อุบัติเหตุขณะปฏิบัติงาน", ข:"การรั่วซึมจากภาชนะที่บรรจุ", ค:"การฟุ้งกระจายของสารรังสี", ง:"การใช้ถุงมือที่ปนเปื้อนสารรังสีไปจับวัสดุอื่น", จ:"ผู้ป่วยที่ได้รับการรักษาด้วยรังสี"
      }, answer:"จ"},
    { q:"ข้อใดไม่ใช่ pathway ที่สารกัมมันตรังสีเข้าสู่ภายในร่างกาย", options:{
        ก:"การหายใจ", ข:"การรับประทาน", ค:"ผิวหนัง", ง:"บาดแผล", จ:"การใกล้ชิดผู้ป่วยที่ได้รับการฝังแร่ Ir-192"
      }, answer:"จ"},
    { q:"การใช้ Syringe shield ในขณะเตรียมสารเภสัชรังสีเพื่อวัตถุประสงค์ในข้อใดมากที่สุด", options:{
        ก:"ลดการปนเปื้อนสารเภสัชรังสี", ข:"ป้องกันการเกิดอุบัติเหตุ", ค:"ลดการได้รับรังสี", ง:"ลดระยะเวลาในการทำงาน", จ:"สะดวกให้การจับหลอดฉีดยา"
      }, answer:"ค"},
    { q:"สารกัมมันตรังสีชนิดใดต้องเก็บในตู้ปลอดเชื้อ (Biohazard) เพื่อป้องกันการฟุ้งกระจายทางรังสี", options:{
        ก:"Cs-137", ข:"Co-60", ค:"Ba-133", ง:"I-131", จ:"Ir-192"
      }, answer:"ง"}
  ]
}
];

// ---------- render ----------
const form = document.getElementById('quiz-form');
const tocList = document.getElementById('toc-list');
let totalQuestions = 0;

quizData.forEach((sec, sIdx) => {
  totalQuestions += sec.questions.length;

  const li = document.createElement('li');
  const a = document.createElement('a');
  a.href = '#sec-' + sIdx;
  a.textContent = sec.section + ' (' + sec.questions.length + ' ข้อ)';
  li.appendChild(a);
  tocList.appendChild(li);

  const secEl = document.createElement('section');
  secEl.className = 'category';
  secEl.id = 'sec-' + sIdx;

  const h2 = document.createElement('h2');
  h2.innerHTML = '<span>' + sec.section + '</span><span class="count">' + sec.questions.length + ' ข้อ</span>';
  secEl.appendChild(h2);

  sec.questions.forEach((item, qIdx) => {
    const qDiv = document.createElement('div');
    qDiv.className = 'question';
    qDiv.dataset.section = sIdx;
    qDiv.dataset.qindex = qIdx;

    const qText = document.createElement('div');
    qText.className = 'qtext';
    qText.innerHTML = '<span class="qnum">' + (qIdx+1) + '.</span><span>' + item.q + '</span>';
    qDiv.appendChild(qText);

    const optsDiv = document.createElement('div');
    optsDiv.className = 'options';

    Object.keys(item.options).forEach(labelKey => {
      const optLabel = document.createElement('label');
      optLabel.className = 'option';
      optLabel.dataset.label = labelKey;

      const input = document.createElement('input');
      input.type = 'radio';
      input.name = 's' + sIdx + '-q' + qIdx;
      input.value = labelKey;

      const otext = document.createElement('span');
      otext.className = 'otext';
      otext.innerHTML = '<span class="olabel">' + labelKey + '.</span>' + item.options[labelKey];

      optLabel.appendChild(input);
      optLabel.appendChild(otext);
      optsDiv.appendChild(optLabel);
    });

    qDiv.appendChild(optsDiv);

    const tag = document.createElement('div');
    tag.className = 'result-tag';
    tag.style.display = 'none';
    tag.dataset.tagFor = 's' + sIdx + '-q' + qIdx;
    qDiv.appendChild(tag);

    secEl.appendChild(qDiv);
  });

  form.appendChild(secEl);
});

document.getElementById('chip-total').textContent = 'รวม ' + totalQuestions + ' ข้อ';
document.getElementById('chip-sections').textContent = quizData.length + ' หมวดวิชา';

// ---------- grading ----------
const submitBtn = document.getElementById('submit-btn');
const scoreContainer = document.getElementById('score-container');
const unansweredNote = document.getElementById('unanswered-note');

submitBtn.addEventListener('click', () => {
  let unanswered = 0;
  let totalCorrect = 0;
  const sectionScores = quizData.map(sec => ({ name: sec.section, correct: 0, total: sec.questions.length }));

  quizData.forEach((sec, sIdx) => {
    sec.questions.forEach((item, qIdx) => {
      const name = 's' + sIdx + '-q' + qIdx;
      const selected = form.querySelector('input[name="' + name + '"]:checked');
      const qDiv = form.querySelector('.question[data-section="' + sIdx + '"][data-qindex="' + qIdx + '"]');
      const tag = qDiv.querySelector('.result-tag');
      const labels = qDiv.querySelectorAll('.option');

      labels.forEach(labelEl => {
        const key = labelEl.dataset.label;
        const input = labelEl.querySelector('input');
        input.disabled = true;
        labelEl.classList.add('disabled');
        if (key === item.answer) {
          labelEl.classList.add('correct');
        } else if (selected && key === selected.value) {
          labelEl.classList.add('incorrect');
        }
      });

      tag.style.display = 'inline-block';
      if (!selected) {
        unanswered++;
        tag.textContent = 'ยังไม่ได้เลือกคำตอบ — เฉลย: ' + item.answer;
        tag.className = 'result-tag blank';
      } else if (selected.value === item.answer) {
        totalCorrect++;
        sectionScores[sIdx].correct++;
        tag.textContent = 'ถูกต้อง';
        tag.className = 'result-tag ok';
      } else {
        tag.textContent = 'ไม่ถูกต้อง — เฉลย: ' + item.answer;
        tag.className = 'result-tag no';
      }
    });
  });

  const pct = ((totalCorrect / totalQuestions) * 100).toFixed(1);

  scoreContainer.innerHTML = `
    <div class="score-panel" id="score-panel">
      <div class="sub">ผลคะแนนรวม</div>
      <div class="big">${totalCorrect} / ${totalQuestions}</div>
      <div class="sub">คิดเป็น ${pct}%</div>
      <div class="score-breakdown">
        ${sectionScores.map(s => `<div class="item"><b>${s.correct}/${s.total}</b>${s.name}</div>`).join('')}
      </div>
      <button class="reset-btn" id="reset-btn" type="button">ทำแบบทดสอบใหม่</button>
    </div>
  `;
  scoreContainer.scrollIntoView({ behavior: 'smooth', block: 'start' });

  submitBtn.disabled = true;
  unansweredNote.textContent = unanswered > 0
    ? 'มี ' + unanswered + ' ข้อที่ยังไม่ได้เลือกคำตอบ (แสดงเฉลยไว้ให้แล้ว)'
    : '';

  document.getElementById('reset-btn').addEventListener('click', () => {
    location.reload();
  });
});
</script>
</body>
</html>
