<html lang="th">
<head>
  <meta charset="utf-8" />
  <title>ระบบแปลผลการดำเนินกิจกรรมออนไลน์</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <style>
    * {
      box-sizing: border-box;
      font-family: "Sarabun", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 20px;
      color: #222;

      /* พื้นหลังรูปโรงเรียน */
      background-image: url("school-bg.jpg"); /* เปลี่ยนชื่อไฟล์ตามรูปโรงเรียนของครู */
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
    }

    .app-wrapper {
      width: 100%;
      max-width: 1100px;
      background: rgba(255, 255, 255, 0.92);
      border-radius: 16px;
      padding: 24px 24px 40px;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.3);
      backdrop-filter: blur(4px);
    }

    h1 {
      margin: 0 0 10px;
      font-size: 1.7rem;
      color: #333;
    }

    h2 {
      margin: 12px 0 6px;
      font-size: 1.2rem;
      color: #333;
    }

    p.subtitle {
      text-align: center;
      margin: 0 0 20px;
      color: #555;
      font-size: 0.95rem;
    }

    .flex {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
    }

    .card {
      background: #f8f9ff;
      border-radius: 14px;
      padding: 16px 18px;
      margin-bottom: 12px;
      border: 1px solid #e1e4ff;
    }

    label {
      display: block;
      font-size: 0.9rem;
      margin-bottom: 4px;
      color: #444;
      font-weight: 600;
    }

    input[type="number"],
    input[type="text"],
    input[type="password"],
    textarea,
    select {
      width: 100%;
      padding: 6px 8px;
      border-radius: 8px;
      border: 1px solid #d0d4f5;
      font-size: 0.9rem;
      outline: none;
      background: #ffffff;
    }

    input[type="number"]:focus,
    input[type="text"]:focus,
    input[type="password"]:focus,
    textarea:focus,
    select:focus {
      border-color: #667eea;
      box-shadow: 0 0 0 1px rgba(102, 126, 234, 0.3);
    }

    textarea {
      min-height: 70px;
      resize: vertical;
    }

    button {
      border: none;
      border-radius: 999px;
      padding: 8px 14px;
      font-size: 0.9rem;
      font-weight: 600;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: transform 0.05s ease, box-shadow 0.1s ease, background 0.2s ease;
      white-space: nowrap;
    }

    button.primary {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      box-shadow: 0 8px 18px rgba(102, 126, 234, 0.35);
    }

    button.secondary {
      background: #ffffff;
      color: #444;
      border: 1px solid #d0d4f5;
    }

    button.soft {
      background: #fdfdfd;
      border: 1px solid #e0e2ff;
      color: #333;
    }

    button:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 24px rgba(0, 0, 0, 0.16);
    }

    button:active {
      transform: translateY(0);
      box-shadow: none;
    }

    button:disabled {
      opacity: 0.55;
      cursor: not-allowed;
      box-shadow: none;
      transform: none;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      padding: 3px 10px;
      border-radius: 999px;
      font-size: 0.75rem;
      font-weight: 600;
    }

    .badge.green {
      background: #e3f9e5;
      color: #2c7a3f;
    }

    .badge.red {
      background: #ffe5e7;
      color: #c53030;
    }

    .badge.yellow {
      background: #fff8e1;
      color: #b7791f;
    }

    .badge.blue {
      background: #e3f0ff;
      color: #2b6cb0;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.85rem;
      background: white;
      border-radius: 10px;
      overflow: hidden;
      border: 1px solid #e1e4ff;
    }

    th, td {
      padding: 6px 6px;
      border-bottom: 1px solid #edf0ff;
      text-align: center;
    }

    th {
      background: #eef0ff;
      font-weight: 700;
    }

    tr:nth-child(even) {
      background: #fafbff;
    }

    .small {
      font-size: 0.8rem;
      color: #666;
    }

    .mt-1 { margin-top: 4px; }
    .mt-2 { margin-top: 8px; }
    .mt-3 { margin-top: 12px; }
    .mt-4 { margin-top: 16px; }

    .result-box {
      background: #ffffff;
      border-radius: 12px;
      padding: 12px 14px;
      border: 1px solid #dde1ff;
      margin-top: 8px;
    }

    .result-title {
      font-weight: 700;
      margin-bottom: 4px;
      font-size: 0.95rem;
    }

    .result-text {
      font-size: 0.86rem;
      line-height: 1.5;
      color: #333;
      white-space: pre-wrap;
    }

    .kpi-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 6px;
    }

    .kpi-card {
      flex: 1 1 150px;
      background: #ffffff;
      border-radius: 10px;
      padding: 8px 10px;
      border: 1px solid #e1e4ff;
    }

    .kpi-label {
      font-size: 0.8rem;
      color: #555;
    }

    .kpi-value {
      font-size: 1.1rem;
      font-weight: 700;
      margin-top: 3px;
    }

    .kpi-status {
      margin-top: 3px;
      font-size: 0.78rem;
    }

    .scroll-x {
      width: 100%;
      overflow-x: auto;
    }

    #loginError {
      color: #c53030;
      margin-top: 6px;
      min-height: 18px;
    }

    /* สีสถานะ */
    .status-pill {
      display: inline-block;
      padding: 2px 8px;
      border-radius: 999px;
      font-size: 0.78rem;
      font-weight: 600;
    }
    .status-none {
      background: #edf2f7;
      color: #4a5568;
    }
    .status-draft {
      background: #fffaf0;
      color: #b7791f;
    }
    .status-submitted {
      background: #ebf8ff;
      color: #2b6cb0;
    }
    .status-editing {
      background: #f7fafc;
      color: #4a5568;
    }
    .status-ack-deputy {
      background: #c6f6d5;
      color: #22543d;
    }
    .status-ack-director {
      background: #9ae6b4;
      color: #22543d;
    }

    /* แดชบอร์ด */
    .dashboard-card {
      background: #ffffff;
      border-radius: 12px;
      padding: 10px 12px;
      border: 1px solid #dde1ff;
      margin-top: 6px;
    }

    .dashboard-legend {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      font-size: 0.8rem;
      margin-top: 4px;
    }

    .legend-item {
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .legend-color {
      width: 14px;
      height: 14px;
      border-radius: 3px;
    }

    .legend-green { background: #48bb78; }
    .legend-yellow { background: #ecc94b; }
    .legend-red { background: #f56565; }

    .dash-row {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 6px;
      font-size: 0.82rem;
    }

    .dash-dim-name {
      flex: 0 0 120px;
      text-align: left;
    }

    .dash-bar-wrap {
      flex: 1 1 auto;
      background: #edf2f7;
      border-radius: 999px;
      overflow: hidden;
      height: 14px;
    }

    .dash-bar-fill {
      height: 100%;
      border-radius: 999px;
    }

    .dash-bar-green { background: #48bb78; }
    .dash-bar-yellow { background: #ecc94b; }
    .dash-bar-red { background: #f56565; }

    .dash-value {
      flex: 0 0 70px;
      text-align: center;
      font-weight: 600;
    }

    .dash-status-pill {
      flex: 0 0 90px;
      text-align: center;
      font-size: 0.78rem;
      padding: 2px 6px;
      border-radius: 999px;
      color: #fff;
    }

    .dash-status-green { background: #48bb78; }
    .dash-status-yellow { background: #ecc94b; color: #111; }
    .dash-status-red { background: #f56565; }

    @media (max-width: 768px) {
      .app-wrapper {
        padding: 16px 14px 24px;
      }
      h1 {
        font-size: 1.3rem;
      }
      button {
        margin-top: 4px;
      }
      .dash-row {
        flex-wrap: wrap;
      }
      .dash-dim-name {
        flex: 1 1 100%;
      }
    }
  </style>
</head>
<body>
  <!-- หน้าเข้าสู่ระบบ -->
  <div id="loginWrapper" class="app-wrapper">
    <h1 style="text-align:center;">เข้าสู่ระบบ ระบบแปลผลกิจกรรมออนไลน์</h1>
    <p class="subtitle">
      กรุณากรอกชื่อ นามสกุล เลือกบทบาท และรหัสผ่านตัวเลข 6 หลัก เพื่อเข้าใช้งานระบบ
    </p>
    <div class="card" style="max-width: 520px; margin: 0 auto;">
      <h2>เข้าสู่ระบบผู้ใช้งาน</h2>
      <div class="flex">
        <div style="flex:1 1 200px;">
          <label>ชื่อ</label>
          <input id="loginFirstName" type="text" placeholder="เช่น จิ๊บ" />
        </div>
        <div style="flex:1 1 200px;">
          <label>นามสกุล</label>
          <input id="loginLastName" type="text" placeholder="เช่น ใจดี" />
        </div>
      </div>
      <div class="mt-2">
        <label>บทบาท (Role)</label>
        <select id="loginRole">
          <option value="teacher">ครู/ผู้รับผิดชอบกิจกรรม</option>
          <option value="deputy">รองผู้อำนวยการ</option>
          <option value="director">ผู้อำนวยการ</option>
        </select>
      </div>
      <div class="mt-2">
        <label>รหัสผ่าน (ตัวเลข 6 หลัก)</label>
        <input
          id="loginPassword"
          type="password"
          maxlength="6"
          inputmode="numeric"
          placeholder="เช่น 123456"
        />
      </div>
      <div id="loginError" class="small"></div>
      <div class="mt-2" style="text-align:right;">
        <button id="btnLogin" class="primary">
          🔐 เข้าสู่ระบบ
        </button>
      </div>
      <p class="small mt-2">
        * ยังไม่เชื่อมต่อฐานข้อมูลจริง รหัสผ่านใช้เพื่อควบคุมการเข้าหน้าใช้งานในเครื่องนี้เท่านั้น
      </p>
    </div>
  </div>

  <!-- หน้าใช้งานหลัก -->
  <div id="mainWrapper" class="app-wrapper" style="display:none;">
    <!-- ข้อมูลสถานศึกษา -->
    <div class="card">
      <h2>ข้อมูลสถานศึกษา</h2>
      <div class="flex">
        <div style="flex: 1 1 260px;">
          <label>ชื่อสถานศึกษา</label>
          <input id="schoolName" type="text" placeholder="เช่น โรงเรียนเตรียมอุดมศึกษาพัฒนาการ ยานนาเวศ" />
        </div>
        <div style="flex: 1 1 260px;">
          <label>สังกัด</label>
          <input id="affiliation" type="text" placeholder="เช่น สำนักงานเขตพื้นที่การศึกษามัธยมศึกษากรุงเทพมหานคร เขต 2" />
        </div>
      </div>
      <div class="flex mt-2">
        <div style="flex: 1 1 260px;">
          <label>ชื่อรองผู้อำนวยการ</label>
          <input id="deputyName" type="text" placeholder="เช่น นาย.... รองผู้อำนวยการโรงเรียน" />
        </div>
        <div style="flex: 1 1 260px;">
          <label>ชื่อผู้อำนวยการ</label>
          <input id="directorName" type="text" placeholder="เช่น นาย.... ผู้อำนวยการโรงเรียน" />
        </div>
      </div>
    </div>

    <!-- ส่วนหัว + ผู้ใช้ปัจจุบัน -->
    <div class="flex" style="align-items:center; justify-content: space-between; margin-bottom: 8px;">
      <div>
        <h1>ระบบแปลผลการดำเนินกิจกรรมออนไลน์</h1>
        <p class="subtitle" style="text-align:left; margin-top:4px;">
          Fully Automatic Activity Evaluation System (Likert 5 ระดับ) – คำนวณค่าเฉลี่ย แปลผล และสรุปผลกิจกรรมให้อัตโนมัติ 100%
        </p>
      </div>
      <div style="text-align:right;">
        <div class="small">
          ผู้ใช้ที่เข้าสู่ระบบ: <span id="currentUserName">-</span>
        </div>
        <div class="small mt-1">
          บทบาท: <span id="currentUserRole">-</span>
        </div>
        <button id="btnLogout" class="soft mt-1">
          🚪 ออกจากระบบ
        </button>
      </div>
    </div>

    <!-- 1. ตั้งค่ากิจกรรม -->
    <div class="card">
      <h2>1. ตั้งค่ากิจกรรม</h2>
      <div class="flex">
        <div style="flex: 1 1 220px;">
          <label>ชื่อกิจกรรม</label>
          <input id="activityName" type="text" placeholder="เช่น ค่ายเสริมทักษะการเรียนรู้เชิงรุก (Active Learning Camp)" />
        </div>
        <div style="flex: 1 1 140px;">
          <label>ปีการศึกษา</label>
          <input id="academicYear" type="text" placeholder="เช่น 2568" />
        </div>
        <div style="flex: 1 1 140px;">
          <label>ภาคเรียน</label>
          <input id="semester" type="text" placeholder="เช่น 1/2568 หรือ ภาคเรียนที่ 1" />
        </div>
        <div style="flex: 1 1 180px;">
          <label>กลุ่มบริหาร</label>
          <input id="managementGroup" type="text" placeholder="เช่น กลุ่มบริหารวิชาการ" />
        </div>
      </div>
      <div class="flex mt-2">
        <div style="flex: 1 1 220px;">
          <label>ชื่อผู้รับผิดชอบกิจกรรม</label>
          <input id="responsiblePerson" type="text" placeholder="เช่น ครูผู้รับผิดชอบโครงการ" />
        </div>
        <div style="flex: 1 1 160px;">
          <label>จำนวนผู้เข้าร่วมกิจกรรม (คน)</label>
          <input id="numAttendees" type="number" min="0" placeholder="เช่น 120" />
        </div>
        <div style="flex: 1 1 160px;">
          <label>จำนวนผู้ตอบแบบประเมิน (คน)</label>
          <input id="numParticipants" type="number" min="1" value="20" />
        </div>
        <div style="flex: 1 1 160px;">
          <label>งบประมาณ (บาท)</label>
          <input id="budget" type="number" min="0" step="0.01" placeholder="เช่น 5000" />
        </div>
        <div style="flex: 1 1 160px;">
          <label>เกณฑ์ความพึงพอใจผ่าน (ค่าเฉลี่ย)</label>
          <input id="thresholdMean" type="number" step="0.01" value="4.00" />
        </div>
        <div style="flex: 1 1 160px;">
          <label>เกณฑ์ร้อยละผู้ผ่าน (KPI %)</label>
          <input id="thresholdPercent" type="number" step="1" value="80" />
        </div>
      </div>
      <p class="small mt-2">
        หมายเหตุ: ระบบจะใช้เกณฑ์นี้ในการตัดสินว่า “กิจกรรมบรรลุเป้าหมายหรือไม่” โดยเทียบค่าเฉลี่ยภาพรวม และร้อยละผู้ผ่านเกณฑ์
      </p>
    </div>

    <!-- 2. กำหนดรายการข้อประเมิน -->
    <div class="card">
      <h2>2. กำหนดข้อประเมิน (รายการคำถาม)</h2>
      <p class="small">
        ด้านล่างเป็นตัวอย่างข้อประเมิน 10 ข้อ สามารถแก้ไขข้อความ และ "ด้าน" (เช่น เนื้อหา / กระบวนการ / วิทยากร / ผลลัพธ์ ฯลฯ) ได้เอง
      </p>
      <div class="scroll-x">
        <table id="itemsTable">
          <thead>
            <tr>
              <th style="width: 40px;">ข้อ</th>
              <th>ข้อความข้อประเมิน</th>
              <th style="width: 150px;">ด้าน (Dimension)</th>
              <th style="width: 80px;">ค่าเฉลี่ย<br />(1–5)</th>
            </tr>
          </thead>
          <tbody>
            <!-- จะถูกเติมด้วย JS ตอนโหลดหน้า -->
          </tbody>
        </table>
      </div>
      <p class="small mt-2">
        ใส่ค่าเฉลี่ยต่อข้อจาก Google Sheet / แบบประเมิน (ช่วง 1.00 – 5.00) แล้วระบบจะคำนวณแปลผลให้อัตโนมัติ
      </p>
    </div>

    <!-- 3. ป้อนสรุปข้อเสนอแนะ (เชิงคุณภาพ) -->
    <div class="card">
      <h2>3. ข้อเสนอแนะจากผู้เข้าร่วม (เชิงคุณภาพ)</h2>
      <div class="flex">
        <div style="flex: 1 1 260px;">
          <label>จุดเด่นที่พบจากข้อเสนอแนะ (สรุปสั้น ๆ)</label>
          <textarea id="strengths" placeholder="เช่น ผู้เข้าร่วมชื่นชอบกิจกรรมกลุ่ม เกม และการอธิบายที่ชัดเจนของวิทยากร"></textarea>
        </div>
        <div style="flex: 1 1 260px;">
          <label>ข้อเสนอแนะ/สิ่งที่ควรพัฒนา</label>
          <textarea id="improvements" placeholder="เช่น ควรเพิ่มเวลาในการทำกิจกรรมปฏิบัติจริง และตัวอย่างที่ใกล้เคียงสถานการณ์จริงของผู้เรียน"></textarea>
        </div>
      </div>
    </div>

    <!-- 4. ปุ่มประมวลผล + ดาวน์โหลด DOC -->
    <div class="card">
      <div class="flex" style="align-items: center; justify-content: space-between; gap: 10px;">
        <div>
          <h2 style="margin-bottom: 4px;">4. ประมวลผล & แปลผลอัตโนมัติ</h2>
          <p class="small" style="margin: 0;">
            เมื่อกรอกข้อมูลครบแล้ว กดปุ่ม “ประมวลผล” ระบบจะสรุปเป็นตัวเลข และข้อความสรุปกิจกรรมให้อัตโนมัติทันที
          </p>
        </div>
        <div class="flex" style="justify-content: flex-end;">
          <button id="btnCalculate" class="primary">
            ⚙️ ประมวลผลอัตโนมัติ
          </button>
          <button id="btnDownloadDoc" class="secondary">
            ⬇️ ดาวน์โหลด .DOC
          </button>
        </div>
      </div>
    </div>

    <!-- 5. การส่งรายงาน & ติดตามสถานะ -->
    <div class="card">
      <h2>5. การส่งรายงานและติดตามสถานะ</h2>
      <p class="small">
        ปุ่มด้านล่างนี้เป็นระบบจัดการฉบับร่าง–ส่งรายงาน–แก้ไข และกดรับทราบ (สำหรับผู้บริหาร) โดยข้อมูลจะถูกเก็บในเบราว์เซอร์เครื่องที่ใช้งาน
      </p>
      <div class="flex mt-1" style="align-items: center; gap: 8px;">
        <button id="btnSaveDraft" class="soft">
          💾 บันทึกข้อมูล (ฉบับร่าง)
        </button>
        <button id="btnSubmitReport" class="secondary">
          📤 ส่งรายงานให้ผู้บริหาร
        </button>
        <button id="btnEditUnlock" class="secondary">
          ✏️ แก้ไขข้อมูล
        </button>
        <button id="btnAcknowledgeDeputy" class="soft">
          ✅ รองผู้อำนวยการ: กดรับทราบรายงาน
        </button>
        <button id="btnAcknowledgeDirector" class="soft">
          ✅ ผู้อำนวยการ: กดรับทราบรายงาน
        </button>
      </div>

      <div id="statusArea" class="result-box mt-2">
        <div class="result-title">สถานะการส่งรายงาน</div>
        <div id="statusText" class="result-text small">
          ยังไม่เคยบันทึกข้อมูลหรือส่งรายงาน
        </div>
      </div>
      <p class="small mt-1">
        * เงื่อนไข: ผู้อำนวยการจะกดปุ่มรับทราบได้ก็ต่อเมื่อ “รองผู้อำนวยการ” รับทราบแล้ว
      </p>
    </div>

    <!-- 6. ผลลัพธ์เชิงสถิติ -->
    <div class="card">
      <h2>6. ผลการประเมินเชิงสถิติ</h2>
      <div id="statsContainer" class="mt-2">
        <!-- จะสร้างด้วย JS -->
      </div>
    </div>

    <!-- 7. สรุปผลข้อความ -->
    <div class="card">
      <h2>7. สรุปผลในภาพรวม (ข้อความพร้อมใช้รายงาน/โครงการ)</h2>
      <div id="summaryContainer" class="result-box">
        <div class="result-title">สรุปผลภาพรวมของกิจกรรม</div>
        <div id="summaryText" class="result-text">
          (ยังไม่ได้ประมวลผล – กรุณากรอกข้อมูล แล้วกดปุ่ม "ประมวลผลอัตโนมัติ")
        </div>
      </div>

      <div class="result-box mt-3">
        <div class="result-title">ข้อเสนอแนะเชิงนโยบาย/การบริหารต่อยอด</div>
        <div id="policyText" class="result-text">
          (จะสร้างข้อความข้อเสนอแนะเชิงนโยบายอัตโนมัติหลังประมวลผล)
        </div>
      </div>
    </div>

    <!-- 8. แดชบอร์ดสรุปผล -->
    <div class="card">
      <h2>8. แดชบอร์ดสรุปผล (Dashboard Summary)</h2>
      <p class="small">
        แสดงผลการประเมินรายด้านในรูปแบบกราฟ/ตารางสรุป<br>
        🟢 สีเขียว = บรรลุ | 🟡 สีเหลือง = ควรพัฒนา | 🔴 สีแดง = ต้องรีบปรับปรุง<br>
        (อ้างอิงจากค่าเฉลี่ยเทียบกับเกณฑ์ที่กำหนดในช่อง “เกณฑ์ความพึงพอใจผ่าน (ค่าเฉลี่ย)”)
      </p>
      <div id="dashboardContainer" class="mt-2"></div>
    </div>
  </div>

  <script>
    // ---------- CONFIG ----------
    const STORAGE_KEY = "activityEvalDraftV1";
    const STATUS_KEY = "activityEvalStatusV1";
    const USER_KEY   = "activityEvalCurrentUserV1";

    const defaultItems = [
      { text: "กิจกรรมมีเนื้อหาสอดคล้องกับวัตถุประสงค์ที่กำหนด", dimension: "เนื้อหา" },
      { text: "เนื้อหาที่จัดกิจกรรมมีความทันสมัยและเชื่อมโยงกับชีวิตจริง", dimension: "เนื้อหา" },
      { text: "รูปแบบกิจกรรมเปิดโอกาสให้ผู้เข้าร่วมมีส่วนร่วมอย่างเหมาะสม", dimension: "กระบวนการ" },
      { text: "เวลาในการดำเนินกิจกรรมมีความเหมาะสม", dimension: "กระบวนการ" },
      { text: "วิทยากร/ครูผู้สอนอธิบายได้ชัดเจน เข้าใจง่าย", dimension: "วิทยากร" },
      { text: "วิทยากร/ครูผู้สอนส่งเสริมให้ผู้เข้าร่วมกล้าคิด กล้าแสดงความคิดเห็น", dimension: "วิทยากร" },
      { text: "กิจกรรมช่วยให้ผู้เข้าร่วมเกิดทักษะหรือความรู้ใหม่ ๆ", dimension: "ผลลัพธ์" },
      { text: "ผู้เข้าร่วมสามารถนำความรู้จากกิจกรรมไปประยุกต์ใช้ได้จริง", dimension: "ผลลัพธ์" },
      { text: "บรรยากาศและสภาพแวดล้อมในการจัดกิจกรรมเอื้อต่อการเรียนรู้", dimension: "บรรยากาศ" },
      { text: "โดยภาพรวม ผู้เข้าร่วมมีความพึงพอใจต่อกิจกรรมครั้งนี้", dimension: "ภาพรวม" }
    ];

    const itemsTableBody = document.querySelector("#itemsTable tbody");
    let hasResult = false;

    // ---------- USER ----------
    function getCurrentUser() {
      const raw = localStorage.getItem(USER_KEY);
      if (!raw) return null;
      try { return JSON.parse(raw); } catch { return null; }
    }
    function setCurrentUser(firstName, lastName, role) {
      const user = { firstName, lastName, role };
      localStorage.setItem(USER_KEY, JSON.stringify(user));
    }
    function clearCurrentUser() {
      localStorage.removeItem(USER_KEY);
    }
    function roleLabel(role) {
      if (role === "deputy") return "รองผู้อำนวยการ";
      if (role === "director") return "ผู้อำนวยการ";
      return "ครู/ผู้รับผิดชอบกิจกรรม";
    }

    // ---------- สร้างตารางข้อประเมิน ----------
    function renderItemsTable() {
      itemsTableBody.innerHTML = "";
      defaultItems.forEach((item, index) => {
        const tr = document.createElement("tr");

        const tdNo = document.createElement("td");
        tdNo.textContent = index + 1;

        const tdText = document.createElement("td");
        const inputText = document.createElement("input");
        inputText.type = "text";
        inputText.value = item.text;
        inputText.dataset.role = "itemText";
        inputText.dataset.index = index;
        tdText.appendChild(inputText);

        const tdDim = document.createElement("td");
        const inputDim = document.createElement("input");
        inputDim.type = "text";
        inputDim.value = item.dimension;
        inputDim.dataset.role = "itemDim";
        inputDim.dataset.index = index;
        tdDim.appendChild(inputDim);

        const tdMean = document.createElement("td");
        const inputMean = document.createElement("input");
        inputMean.type = "number";
        inputMean.step = "0.01";
        inputMean.min = "1";
        inputMean.max = "5";
        inputMean.placeholder = "เช่น 4.35";
        inputMean.dataset.role = "itemMean";
        inputMean.dataset.index = index;
        tdMean.appendChild(inputMean);

        tr.appendChild(tdNo);
        tr.appendChild(tdText);
        tr.appendChild(tdDim);
        tr.appendChild(tdMean);
        itemsTableBody.appendChild(tr);
      });
    }

    function interpretLikert(mean) {
      if (mean >= 4.51) return "มากที่สุด";
      if (mean >= 3.51) return "มาก";
      if (mean >= 2.51) return "ปานกลาง";
      if (mean >= 1.51) return "น้อย";
      return "น้อยที่สุด";
    }

    // สำหรับคำนวณ dimension ใช้กับทั้ง dashboard และ doc
    function computeDimensionStats() {
      const itemInputs = document.querySelectorAll("input[data-role='itemText']");
      const dimInputs = document.querySelectorAll("input[data-role='itemDim']");
      const meanInputs = document.querySelectorAll("input[data-role='itemMean']");

      const dimMap = {};
      let sumAllMeans = 0;
      let countMeans = 0;

      for (let i = 0; i < itemInputs.length; i++) {
        const dim = (dimInputs[i].value.trim() || "ไม่ระบุด้าน");
        const meanVal = parseFloat(meanInputs[i].value);
        if (!isNaN(meanVal)) {
          if (!dimMap[dim]) dimMap[dim] = { sum: 0, count: 0 };
          dimMap[dim].sum += meanVal;
          dimMap[dim].count += 1;

          sumAllMeans += meanVal;
          countMeans++;
        }
      }

      const dims = Object.keys(dimMap).map(dim => {
        const mean = dimMap[dim].sum / dimMap[dim].count;
        return {
          name: dim,
          mean,
          level: interpretLikert(mean)
        };
      });

      return {
        dims,
        overallMean: countMeans ? sumAllMeans / countMeans : null,
        countMeans
      };
    }

    // จัดกลุ่มสีแดชบอร์ด
    function classifyStatus(value, thresholdMean) {
      // กำหนดคร่าว ๆ: >= เกณฑ์ = เขียว, >= เกณฑ์-0.5 = เหลือง, น้อยกว่านั้น = แดง
      if (value >= thresholdMean) {
        return { color: "green", text: "บรรลุ" };
      } else if (value >= thresholdMean - 0.5) {
        return { color: "yellow", text: "ควรพัฒนา" };
      } else {
        return { color: "red", text: "ต้องรีบปรับปรุง" };
      }
    }

    // ---------- คำนวณและแปลผล ----------
    function calculateAndRender() {
      const schoolName = document.getElementById("schoolName").value.trim();
      const affiliation = document.getElementById("affiliation").value.trim();

      const activityName = document.getElementById("activityName").value.trim() || "กิจกรรมครั้งนี้";
      const academicYear = document.getElementById("academicYear").value.trim();
      const semester = document.getElementById("semester").value.trim();
      const managementGroup = document.getElementById("managementGroup").value.trim();
      const responsiblePerson = document.getElementById("responsiblePerson").value.trim();

      const numAttendees = parseFloat(document.getElementById("numAttendees").value) || 0;
      const numParticipants = parseFloat(document.getElementById("numParticipants").value) || 0;
      const budgetValue = document.getElementById("budget").value.trim();

      const thresholdMean = parseFloat(document.getElementById("thresholdMean").value) || 4.0;
      const thresholdPercent = parseFloat(document.getElementById("thresholdPercent").value) || 80;

      const strengths = document.getElementById("strengths").value.trim();
      const improvements = document.getElementById("improvements").value.trim();

      const itemInputs = document.querySelectorAll("input[data-role='itemText']");
      const dimInputs = document.querySelectorAll("input[data-role='itemDim']");
      const meanInputs = document.querySelectorAll("input[data-role='itemMean']");

      const items = [];
      let sumAllMeans = 0;
      let countMeans = 0;
      const dimMap = {};

      for (let i = 0; i < itemInputs.length; i++) {
        const text = itemInputs[i].value.trim() || `ข้อที่ ${i + 1}`;
        const dim = dimInputs[i].value.trim() || "ไม่ระบุด้าน";
        const meanVal = parseFloat(meanInputs[i].value);

        if (!isNaN(meanVal)) {
          items.push({
            index: i + 1,
            text,
            dimension: dim,
            mean: meanVal,
            level: interpretLikert(meanVal)
          });

          sumAllMeans += meanVal;
          countMeans++;

          if (!dimMap[dim]) {
            dimMap[dim] = { sum: 0, count: 0 };
          }
          dimMap[dim].sum += meanVal;
          dimMap[dim].count += 1;
        }
      }

      const statsContainer = document.getElementById("statsContainer");
      const summaryTextEl = document.getElementById("summaryText");
      const policyTextEl = document.getElementById("policyText");
      const dashboardContainer = document.getElementById("dashboardContainer");

      if (items.length === 0) {
        statsContainer.innerHTML = `<p class="small">ยังไม่ได้กรอกค่าเฉลี่ยของข้อประเมินใด ๆ กรุณากรอกอย่างน้อย 1 ข้อ</p>`;
        summaryTextEl.textContent = "ยังไม่สามารถสรุปผลได้เนื่องจากไม่มีข้อมูลค่าเฉลี่ยของข้อประเมิน";
        policyTextEl.textContent = "โปรดกรอกข้อมูลการประเมินให้ครบถ้วนก่อน เพื่อให้ระบบสามารถสรุปข้อเสนอแนะเชิงนโยบายได้อย่างเหมาะสม";
        dashboardContainer.innerHTML = `<p class="small">ไม่มีข้อมูลสำหรับสร้างแดชบอร์ด กรุณากรอกค่าเฉลี่ยข้อประเมินก่อน</p>`;
        hasResult = false;
        return;
      }

      const overallMean = sumAllMeans / countMeans;
      const estimatedPercentPass = overallMean >= thresholdMean ? 100 : 60;
      const overallLevel = interpretLikert(overallMean);
      const overallPassKPI =
        overallMean >= thresholdMean && estimatedPercentPass >= thresholdPercent;

      // การ์ด KPI
      let dimHtml = `
        <div class="kpi-row">
          <div class="kpi-card">
            <div class="kpi-label">ค่าเฉลี่ยภาพรวม</div>
            <div class="kpi-value">${overallMean.toFixed(2)}</div>
            <div class="kpi-status">
              ระดับ: <span class="badge ${overallMean >= thresholdMean ? "green" : "yellow"}">${overallLevel}</span>
            </div>
          </div>
          <div class="kpi-card">
            <div class="kpi-label">จำนวนข้อประเมินที่ใช้</div>
            <div class="kpi-value">${countMeans} ข้อ</div>
            <div class="kpi-status small">จากทั้งหมด ${itemInputs.length} ข้อ</div>
          </div>
          <div class="kpi-card">
            <div class="kpi-label">ประมาณการร้อยละผู้ผ่านเกณฑ์</div>
            <div class="kpi-value">${estimatedPercentPass.toFixed(0)}%</div>
            <div class="kpi-status">
              เกณฑ์ที่ตั้งไว้ ≥ ${thresholdPercent.toFixed(0)}%
            </div>
          </div>
          <div class="kpi-card">
            <div class="kpi-label">สรุปการบรรลุเป้าหมายของกิจกรรม</div>
            <div class="kpi-status">
              ${
                overallPassKPI
                  ? '<span class="badge green">บรรลุตามตัวชี้วัด</span>'
                  : '<span class="badge red">ยังไม่บรรลุตามตัวชี้วัด</span>'
              }
            </div>
          </div>
        </div>
      `;

      // ตารางค่าเฉลี่ยตามด้าน
      let dimTable = `
        <div class="mt-3">
          <div class="small"><b>สรุปค่าเฉลี่ยตามด้าน (Dimension)</b></div>
          <div class="scroll-x mt-1">
            <table>
              <thead>
                <tr>
                  <th>ด้าน</th>
                  <th>ค่าเฉลี่ย</th>
                  <th>ระดับ</th>
                </tr>
              </thead>
              <tbody>
      `;

      Object.keys(dimMap).forEach((dim) => {
        const dMean = dimMap[dim].sum / dimMap[dim].count;
        dimTable += `
          <tr>
            <td>${dim}</td>
            <td>${dMean.toFixed(2)}</td>
            <td>${interpretLikert(dMean)}</td>
          </tr>
        `;
      });

      dimTable += `
              </tbody>
            </table>
          </div>
        </div>
      `;

      // ตารางค่าเฉลี่ยรายข้อ
      let itemTable = `
        <div class="mt-3">
          <div class="small"><b>ค่าเฉลี่ยรายข้อประเมิน</b></div>
          <div class="scroll-x mt-1">
            <table>
              <thead>
                <tr>
                  <th style="width: 40px;">ข้อ</th>
                  <th>ข้อความข้อประเมิน</th>
                  <th style="width: 120px;">ด้าน</th>
                  <th style="width: 80px;">ค่าเฉลี่ย</th>
                  <th style="width: 80px;">ระดับ</th>
                </tr>
              </thead>
              <tbody>
      `;

      items.forEach((item) => {
        itemTable += `
          <tr>
            <td>${item.index}</td>
            <td style="text-align: left;">${item.text}</td>
            <td>${item.dimension}</td>
            <td>${item.mean.toFixed(2)}</td>
            <td>${item.level}</td>
          </tr>
        `;
      });

      itemTable += `
              </tbody>
            </table>
          </div>
        </div>
      `;

      statsContainer.innerHTML = dimHtml + dimTable + itemTable;

      // ---------- ข้อความสรุป ----------
      const nameForText = activityName || "กิจกรรมดังกล่าว";
      let summaryText = "";

      if (schoolName || affiliation) {
        summaryText += `การประเมินผลการดำเนินกิจกรรมของ`;
        if (schoolName) summaryText += `${schoolName} `;
        if (affiliation) summaryText += `สังกัด ${affiliation} `;
        summaryText += `\n\n`;
      }

      summaryText += `${nameForText}`;
      if (semester || academicYear) {
        summaryText += ` จัดในภาคเรียน/ปีการศึกษา `;
        if (semester) summaryText += `${semester} `;
        if (academicYear) summaryText += `ปีการศึกษา ${academicYear} `;
      }
      if (managementGroup) {
        summaryText += `ภายใต้การกำกับดูแลของ${managementGroup} `;
      }
      if (responsiblePerson) {
        summaryText += `โดยมีผู้รับผิดชอบกิจกรรมคือ ${responsiblePerson} `;
      }

      if (numAttendees > 0 && numParticipants > 0) {
        summaryText += `มีผู้เข้าร่วมกิจกรรมทั้งหมด ${numAttendees} คน และมีผู้ตอบแบบประเมินจำนวนประมาณ ${numParticipants} คน `;
      } else if (numAttendees > 0) {
        summaryText += `มีผู้เข้าร่วมกิจกรรมทั้งหมดประมาณ ${numAttendees} คน `;
      } else if (numParticipants > 0) {
        summaryText += `มีผู้ตอบแบบประเมินจำนวนประมาณ ${numParticipants} คน `;
      }

      if (budgetValue) {
        summaryText += `ใช้งบประมาณดำเนินกิจกรรมทั้งสิ้นประมาณ ${budgetValue} บาท `;
      }

      summaryText += `ผลการประเมินภาพรวมมีค่าเฉลี่ยเท่ากับ ${overallMean.toFixed(2)} อยู่ในระดับ“${overallLevel}” `;
      summaryText += `โดยจากการตีความตามเกณฑ์ที่กำหนด (${thresholdMean.toFixed(2)} ขึ้นไปถือว่า “ผ่านเกณฑ์”) `;
      summaryText += `พบว่ากิจกรรม ${
        overallMean >= thresholdMean
          ? "มีแนวโน้มบรรลุเป้าหมายด้านความพึงพอใจของผู้เข้าร่วม"
          : "ยังมีบางประเด็นที่ควรปรับปรุงเพิ่มเติมเพื่อให้บรรลุเป้าหมายด้านความพึงพอใจของผู้เข้าร่วม"
      }\n\n`;

      summaryText += `เมื่อพิจารณาเป็นรายด้าน พบว่า\n`;
      Object.keys(dimMap).forEach((dim) => {
        const dMean = dimMap[dim].sum / dimMap[dim].count;
        const dLevel = interpretLikert(dMean);
        summaryText += `• ด้าน${dim} มีค่าเฉลี่ย ${dMean.toFixed(2)} อยู่ในระดับ“${dLevel}”\n`;
      });

      summaryText += `\nประมาณการร้อยละของผู้เข้าร่วมที่ผ่านเกณฑ์ความพึงพอใจ (ค่าเฉลี่ยไม่ต่ำกว่า ${thresholdMean.toFixed(2)}) อยู่ที่ประมาณ ${estimatedPercentPass.toFixed(0)}% `;
      summaryText += `ซึ่งเทียบกับเกณฑ์ตัวชี้วัดที่กำหนดไว้ไม่ต่ำกว่า ${thresholdPercent.toFixed(0)}% แล้วถือว่า `;
      summaryText += overallPassKPI
        ? "กิจกรรมครั้งนี้บรรลุเป้าหมายตามตัวชี้วัดที่กำหนด"
        : "กิจกรรมครั้งนี้ยังไม่บรรลุตามตัวชี้วัดที่กำหนดอย่างเต็มที่ และควรมีการออกแบบกิจกรรม/ปรับกลยุทธ์เพิ่มเติมในครั้งถัดไป";

      summaryTextEl.textContent = summaryText;

      // ---------- ข้อเสนอแนะเชิงนโยบาย ----------
      let policyText = "";

      if (strengths) {
        policyText += `1) จุดเด่นของการดำเนินกิจกรรม\n`;
        policyText += `จากการวิเคราะห์ข้อเสนอแนะของผู้เข้าร่วม พบว่า จุดเด่นสำคัญของกิจกรรม ได้แก่ ${strengths}\n\n`;
      } else {
        policyText += `1) จุดเด่นของการดำเนินกิจกรรม\n`;
        policyText += `ผู้เข้าร่วมส่วนใหญ่สะท้อนว่ากิจกรรมมีความน่าสนใจ และเอื้อต่อการเรียนรู้ในภาพรวม\n\n`;
      }

      if (improvements) {
        policyText += `2) ข้อเสนอแนะและประเด็นที่ควรพัฒนา\n`;
        policyText += `ผู้เข้าร่วมเสนอให้มีการปรับปรุง/เพิ่มเติมในประเด็นต่อไปนี้ ได้แก่ ${improvements}\n\n`;
      } else {
        policyText += `2) ข้อเสนอแนะและประเด็นที่ควรพัฒนา\n`;
        policyText += `ควรสำรวจความต้องการเชิงลึกของผู้เข้าร่วมเพิ่มเติม เพื่อนำมาปรับกิจกรรมให้ตอบโจทย์มากขึ้น เช่น การเพิ่มเวลาในการทำกิจกรรม การยกตัวอย่างกรณีศึกษา และการติดตามผลหลังจบกิจกรรม\n\n`;
      }

      policyText += `3) ข้อเสนอแนะเชิงนโยบาย/การบริหารจัดการต่อไป\n`;
      policyText += `เพื่อยกระดับคุณภาพของ${nameForText} ในครั้งถัดไป เสนอให้\n`;
      policyText += `• นำข้อมูลเชิงสถิติและข้อเสนอแนะเชิงคุณภาพครั้งนี้ ไปใช้ในการปรับปรุงรูปแบบกิจกรรม เนื้อหา และวิธีการจัดการเรียนรู้\n`;
      policyText += `• กำหนดตัวชี้วัดที่สะท้อนผลลัพธ์ผู้เรียน/ผู้เข้าร่วมอย่างชัดเจน เช่น การติดตามการนำความรู้ไปใช้จริงในระยะ 1–3 เดือนหลังจบกิจกรรม\n`;
      policyText += `• ส่งเสริมให้ครู/วิทยากรพัฒนาทักษะด้านการจัดกิจกรรมเชิงรุกและการใช้สื่อดิจิทัล เพื่อเพิ่มความน่าสนใจและประสิทธิภาพในการเรียนรู้ของผู้เข้าร่วม`;

      policyTextEl.textContent = policyText;

      // ---------- แดชบอร์ดสรุปผล ----------
      const dimStats = computeDimensionStats();
      const dims = dimStats.dims || [];

      if (!dims.length) {
        dashboardContainer.innerHTML = `<p class="small">ไม่มีข้อมูลรายด้านสำหรับสร้างแดชบอร์ด</p>`;
      } else {
        let dashHtml = `
          <div class="dashboard-card">
            <div class="small"><b>ภาพรวมสถานะตามด้าน (Dimension)</b></div>
            <div class="dashboard-legend mt-1">
              <div class="legend-item"><span class="legend-color legend-green"></span> บรรลุ</div>
              <div class="legend-item"><span class="legend-color legend-yellow"></span> ควรพัฒนา</div>
              <div class="legend-item"><span class="legend-color legend-red"></span> ต้องรีบปรับปรุง</div>
            </div>
            <div class="mt-2">
        `;

        dims.forEach(d => {
          const status = classifyStatus(d.mean, thresholdMean);
          const barWidth = Math.max(0, Math.min(100, (d.mean / 5) * 100));
          const barColorClass =
            status.color === "green"
              ? "dash-bar-green"
              : status.color === "yellow"
              ? "dash-bar-yellow"
              : "dash-bar-red";
          const pillClass =
            status.color === "green"
              ? "dash-status-green"
              : status.color === "yellow"
              ? "dash-status-yellow"
              : "dash-status-red";

          dashHtml += `
            <div class="dash-row">
              <div class="dash-dim-name">${d.name}</div>
              <div class="dash-bar-wrap">
                <div class="dash-bar-fill ${barColorClass}" style="width:${barWidth.toFixed(0)}%;"></div>
              </div>
              <div class="dash-value">${d.mean.toFixed(2)}</div>
              <div class="dash-status-pill ${pillClass}">${status.text}</div>
            </div>
          `;
        });

        dashHtml += `
            </div>
          </div>
        `;

        // ตารางสรุปรายด้านในแดชบอร์ด
        dashHtml += `
          <div class="dashboard-card mt-2">
            <div class="small"><b>ตารางสรุปสถานะรายด้าน</b></div>
            <div class="scroll-x mt-1">
              <table>
                <thead>
                  <tr>
                    <th>ด้าน</th>
                    <th>ค่าเฉลี่ย</th>
                    <th>ระดับ (Likert)</th>
                    <th>สถานะ</th>
                  </tr>
                </thead>
                <tbody>
        `;
        dims.forEach(d => {
          const status = classifyStatus(d.mean, thresholdMean);
          const statusText = status.text;
          let statusColor = "#48bb78";
          if (status.color === "yellow") statusColor = "#ecc94b";
          if (status.color === "red") statusColor = "#f56565";

          dashHtml += `
            <tr>
              <td>${d.name}</td>
              <td>${d.mean.toFixed(2)}</td>
              <td>${d.level}</td>
              <td style="font-weight:600; color:${statusColor};">${statusText}</td>
            </tr>
          `;
        });

        dashHtml += `
                </tbody>
              </table>
            </div>
          </div>
        `;

        dashboardContainer.innerHTML = dashHtml;
      }

      hasResult = true;
    }

    // ---------- ลายเซ็นสำหรับ .doc ----------
    function buildSignatureBlockForDoc() {
      const user = getCurrentUser() || {};
      const reporterName = `${user.firstName || ""} ${user.lastName || ""}`.trim();
      const deputyName = (document.getElementById("deputyName").value || "").trim();
      const directorName = (document.getElementById("directorName").value || "").trim();

      const reporterLine = reporterName || "........................................................";
      const deputyLine   = deputyName   || "........................................................";
      const directorLine = directorName || "........................................................";

      const sigHtml = `
        <h2>ลายเซ็นผู้เกี่ยวข้อง</h2>
        <p style="margin-top:18pt;">
          ลงชื่อ........................................................ ผู้รายงาน<br>
          (${reporterLine})<br>
          ตำแหน่ง: ${roleLabel(user.role || "teacher")}
        </p>
        <p style="margin-top:18pt;">
          ลงชื่อ........................................................ รองผู้อำนวยการ<br>
          (${deputyLine})
        </p>
        <p style="margin-top:18pt;">
          ลงชื่อ........................................................ ผู้อำนวยการ<br>
          (${directorLine})
        </p>
      `;
      return sigHtml;
    }

    // ---------- สถานะ + localStorage ----------
    function getStatusObj() {
      const raw = localStorage.getItem(STATUS_KEY);
      if (!raw) return { current: "none", isLocked: false, history: [] };
      try {
        return JSON.parse(raw);
      } catch {
        return { current: "none", isLocked: false, history: [] };
      }
    }

    function saveStatusObj(obj) {
      localStorage.setItem(STATUS_KEY, JSON.stringify(obj));
    }

    function statusLabel(code) {
      switch (code) {
        case "draft":
          return "ฉบับร่าง (ยังไม่ส่งผู้บริหาร)";
        case "submitted":
          return "ส่งให้ผู้บริหารแล้ว (รอการรับทราบ)";
        case "editing":
          return "อยู่ระหว่างแก้ไขข้อมูล";
        case "ack_deputy":
          return "รองผู้อำนวยการรับทราบแล้ว";
        case "ack_director":
          return "ผู้อำนวยการรับทราบแล้ว";
        default:
          return "ยังไม่เคยบันทึกข้อมูลหรือส่งรายงาน";
      }
    }

    function statusClass(code) {
      switch (code) {
        case "draft": return "status-draft";
        case "submitted": return "status-submitted";
        case "editing": return "status-editing";
        case "ack_deputy": return "status-ack-deputy";
        case "ack_director": return "status-ack-director";
        default: return "status-none";
      }
    }

    function renderStatus() {
      const statusArea = document.getElementById("statusText");
      const statusObj = getStatusObj();

      if (!statusObj.history || statusObj.history.length === 0 || statusObj.current === "none") {
        statusArea.textContent = "ยังไม่เคยบันทึกข้อมูลหรือส่งรายงาน";
        return;
      }

      let html = `สถานะปัจจุบัน: <span class="status-pill ${statusClass(statusObj.current)}">${statusLabel(statusObj.current)}</span><br><br>ไทม์ไลน์การดำเนินการ:<br>`;
      statusObj.history.forEach((h) => {
        html += `• [${h.time}] <span class="status-pill ${statusClass(h.status)}">${statusLabel(h.status)}</span>${h.note ? " – " + h.note : ""}<br>`;
      });

      statusArea.innerHTML = html;
    }

    function setFormDisabled(disabled) {
      const selectors = "input[type='text'], input[type='number'], textarea, #btnCalculate";
      document.querySelectorAll(selectors).forEach((el) => {
        el.disabled = disabled;
      });
    }

    function applyRolePermissions() {
      const user = getCurrentUser() || {};
      const role = user.role || "teacher";
      const st = getStatusObj();

      const btnSaveDraft = document.getElementById("btnSaveDraft");
      const btnSubmitReport = document.getElementById("btnSubmitReport");
      const btnEditUnlock = document.getElementById("btnEditUnlock");
      const btnAcknowledgeDeputy = document.getElementById("btnAcknowledgeDeputy");
      const btnAcknowledgeDirector = document.getElementById("btnAcknowledgeDirector");

      // ฟอร์ม: ครูแก้ได้, ผู้บริหารอ่านอย่างเดียว
      const shouldLockInputs = st.isLocked || role !== "teacher";
      setFormDisabled(shouldLockInputs);

      // ค่า default
      btnAcknowledgeDeputy.disabled = false;
      btnAcknowledgeDirector.disabled = false;

      if (role === "teacher") {
        btnSaveDraft.style.display = "inline-flex";
        btnSubmitReport.style.display = "inline-flex";
        btnEditUnlock.style.display = "inline-flex";
        btnAcknowledgeDeputy.style.display = "none";
        btnAcknowledgeDirector.style.display = "none";
      } else if (role === "deputy") {
        btnSaveDraft.style.display = "none";
        btnSubmitReport.style.display = "none";
        btnEditUnlock.style.display = "none";
        btnAcknowledgeDeputy.style.display = "inline-flex";
        btnAcknowledgeDirector.style.display = "none";
      } else if (role === "director") {
        btnSaveDraft.style.display = "none";
        btnSubmitReport.style.display = "none";
        btnEditUnlock.style.display = "none";
        btnAcknowledgeDeputy.style.display = "none";
        btnAcknowledgeDirector.style.display = "inline-flex";

        // เงื่อนไข: ผอ. กดได้เมื่อสถานะปัจจุบันคือ ack_deputy หรือเคย ack_director แล้ว
        if (st.current !== "ack_deputy" && st.current !== "ack_director") {
          btnAcknowledgeDirector.disabled = true;
          btnAcknowledgeDirector.title = "รองผู้อำนวยการต้องกดรับทราบก่อน";
        } else {
          btnAcknowledgeDirector.disabled = false;
          btnAcknowledgeDirector.title = "";
        }
      }
    }

    function updateStatus(newStatus, note, lockForm) {
      const statusObj = getStatusObj();
      const time = new Date().toLocaleString("th-TH");
      if (!statusObj.history) statusObj.history = [];
      statusObj.history.push({ status: newStatus, time, note: note || "" });
      statusObj.current = newStatus;
      statusObj.isLocked = !!lockForm;
      saveStatusObj(statusObj);
      renderStatus();
      applyRolePermissions();
    }

    function collectItemsForSave() {
      const itemInputs = document.querySelectorAll("input[data-role='itemText']");
      const dimInputs = document.querySelectorAll("input[data-role='itemDim']");
      const meanInputs = document.querySelectorAll("input[data-role='itemMean']");
      const items = [];
      for (let i = 0; i < itemInputs.length; i++) {
        items.push({
          text: itemInputs[i].value,
          dimension: dimInputs[i].value,
          mean: meanInputs[i].value
        });
      }
      return items;
    }

    function saveDraft() {
      const data = {
        schoolName: document.getElementById("schoolName").value,
        affiliation: document.getElementById("affiliation").value,
        deputyName: document.getElementById("deputyName").value,
        directorName: document.getElementById("directorName").value,
        activityName: document.getElementById("activityName").value,
        academicYear: document.getElementById("academicYear").value,
        semester: document.getElementById("semester").value,
        managementGroup: document.getElementById("managementGroup").value,
        responsiblePerson: document.getElementById("responsiblePerson").value,
        numAttendees: document.getElementById("numAttendees").value,
        numParticipants: document.getElementById("numParticipants").value,
        budget: document.getElementById("budget").value,
        thresholdMean: document.getElementById("thresholdMean").value,
        thresholdPercent: document.getElementById("thresholdPercent").value,
        strengths: document.getElementById("strengths").value,
        improvements: document.getElementById("improvements").value,
        items: collectItemsForSave(),
        summaryText: document.getElementById("summaryText").innerText,
        policyText: document.getElementById("policyText").innerText,
        statsHtml: document.getElementById("statsContainer").innerHTML,
        dashboardHtml: document.getElementById("dashboardContainer").innerHTML,
        hasResult: hasResult
      };

      localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
      updateStatus("draft", "บันทึกร่างข้อมูลล่าสุด", false);
      alert("บันทึกข้อมูลฉบับร่างเรียบร้อย (เก็บไว้ในเบราว์เซอร์เครื่องนี้)");
    }

    function loadDraft() {
      const raw = localStorage.getItem(STORAGE_KEY);
      if (!raw) {
        renderStatus();
        applyRolePermissions();
        return;
      }
      try {
        const data = JSON.parse(raw);
        document.getElementById("schoolName").value = data.schoolName || "";
        document.getElementById("affiliation").value = data.affiliation || "";
        document.getElementById("deputyName").value = data.deputyName || "";
        document.getElementById("directorName").value = data.directorName || "";
        document.getElementById("activityName").value = data.activityName || "";
        document.getElementById("academicYear").value = data.academicYear || "";
        document.getElementById("semester").value = data.semester || "";
        document.getElementById("managementGroup").value = data.managementGroup || "";
        document.getElementById("responsiblePerson").value = data.responsiblePerson || "";
        document.getElementById("numAttendees").value = data.numAttendees || "";
        document.getElementById("numParticipants").value = data.numParticipants || "";
        document.getElementById("budget").value = data.budget || "";
        document.getElementById("thresholdMean").value = data.thresholdMean || "4.00";
        document.getElementById("thresholdPercent").value = data.thresholdPercent || "80";
        document.getElementById("strengths").value = data.strengths || "";
        document.getElementById("improvements").value = data.improvements || "";

        if (data.items && data.items.length) {
          const itemInputs = document.querySelectorAll("input[data-role='itemText']");
          const dimInputs = document.querySelectorAll("input[data-role='itemDim']");
          const meanInputs = document.querySelectorAll("input[data-role='itemMean']");
          for (let i = 0; i < itemInputs.length && i < data.items.length; i++) {
            const it = data.items[i];
            itemInputs[i].value = it.text || "";
            dimInputs[i].value = it.dimension || "";
            meanInputs[i].value = it.mean || "";
          }
        }

        if (data.statsHtml) {
          document.getElementById("statsContainer").innerHTML = data.statsHtml;
        }
        if (data.dashboardHtml) {
          document.getElementById("dashboardContainer").innerHTML = data.dashboardHtml;
        }
        if (data.summaryText) {
          document.getElementById("summaryText").innerText = data.summaryText;
        }
        if (data.policyText) {
          document.getElementById("policyText").innerText = data.policyText;
        }

        hasResult = !!data.hasResult;
      } catch {
        console.warn("ไม่สามารถอ่านข้อมูลฉบับร่างได้");
      }

      renderStatus();
      applyRolePermissions();
    }

    function submitReport() {
      if (!hasResult) {
        alert("กรุณาประมวลผลก่อน (กดปุ่ม \"ประมวลผลอัตโนมัติ\") แล้วจึงส่งรายงานให้ผู้บริหาร");
        return;
      }
      saveDraft();
      updateStatus("submitted", "ส่งรายงานให้ผู้บริหาร (บันทึกสถานะในระบบติดตาม)", true);
      alert("บันทึกสถานะว่า \"ส่งรายงานให้ผู้บริหารแล้ว\" เรียบร้อย (ฟอร์มถูกล็อกไว้จนกว่าจะกด \"แก้ไขข้อมูล\")");
    }

    function editUnlock() {
      updateStatus("editing", "ปลดล็อกเพื่อแก้ไขข้อมูลรายงาน", false);
      alert("ปลดล็อกแบบฟอร์มแล้ว สามารถแก้ไขข้อมูลและประมวลผลใหม่ได้");
    }

    function acknowledgeDeputy() {
      updateStatus("ack_deputy", "รองผู้อำนวยการกดรับทราบรายงาน", true);
      alert("บันทึกสถานะแล้ว: รองผู้อำนวยการรับทราบรายงาน");
    }

    function acknowledgeDirector() {
      const st = getStatusObj();
      if (st.current !== "ack_deputy" && st.current !== "ack_director") {
        alert("รองผู้อำนวยการต้องกดรับทราบรายงานก่อน ผู้อำนวยการจึงจะรับทราบได้");
        return;
      }
      updateStatus("ack_director", "ผู้อำนวยการกดรับทราบรายงาน", true);
      alert("บันทึกสถานะแล้ว: ผู้อำนวยการรับทราบรายงาน");
    }

    // ---------- สร้าง .DOC ----------
    function escapeHtml(str) {
      return str
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;");
    }

    function createDocContent() {
      const schoolName = document.getElementById("schoolName").value.trim();
      const affiliation = document.getElementById("affiliation").value.trim();

      const activityName = document.getElementById("activityName").value.trim() || "กิจกรรมครั้งนี้";
      const academicYear = document.getElementById("academicYear").value.trim();
      const semester = document.getElementById("semester").value.trim();
      const managementGroup = document.getElementById("managementGroup").value.trim();
      const responsiblePerson = document.getElementById("responsiblePerson").value.trim();
      const numAttendees = document.getElementById("numAttendees").value.trim();
      const numParticipants = document.getElementById("numParticipants").value.trim();
      const budgetValue = document.getElementById("budget").value.trim();

      const summaryText = document.getElementById("summaryText").innerText.trim();
      const policyText = document.getElementById("policyText").innerText.trim();
      const now = new Date().toLocaleString("th-TH");
      const user = getCurrentUser() || {};

      const dimStats = computeDimensionStats();
      const dims = dimStats.dims || [];

      let headerHtml = "";
      if (schoolName) headerHtml += `<p><b>สถานศึกษา:</b> ${escapeHtml(schoolName)}</p>`;
      if (affiliation) headerHtml += `<p><b>สังกัด:</b> ${escapeHtml(affiliation)}</p>`;
      headerHtml += `<p><b>ชื่อกิจกรรม:</b> ${escapeHtml(activityName)}</p>`;

      if (semester || academicYear) {
        headerHtml += `<p><b>ภาคเรียน/ปีการศึกษา:</b> ${escapeHtml((semester || "") + (academicYear ? " ปีการศึกษา " + academicYear : ""))}</p>`;
      }
      if (managementGroup) {
        headerHtml += `<p><b>กลุ่มบริหาร:</b> ${escapeHtml(managementGroup)}</p>`;
      }
      if (responsiblePerson) {
        headerHtml += `<p><b>ผู้รับผิดชอบกิจกรรม:</b> ${escapeHtml(responsiblePerson)}</p>`;
      }
      if (numAttendees) {
        headerHtml += `<p><b>จำนวนผู้เข้าร่วมกิจกรรม:</b> ${escapeHtml(numAttendees)} คน</p>`;
      }
      if (numParticipants) {
        headerHtml += `<p><b>จำนวนผู้ตอบแบบประเมิน:</b> ${escapeHtml(numParticipants)} คน</p>`;
      }
      if (budgetValue) {
        headerHtml += `<p><b>งบประมาณ:</b> ${escapeHtml(budgetValue)} บาท</p>`;
      }

      let userLine = "";
      if (user.firstName || user.lastName) {
        userLine = `จัดทำโดย: ${user.firstName || ""} ${user.lastName || ""} (${roleLabel(user.role || "teacher")})`;
        headerHtml += `<p>${escapeHtml(userLine)}</p>`;
      }

      headerHtml += `<p>จัดทำเมื่อ: ${escapeHtml(now)}</p>`;

      // ตารางสรุปค่าเฉลี่ยตามด้าน
      let dimTableHtml = "";
      if (dims.length > 0) {
        dimTableHtml += `
          <h2>สรุปค่าเฉลี่ยตามด้าน (Dimension)</h2>
          <table>
            <thead>
              <tr>
                <th>ด้าน</th>
                <th>ค่าเฉลี่ย</th>
                <th>ระดับ</th>
              </tr>
            </thead>
            <tbody>
        `;
        dims.forEach(d => {
          dimTableHtml += `
            <tr>
              <td>${escapeHtml(d.name)}</td>
              <td>${d.mean.toFixed(2)}</td>
              <td>${escapeHtml(d.level)}</td>
            </tr>
          `;
        });
        dimTableHtml += `
            </tbody>
          </table>
        `;
      }

      const safeSummary = escapeHtml(summaryText).replace(/\n/g, "<br>");
      const safePolicy  = escapeHtml(policyText).replace(/\n/g, "<br>");

      const docHtml = `
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>รายงานการประเมินกิจกรรม</title>
  <style>
    body {
      font-family: 'TH SarabunPSK', 'TH Sarabun New', 'Tahoma', sans-serif;
      font-size: 16pt;
      line-height: 1.3;
    }
    h1 {
      text-align: center;
      margin-bottom: 0;
    }
    h2 {
      margin-top: 18pt;
      margin-bottom: 6pt;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 6pt;
    }
    th, td {
      border: 1px solid #000;
      padding: 4pt;
      text-align: center;
    }
    p {
      margin: 4pt 0;
    }
  </style>
</head>
<body>
  <h1>รายงานการประเมินผลการดำเนินกิจกรรม</h1>
  ${headerHtml}
  ${dimTableHtml}
  <h2>สรุปผลภาพรวมของกิจกรรม</h2>
  <p>${safeSummary}</p>
  <h2>ข้อเสนอแนะเชิงนโยบาย/การบริหารจัดการต่อไป</h2>
  <p>${safePolicy}</p>
  ${buildSignatureBlockForDoc()}
</body>
</html>`;

      return docHtml;
    }

    function downloadDoc() {
      if (!hasResult) {
        alert("กรุณากด \"ประมวลผลอัตโนมัติ\" ก่อน แล้วจึงดาวน์โหลดไฟล์ .DOC");
        return;
      }
      const html = createDocContent();
      const blob = new Blob([html], { type: "application/msword" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "activity-eval-report.doc";
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    }

    // ---------- INIT & LOGIN ----------
    document.addEventListener("DOMContentLoaded", () => {
      renderItemsTable();

      const loginWrapper = document.getElementById("loginWrapper");
      const mainWrapper = document.getElementById("mainWrapper");
      const currentUserNameEl = document.getElementById("currentUserName");
      const currentUserRoleEl = document.getElementById("currentUserRole");

      function showLogin() {
        loginWrapper.style.display = "block";
        mainWrapper.style.display = "none";
      }

      function showMain() {
        loginWrapper.style.display = "none";
        mainWrapper.style.display = "block";
        const user = getCurrentUser();
        if (user && currentUserNameEl) {
          currentUserNameEl.textContent = `${user.firstName || ""} ${user.lastName || ""}`.trim() || "-";
          currentUserRoleEl.textContent = roleLabel(user.role || "teacher");
        }
        loadDraft();
      }

      // ตรวจว่ามี user เดิมไหม
      const user = getCurrentUser();
      if (user) {
        showMain();
      } else {
        showLogin();
      }

      // ปุ่ม Login
      const loginBtn = document.getElementById("btnLogin");
      const loginError = document.getElementById("loginError");

      loginBtn.addEventListener("click", () => {
        const firstName = document.getElementById("loginFirstName").value.trim();
        const lastName  = document.getElementById("loginLastName").value.trim();
        const password  = document.getElementById("loginPassword").value.trim();
        const role      = document.getElementById("loginRole").value;

        if (!firstName || !lastName) {
          loginError.textContent = "กรุณากรอกชื่อและนามสกุลให้ครบถ้วน";
          return;
        }

        if (!/^[0-9]{6}$/.test(password)) {
          loginError.textContent = "กรุณากรอกรหัสผ่านเป็นตัวเลข 6 หลัก";
          return;
        }

        loginError.textContent = "";
        setCurrentUser(firstName, lastName, role);
        showMain();
      });

      // ปุ่ม Logout
      const logoutBtn = document.getElementById("btnLogout");
      logoutBtn.addEventListener("click", () => {
        clearCurrentUser();
        alert("ออกจากระบบเรียบร้อย");
        showLogin();
      });

      // ปุ่มหลักในหน้า Main
      document.getElementById("btnCalculate").addEventListener("click", calculateAndRender);
      document.getElementById("btnDownloadDoc").addEventListener("click", downloadDoc);

      document.getElementById("btnSaveDraft").addEventListener("click", saveDraft);
      document.getElementById("btnSubmitReport").addEventListener("click", submitReport);
      document.getElementById("btnEditUnlock").addEventListener("click", editUnlock);
      document.getElementById("btnAcknowledgeDeputy").addEventListener("click", acknowledgeDeputy);
      document.getElementById("btnAcknowledgeDirector").addEventListener("click", acknowledgeDirector);
    });
  </script>
</body>
</html>
