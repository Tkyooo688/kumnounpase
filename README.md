<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>เว็บไซต์คำนวณภาษี | โครงงาน IS</title>
  <link rel="stylesheet" href="preentry/styles.css">
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: linear-gradient(120deg, #ffe0e6 0%, #fff 100%);
      margin: 0;
      padding: 0;
      color: #333;
    }
    header {
      background: #FF6F61;
      color: #fff;
      padding: 30px 0 20px 0;
      text-align: center;
      border-bottom-left-radius: 40px;
      border-bottom-right-radius: 40px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    header h1 {
      margin: 0 0 10px 0;
      font-size: 2.2rem;
      letter-spacing: 2px;
    }
    header p {
      margin: 0;
      font-size: 1.1rem;
      opacity: 0.95;
    }
    main {
      max-width: 600px;
      margin: 40px auto 0 auto;
      background: #fff;
      border-radius: 18px;
      box-shadow: 0 4px 24px rgba(255,111,97,0.08);
      padding: 32px 28px 24px 28px;
    }
    section {
      margin-bottom: 32px;
    }
    h2 {
      color: #FF6F61;
      margin-top: 0;
      margin-bottom: 18px;
      font-size: 1.3rem;
      border-left: 5px solid #FF6F61;
      padding-left: 10px;
    }
    label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
    }
    input[type="number"] {
      width: 100%;
      padding: 10px;
      border: 1px solid #FFB3A7;
      border-radius: 6px;
      font-size: 1rem;
      margin-bottom: 18px;
      box-sizing: border-box;
      background: #fff7f6;
    }
    button {
      background: #FF6F61;
      color: #fff;
      border: none;
      padding: 12px 28px;
      border-radius: 6px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s;
      margin-top: 8px;
      margin-bottom: 10px;
    }
    button:hover {
      background: #e65c54;
    }
    .result-box {
      background: #fff7f6;
      border: 1px solid #FFB3A7;
      border-radius: 8px;
      padding: 18px;
      margin-top: 18px;
      font-size: 1.1rem;
      color: #333;
    }
    .advice {
      background: #fff7f6;
      border-left: 5px solid #FF6F61;
      border-radius: 8px;
      padding: 18px;
      font-size: 1rem;
      color: #444;
    }
    @media (max-width: 700px) {
      main { padding: 18px 5vw; }
    }
  </style>
