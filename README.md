<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>โครงงานคำนวณภาษี - วิชา IS</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Mitr&display=swap');

  body {
    font-family: 'Mitr', sans-serif;
    margin: 0; padding: 0;
    background: #e3f0db;
    color: #2e3a2f;
  }
  header {
    background: linear-gradient(90deg, #2b6e2a, #a9995d);
    color: #f5f2e7;
    padding: 1.2rem 2rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1.2px;
  }
  main {
    max-width: 900px;
    margin: 2rem auto;
    background: #f9f7f1;
    border-radius: 10px;
    box-shadow: 0 0 15px #a9995d66;
    padding: 2rem 3rem;
  }
  h1, h2 {
    color: #2b6e2a;
  }
  p.intro {
    font-size: 1rem;
    line-height: 1.5;
    margin-bottom: 1.8rem;
    border-left: 4px solid #a9995d;
    padding-left: 1rem;
    color: #4a5234;
  }
  label {
    display: block;
    margin-top: 1rem;
    font-weight: 600;
  }
  input[type=text], input[type=number], select {
    width: 100%;
    padding: 0.5rem 0.7rem;
    margin-top: 0.3rem;
    border: 1.8px solid #a9995d;
    border-radius: 6px;
    font-size: 1rem;
    background: #fbf9f1;
    color: #2e3a2f;
    box-sizing: border-box;
  }
  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  button {
    margin-top: 2rem;
    background: #2b6e2a;
    border: none;
    color: #f5f2e7;
    font-size: 1.1rem;
    font-weight: 700;
    padding: 0.8rem 2.5rem;
    border-radius: 8px;
    cursor: pointer;
    box-shadow: 0 5px 12px #598a39aa;
    transition: background 0.3s ease;
  }
  button:hover {
    background: #1e4c1b;
  }
  .hidden {
    display: none;
  }
  .search-container {
    position: relative;
  }
  .search-container input[type=text] {
    padding-right: 40px;
  }
  .search-results {
    position: absolute;
    top: 100%;
    left: 0; right: 0;
    max-height: 160px;
    overflow-y: auto;
    background: #fbf9f1;
    border: 1.5px solid #a9995d;
    border-top: none;
    z-index: 100;
  }
  .search-results div {
    padding: 0.4rem 0.8rem;
    cursor: pointer;
  }
  .search-results div:hover {
    background: #a9995d44;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 2rem;
    color: #2e3a2f;
  }
  table, th, td {
    border: 1.5px solid #a9995d;
  }
  th, td {
    padding: 0.7rem 1rem;
    text-align: center;
  }
  th {
    background: #a9995d;
    color: #f5f2e7;
  }
  a.ssp-link {
    color: #2b6e2a;
    text-decoration: underline;
    font-weight: 600;
  }
  a.ssp-link:hover {
    color: #1e4c1b;
  }
  footer {
    margin-top: 3rem;
    text-align: center;
    font-size: 0.9rem;
    color: #777;
  }
</style>
</head>
<body>

<header>
  โครงงานคำนวณภาษีเงินได้บุคคลธรรมดา <br />
  <small>จัดทำเพื่อวิชา IS เท่านั้น (ไม่ใช่เว็บไซต์ทางการ)</small>
</header>

<main>
  <!-- หน้า 1 : คำนำ + กรอกข้อมูล -->
  <section id="page1">
    <h1>คำชี้แจงและคำนำ</h1>
    <p class="intro">
      โครงงานนี้จัดทำขึ้นเพื่อใช้ในวิชา IS โดยมีวัตถุประสงค์เพื่อช่วยในการคำนวณภาษีเงินได้บุคคลธรรมดาตามกฎหมายไทยอย่างถูกต้องและง่ายดาย<br />
      ผู้ใช้งานสามารถกรอกข้อมูลส่วนตัว เช่น ชื่อ, อายุ, อาชีพ รวมถึงรายได้และค่าลดหย่อนต่างๆ เพื่อคำนวณภาษีที่ต้องชำระ<br />
      โปรดใช้ข้อมูลจริงและตรวจสอบให้แน่ใจว่ากรอกข้อมูลครบถ้วนก่อนทำการคำนวณ<br />
      สำหรับข้อมูลเพิ่มเติมและการยื่นภาษีอย่างเป็นทางการ สามารถเยี่ยมชมเว็บไซต์กรมสรรพากรได้ที่ <a href="https://www.rd.go.th" target="_blank" class="ssp-link">www.rd.go.th</a>
    </p>

    <form id="infoForm">
      <label for="name">ชื่อ-นามสกุล</label>
      <input type="text" id="name" required placeholder="เช่น สมชาย ใจดี" />

      <label for="age">อายุ</label>
      <input type="number" id="age" min="15" max="100" required placeholder="ปี" />

      <label for="occupationSearch">ค้นหาอาชีพ</label>
      <div class="search-container">
        <input type="text" id="occupationSearch" placeholder="พิมพ์เพื่อค้นหาอาชีพ..." autocomplete="off" />
        <div id="searchResults" class="search-results hidden"></div>
      </div>

      <label for="occupationSelect">เลือกอาชีพ</label>
      <select id="occupationSelect" size="6" required></select>

      <button type="submit">ถัดไป &raquo;</button>
    </form>
  </section>

  <!-- หน้า 2 : คำนวณภาษี -->
  <section id="page2" class="hidden">
    <h1>คำนวณภาษีเงินได้บุคคลธรรมดา</h1>

    <form id="taxForm">
      <label>ชื่อ-นามสกุล</label>
      <p id="showName" style="font-weight:700; margin-bottom:1rem;"></p>

      <label>อายุ</label>
      <p id="showAge" style="font-weight:700; margin-bottom:1rem;"></p>

      <label>อาชีพ</label>
      <p id="showOccupation" style="font-weight:700; margin-bottom:1rem;"></p>

      <label for="income">รายได้ต่อปี (บาท)</label>
      <input type="number" id="income" min="0" required placeholder="เช่น 500000" />

      <label for="deductions">ค่าลดหย่อนต่อปี (บาท)</label>
      <input type="number" id="deductions" min="0" value="60000" required />

      <button type="submit">คำนวณภาษี</button>
    </form>

    <div id="result" style="margin-top: 2rem;"></div>

    <h2>อัตราภาษีเงินได้บุคคลธรรมดา</h2>
    <table>
      <thead>
        <tr>
          <th>ฐานภาษี (บาท)</th>
          <th>อัตราภาษี (%)</th>
          <th>จำนวนภาษีที่ต้องชำระ (บาท)</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>0 – 150,000</td><td>0</td><td>ยกเว้นภาษี</td></tr>
        <tr><td>150,001 – 300,000</td><td>5</td><td>5% ของเงินได้สุทธิ</td></tr>
        <tr><td>300,001 – 500,000</td><td>10</td><td>10% ของเงินได้สุทธิ</td></tr>
        <tr><td>500,001 – 750,000</td><td>15</td><td>15% ของเงินได้สุทธิ</td></tr>
        <tr><td>750,001 – 1,000,000</td><td>20</td><td>20% ของเงินได้สุทธิ</td></tr>
        <tr><td>1,000,001 – 2,000,000</td><td>25</td><td>25% ของเงินได้สุทธิ</td></tr>
        <tr><td>2,000,001 – 5,000,000</td><td>30</td><td>30% ของเงินได้สุทธิ</td></tr>
        <tr><td>5,000,001 ขึ้นไป</td><td>35</td><td>35% ของเงินได้สุทธิ</td></tr>
      </tbody>
    </table>

    <p style="margin-top:1.5rem;">
      ขอแนะนำให้ตรวจสอบข้อมูลกับเว็บไซต์กรมสรรพากร <a href="https://www.rd.go.th" target="_blank" class="ssp-link">www.rd.go.th</a> ก่อนการยื่นภาษีทุกครั้ง
    </p>

    <button id="backBtn" style="background:#a9995d;">ย้อนกลับ</button>
  </section>
</main>

<footer>
  &copy; 2025 โครงงานคำนวณภาษี วิชา IS
</footer>

<script>
  // อาชีพตัวอย่างเยอะๆ (ตัดให้เห็นตัวอย่างก่อน)
  const occupations = [
    "นักเรียน/นักศึกษา", "พนักงานบริษัท", "เจ้าของกิจการ", "ฟรีแลนซ์", "ข้าราชการ", "ครู", "แพทย์", "วิศวกร", 
    "นักบัญชี", "นักกฎหมาย", "พนักงานธนาคาร", "นักวิจัย", "ศิลปิน", "นักดนตรี", "นักกีฬา", "นักข่าว", 
    "ช่างภาพ", "นักออกแบบ", "โปรแกรมเมอร์", "พนักงานโรงแรม", "พนักงานขาย", "เจ้าหน้าที่ฝ่ายการตลาด", 
    "พนักงานขับรถ", "แม่บ้าน", "ช่างซ่อม", "เกษตรกร", "ชาวประมง", "นักธุรกิจ", "เจ้าของร้านอาหาร", 
    "พนักงาน Call Center", "นักจิตวิทยา", "นักสังคมสงเคราะห์", "พยาบาล", "นักบวช", "นักบำบัด", "นักเทคนิคการแพทย์",
    "นักเศรษฐศาสตร์", "นักบริหาร", "ผู้จัดการ", "ผู้ประกอบการ", "ช่างไฟฟ้า", "นักพัฒนาเว็บ", "ช่างไม้", "ช่างเชื่อม",
    "นักออกแบบแฟชั่น", "เจ้าหน้าที่รักษาความปลอดภัย", "นักวิเคราะห์ข้อมูล", "พนักงานขนส่ง", "นักภาษาศาสตร์",
    "เจ้าหน้าที่ประชาสัมพันธ์", "นักแปลภาษา", "นักดาราศาสตร์", "นักโบราณคดี", "นักวิทยาศาสตร์", "นักสถิติ",
    "นักวางแผนทางการเงิน", "ผู้บริหารระดับสูง", "นักแสดง", "ผู้กำกับหนัง", "นักเทคโนโลยีสารสนเทศ", "นักทำสวน",
    "ช่างภาพยนตร์", "พนักงานสายการบิน", "ผู้จัดการโรงแรม", "นักกายภาพบำบัด", "นักบรรยาย", "นักประชาสัมพันธ์",
    "นักบัญชีตรวจสอบ", "นักโฆษณา", "เจ้าหน้าที่สาธารณสุข", "นักจัดการทรัพยากรมนุษย์", "นักประชาสัมพันธ์",
    "นักวางแผนเมือง", "เจ้าหน้าที่ฝ่ายกฎหมาย", "นักเขียน", "นักวิชาการ", "เจ้าหน้าที่ฝ่ายสนับสนุน"
  ];

  // ฟังก์ชันเติม dropdown อาชีพ
  const occupationSelect = document.getElementById('occupationSelect');
  function fillOccupations(list) {
    occupationSelect.innerHTML = '';
    list.forEach(occ => {
      const option = document.createElement('option');
      option.value = occ;
      option.textContent = occ;
      occupationSelect.appendChild(option);
    });
  }
  fillOccupations(occupations);

  // ค้นหาอาชีพ
  const occupationSearch = document.getElementById('occupationSearch');
  const searchResults = document.getElementById('searchResults');

  occupationSearch.addEventListener('input', () => {
    const query = occupationSearch.value.toLowerCase().trim();
    if (!query) {
      searchResults.classList.add('hidden');
      return;
    }
    const filtered = occupations.filter(o => o.toLowerCase().includes(query));
    if (filtered.length === 0) {
      searchResults.classList.add('hidden');
      return;
    }
    searchResults.innerHTML = '';
    filtered.forEach(item => {
      const div = document.createElement('div');
      div.textContent = item;
      div.onclick = () => {
        occupationSelect.value = item;
        occupationSearch.value = item;
        searchResults.classList.add('hidden');
      };
      searchResults.appendChild(div);
    });
    searchResults.classList.remove('hidden');
  });

  document.addEventListener('click', (e) => {
    if (!occupationSearch.contains(e.target)) {
      searchResults.classList.add('hidden');
    }
  });

  // หน้าแรก กรอกข้อมูล
  const infoForm = document.getElementById('infoForm');
  infoForm.addEventListener('submit', e => {
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const age = parseInt(document.getElementById('age').value);
    const occupation = occupationSelect.value;

    if (!name || !age || !occupation) {
      alert('กรุณากรอกข้อมูลให้ครบถ้วน');
      return;
    }

    document.getElementById('showName').textContent = name;
    document.getElementById('showAge').textContent = age;
    document.getElementById('showOccupation').textContent = occupation;

    document.getElementById('page1').classList.add('hidden');
    document.getElementById('page2').classList.remove('hidden');
  });

  // คำนวณภาษี
  const taxForm = document.getElementById('taxForm');
  taxForm.addEventListener('submit', e => {
    e.preventDefault();
    const income = parseFloat(document.getElementById('income').value);
    const deductions = parseFloat(document.getElementById('deductions').value);
    if (income < 0 || deductions < 0) {
      alert('กรุณากรอกตัวเลขที่ถูกต้อง');
      return;
    }

    const taxableIncome = Math.max(0, income - deductions);
    let tax = 0;

    const brackets = [
      { limit: 150000, rate: 0 },
      { limit: 300000, rate: 0.05 },
      { limit: 500000, rate: 0.10 },
      { limit: 750000, rate: 0.15 },
      { limit: 1000000, rate: 0.20 },
      { limit: 2000000, rate: 0.25 },
      { limit: 5000000, rate: 0.30 },
      { limit: Infinity, rate: 0.35 }
    ];

    let remaining = taxableIncome;
    let lastLimit = 0;
    for (const bracket of brackets) {
      if (remaining <= 0) break;
      const taxableAtThisRate = Math.min(bracket.limit - lastLimit, remaining);
      tax += taxableAtThisRate * bracket.rate;
      remaining -= taxableAtThisRate;
      lastLimit = bracket.limit;
    }

    const resultDiv = document.getElementById('result');
    resultDiv.innerHTML = `
      <h2>ผลลัพธ์การคำนวณ</h2>
      <p>รายได้สุทธิหลังหักค่าลดหย่อน: <strong>${taxableIncome.toLocaleString()} บาท</strong></p>
      <p>ภาษีที่ต้องชำระ: <strong>${tax.toLocaleString(undefined, {minimumFractionDigits:2, maximumFractionDigits:2})} บาท</strong></p>
    `;
  });

  // ปุ่มย้อนกลับหน้าแรก
  document.getElementById('backBtn').addEventListener('click', () => {
   
