<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>เว็บไซต์คำนวณภาษี | โครงงาน IS</title>
<style>
  body {
    font-family: 'Segoe UI', Arial, sans-serif;
    background: #f0f6f4;
    margin: 0;
    padding: 0;
    color: #2e3a2f;
  }
  header {
    background: linear-gradient(90deg, #2b6e2a, #a9995d);
    color: #f5f2e7;
    text-align: center;
    padding: 2rem 1rem;
    border-bottom-left-radius: 40px;
    border-bottom-right-radius: 40px;
    box-shadow: 0 3px 10px rgba(0,0,0,0.1);
  }
  header h1 {
    margin: 0 0 0.5rem 0;
    font-size: 2rem;
    letter-spacing: 1px;
  }
  header p {
    margin: 0;
    font-size: 1rem;
    opacity: 0.85;
  }
  main {
    max-width: 700px;
    margin: 40px auto;
    background: #f9f7f1;
    border-radius: 18px;
    box-shadow: 0 4px 24px rgba(0,0,0,0.08);
    padding: 2rem 2.5rem;
  }
  section {
    margin-bottom: 2.5rem;
  }
  h2 {
    color: #2b6e2a;
    margin-top: 0;
    margin-bottom: 1rem;
    border-left: 5px solid #a9995d;
    padding-left: 10px;
  }
  label {
    display: block;
    margin-bottom: 6px;
    font-weight: 600;
  }
  input[type="number"] {
    width: 100%;
    padding: 10px;
    border: 1.5px solid #a9995d;
    border-radius: 6px;
    font-size: 1rem;
    margin-bottom: 18px;
    background: #fefbf4;
  }
  button {
    background: #2b6e2a;
    color: #f5f2e7;
    border: none;
    padding: 12px 28px;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: 0.3s;
  }
  button:hover {
    background: #1e4c1b;
  }
  .result-box {
    background: #fefbf4;
    border: 1.5px solid #a9995d;
    border-radius: 8px;
    padding: 18px;
    margin-top: 18px;
    font-size: 1.1rem;
  }
  .advice {
    background: #fefbf4;
    border-left: 5px solid #a9995d;
    border-radius: 8px;
    padding: 18px;
    font-size: 1rem;
    color: #2e3a2f;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 18px;
  }
  th, td {
    border: 1.5px solid #a9995d;
    padding: 10px;
    text-align: center;
  }
  th {
    background: #2b6e2a;
    color: #f5f2e7;
  }
  @media (max-width: 700px) {
    main { padding: 1.5rem; }
  }
</style>
</head>
<body>

<header>
  <h1>เว็บไซต์คำนวณภาษี</h1>
  <p>ส่วนหนึ่งของโครงงาน IS กรณีศึกษาเรื่องภาษี</p>
</header>

<main>
  <!-- บทคำนำ -->
  <section>
    <h2>บทคำนำ</h2>
    <p>
      เว็บไซต์นี้จัดทำขึ้นเพื่อใช้ในการศึกษาและเป็นส่วนหนึ่งของโครงงาน IS กรณีศึกษาเรื่องภาษี
      โดยมีวัตถุประสงค์เพื่อให้ผู้ใช้งานสามารถคำนวณภาษีเบื้องต้นได้ด้วยตนเอง
      และได้รับคำแนะนำเกี่ยวกับการยื่นภาษีอย่างถูกต้อง
    </p>
  </section>

  <!-- คำนวณภาษี -->
  <section>
    <h2>คำนวณภาษีของคุณ</h2>
    <form id="taxForm" onsubmit="calculateTax(event)">
      <label for="income">รายได้ทั้งปี (บาท):</label>
      <input type="number" id="income" min="0" required placeholder="กรุณากรอกจำนวนเงินรายได้">

      <label for="deduct">ค่าลดหย่อน (บาท):</label>
      <input type="number" id="deduct" min="0" value="60000" required placeholder="กรุณากรอกค่าลดหย่อน">

      <button type="submit">คำนวณภาษี</button>
    </form>
    <div class="result-box" id="result" style="display:none;"></div>
  </section>

  <!-- ตารางอัตราภาษี -->
  <section>
    <h2>ตารางอัตราภาษีเงินได้บุคคลธรรมดา (ปี 2566)</h2>
    <table>
      <thead>
        <tr>
          <th>ฐานรายได้ (บาท)</th>
          <th>อัตราภาษี (%)</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>0 – 150,000</td><td>0</td></tr>
        <tr><td>150,001 – 300,000</td><td>5</td></tr>
        <tr><td>300,001 – 500,000</td><td>10</td></tr>
        <tr><td>500,001 – 750,000</td><td>15</td></tr>
        <tr><td>750,001 – 1,000,000</td><td>20</td></tr>
        <tr><td>1,000,001 – 2,000,000</td><td>25</td></tr>
        <tr><td>2,000,001 – 5,000,000</td><td>30</td></tr>
        <tr><td>5,000,001 ขึ้นไป</td><td>35</td></tr>
      </tbody>
    </table>
  </section>

  <!-- คำแนะนำ -->
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
    <p style="color:#666; font-size:0.95em;">* หมายเหตุ: ข้อมูลนี้เป็นเพียงแนวทางเบื้องต้น กรุณาตรวจสอบข้อมูลล่าสุดจากกรมสรรพากร</p>

    <!-- ขั้นตอนการยื่นภาษี -->
    <h3 style="margin-top:20px; color:#2b6e2a;">ขั้นตอนการยื่นภาษีเงินได้บุคคลธรรมดา</h3>
    <ol style="text-align:left; margin-left:1rem;">
      <li><strong>เตรียมเอกสารหลักฐานประกอบการยื่นภาษี:</strong> หนังสือรับรองเงินเดือน, หลักฐานการหักลดหย่อน, เอกสารรายได้เพิ่มเติม</li>
      <li><strong>คำนวณรายได้สุทธิและค่าลดหย่อน:</strong> รวมรายได้ทั้งหมดของปีภาษีและหักค่าลดหย่อนตามกฎหมาย</li>
      <li><strong>คำนวณภาษีที่ต้องชำระ:</strong> ใช้เงินได้สุทธิคำนวณตามอัตราภาษีเงินได้บุคคลธรรมดา</li>
      <li><strong>ตรวจสอบความถูกต้องของข้อมูล:</strong> ตรวจสอบเอกสารและผลการคำนวณก่อนทำการยื่นภาษี</li>
      <li><strong>ยื่นแบบแสดงรายการภาษี:</strong> สามารถยื่นผ่านเว็บไซต์ <a href="https://efiling.rd.go.th/rd-cms/" target="_blank">กรมสรรพากร</a> หรือยื่นด้วยตนเองที่สำนักงานสรรพากร</li>
      <li><strong>ชำระภาษีที่ต้องชำระ:</strong> ชำระภาษีภายในกำหนดเวลาที่กฎหมายกำหนด</li>
      <li><strong>เก็บหลักฐานการยื่นภาษี:</strong> เก็บสำเนาแบบฟอร์มและใบเสร็จรับเงินเพื่อเป็นหลักฐาน</li>
    </ol>
  </div>
</section>


<script>
function calculateTax(event) {
  event.preventDefault();
  const income = parseFloat(document.getElementById('income').value) || 0;
  const deduct = parseFloat(document.getElementById('deduct').value) || 0;
  let net = income - deduct;
  if (net < 0) net = 0;

  let tax = 0;
  if (net <= 150000) tax = 0;
  else if (net <= 300000) tax = (net - 150000) * 0.05;
  else if (net <= 500000) tax = (150000*0.05) + (net-300000)*0.10;
  else if (net <= 750000) tax = (150000*0.05)+(200000*0.10)+(net-500000)*0.15;
  else if (net <= 1000000) tax = (150000*0.05)+(200000*0.10)+(250000*0.15)+(net-750000)*0.20;
  else if (net <= 2000000) tax = (150000*0.05)+(200000*0.10)+(250000*0.15)+(250000*0.20)+(net-1000000)*0.25;
  else if (net <= 5000000) tax = (150000*0.05)+(200000*0.10)+(250000*0.15)+(250000*0.20)+(1000000*0.25)+(net-2000000)*0.30;
  else tax = (150000*0.05)+(200000*0.10)+(250000*0.15)+(250000*0.20)+(1000000*0.25)+(3000000*0.30)+(net-5000000)*0.35;

  document.getElementById('result').style.display = 'block';
  document.getElementById('result').innerHTML = `
    <strong>รายได้สุทธิหลังหักค่าลดหย่อน:</strong> ${net.toLocaleString()} บาท<br>
    <strong>ภาษีที่ต้องชำระ:</strong> <span style="color:#2b6e2a;">${tax.toLocaleString(undefined, {maximumFractionDigits:2})} บาท</span>
  `;
}
</script>
</body>
</html>