</head>
<body>
  <!-- Pre-entry overlay -->
  <div id="preentry" role="dialog" aria-modal="true" aria-labelledby="preentry-title">
    <div class="card" role="form">
      <h1 id="preentry-title">กรุณากรอกข้อมูลก่อนเข้าหน้าเว็บไซต์</h1>
      <ol class="fields-list">
        <li>
          <label for="pe-firstName">ชื่อ</label>
          <input id="pe-firstName" name="firstName" type="text" placeholder="ชื่อ" required />
        </li>
        <li>
          <label for="pe-lastName">นามสกุล</label>
          <input id="pe-lastName" name="lastName" type="text" placeholder="นามสกุล" required />
        </li>
        <li>
          <label for="pe-age">อายุ</label>
          <input id="pe-age" name="age" type="number" min="0" placeholder="อายุ" required />
        </li>
        <li>
          <label for="pe-occupation">อาชีพ</label>
          <input id="pe-occupation" name="occupation" type="text" placeholder="อาชีพ" required />
        </li>
        <li>
          <label for="pe-income">รายได้ (บาท/เดือน)</label>
          <input id="pe-income" name="income" type="number" min="0" step="0.01" placeholder="รายได้ต่อเดือน" required />
        </li>
      </ol>

      <div class="actions">
        <button id="enterBtn" type="button" disabled>เริ่มต้น</button>
      </div>
      <p class="hint">ข้อมูลใช้เพื่อปรับประสบการณ์ (เก็บไว้ในเครื่อง ไม่เผยแพร่)</p>
    </div>
  </div>

  <header>
    <h1>เว็บไซต์คำนวณภาษี</h1>
    <p>ส่วนหนึ่งของโครงงาน IS กรณีศึกษาเรื่องภาษี</p>
  </header>
  <main id="site-content" aria-hidden="true">
 
    <!-- ส่วนที่ 1: บทคำนำ -->
    <section>
      <h2>บทคำนำ</h2>
      <p>
        เว็บไซต์นี้จัดทำขึ้นเพื่อใช้ในการศึกษาและเป็นส่วนหนึ่งของโครงงาน IS กรณีศึกษาเรื่องภาษี
        โดยมีวัตถุประสงค์เพื่อให้ผู้ใช้งานสามารถคำนวณภาษีเบื้องต้นได้ด้วยตนเอง
        และได้รับคำแนะนำเกี่ยวกับการยื่นภาษีอย่างถูกต้อง
      </p>
    </section>

    <!-- ส่วนที่ 2: คำนวณภาษี -->
    <section>
      <h2>คำนวณภาษีของคุณ</h2>
      <form id="taxForm" onsubmit="calculateTax(event)">
        <label for="income">รายได้ทั้งปี (บาท):</label>
        <input type="number" id="income" min="0" required placeholder="กรุณากรอกจำนวนเงินรายได้">

        <label for="deduct">ค่าลดหย่อน (บาท):</label>
        <input type="number" id="deduct" min="0" value="60000" required placeholder="กรุณากรอกค่าลดหย่อน">
        <div style="color:#888; font-size:0.95em; margin-bottom:12px;">
          <strong>ค่าลดหย่อน</strong> คือจำนวนเงินที่กฎหมายกำหนดให้หักออกจากรายได้ก่อนคำนวณภาษี เช่น ค่าลดหย่อนส่วนตัว 60,000 บาท, คู่สมรส, บุตร, ประกันชีวิต ฯลฯ<br>
          สามารถดูรายละเอียดเพิ่มเติมได้ที่ <a href="https://www.rd.go.th/604.html" target="_blank">กรมสรรพากร</a>
        </div>

        <button type="submit">คำนวณภาษี</button>
      </form>
      <div class="result-box" id="result" style="display:none;"></div>
    </section>

    <!-- ส่วนที่ 3: คำแนะนำและวิธียื่นภาษี -->
    <section>
      <h2>คำแนะนำและวิธียื่นภาษี</h2>
      <div class="advice">
        <ul style="text-align:left;">
          <li>ศึกษาข้อมูลเกี่ยวกับประเภทของรายได้และค่าลดหย่อนที่สามารถใช้ได้</li>
          <li>เตรียมเอกสารที่เกี่ยวข้อง เช่น หนังสือรับรองเงินเดือน, หลักฐานค่าลดหย่อน</li>
          <li>สามารถยื่นภาษีออนไลน์ผ่านเว็บไซต์ <a href="https://efiling.rd.go.th/rd-cms/" target="_blank">กรมสรรพากร</a></li>
          <li>ตรวจสอบข้อมูลก่อนยื่นทุกครั้งเพื่อป้องกันข้อผิดพลาด</li>
          <li>หากมีข้อสงสัยควรปรึกษาผู้เชี่ยวชาญด้านภาษี</li>
        </ul>
        <p style="color:#888; font-size:0.95em;">* หมายเหตุ: ข้อมูลนี้เป็นเพียงแนวทางเบื้องต้น กรุณาตรวจสอบข้อมูลล่าสุดจากกรมสรรพากร</p>
      </div>
    </section>

    <!-- ส่วนที่ 4: อ้างอิง -->
    <section>
      <h2>อ้างอิง</h2>
      <div class="advice">
        <ul style="text-align:left;">
          <li>
            <a href="https://www.rd.go.th/604.html" target="_blank">
              กรมสรรพากร: ตารางอัตราภาษีเงินได้บุคคลธรรมดา
            </a>
          </li>
          <li>
            <a href="https://efiling.rd.go.th/rd-cms/" target="_blank">
              ระบบยื่นแบบแสดงรายการภาษีเงินได้บุคคลธรรมดาออนไลน์
            </a>
          </li>
        </ul>
        <p style="color:#888; font-size:0.95em;">
          * ข้อมูลอัตราภาษีและค่าลดหย่อนอ้างอิงจากเว็บไซต์กรมสรรพากร
        </p>
      </div>
    </section>
  </main>
  <script src="preentry/script.js"></script>
  <script>
    function calculateTax(event) {
      event.preventDefault();
      const income = parseFloat(document.getElementById('income').value) || 0;
      const deduct = parseFloat(document.getElementById('deduct').value) || 0;
      let net = income - deduct;
      if (net < 0) net = 0;

      // ปรับปรุงช่วงรายได้ 0-150,000 และ 150,001-240,000 ไม่เสียภาษี
      let tax = 0;
      if (net <= 150000) {
        tax = 0;
      } else if (net <= 240000) {
        tax = 0;
      } else if (net <= 500000) {
        tax = (net - 240000) * 0.10;
      } else if (net <= 1000000) {
        tax = (260000 * 0.10) + (net - 500000) * 0.20;
      } else if (net <= 2000000) {
        tax = (260000 * 0.10) + (500000 * 0.20) + (net - 1000000) * 0.30;
      } else {
        tax = (260000 * 0.10) + (500000 * 0.20) + (1000000 * 0.30) + (net - 2000000) * 0.35;
      }

      let resultText = `<strong>รายได้สุทธิหลังหักค่าลดหย่อน:</strong> ${net.toLocaleString()} บาท<br>`;
      if (tax === 0) {
        resultText += `<strong style="color:#4CAF50;">ไม่ต้องเสียภาษี แต่ต้องยื่นแบบแสดงรายการภาษีเงินได้บุคคลธรรมดา</strong>`;
      } else {
        resultText += `<strong>ภาษีที่ต้องชำระ:</strong> <span style="color:#FF6F61;">${tax.toLocaleString(undefined, {maximumFractionDigits:2})} บาท</span>`;
      }

      document.getElementById('result').style.display = "block";
      document.getElementById('result').innerHTML = resultText;
    }
  </script>
</body>

</html>
