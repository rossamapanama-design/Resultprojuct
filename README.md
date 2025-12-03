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
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 20px;
      color: #222;
    }

    .app-wrapper {
      width: 100%;
      max-width: 1100px;
      background: #ffffff;
      border-radius: 16px;
      padding: 24px 24px 40px;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.22);
    }

    h1 {
      margin: 0 0 10px;
      font-size: 1.7rem;
      text-align: center;
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
    select,
    textarea {
      width: 100%;
      padding: 6px 8px;
      border-radius: 8px;
      border: 1px solid #d0d4f5;
      font-size: 0.9rem;
      outline: none;
    }

    input[type="number"]:focus,
    input[type="text"]:focus,
    select:focus,
    textarea:focus {
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
      padding: 8px 18px;
      font-size: 0.95rem;
      font-weight: 600;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: transform 0.05s ease, box-shadow 0.1s ease, background 0.2s ease;
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

    button:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 24px rgba(0, 0, 0, 0.16);
    }

    button:active {
      transform: translateY(0);
      box-shadow: none;
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

    @media (max-width: 768px) {
      .app-wrapper {
        padding: 16px 14px 24px;
      }
      h1 {
        font-size: 1.3rem;
      }
    }
  </style>
</head>
<body>
  <div class="app-wrapper">
    <h1>ระบบแปลผลการดำเนินกิจกรรมออนไลน์</h1>
    <p class="subtitle">
      Fully Automatic Activity Evaluation System (Likert 5 ระดับ) – คำนวณค่าเฉลี่ย แปลผล และสรุปผลกิจกรรมให้อัตโนมัติ 100%
    </p>

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
          <label>ชื่อผู้รับผิดชอบกิจกรรม</label>
          <input id="responsiblePerson" type="text" placeholder="เช่น ครูผู้รับผิดชอบโครงการ" />
        </div>
      </div>
      <div class="flex mt-2">
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

    <!-- ปุ่มประมวลผล + ดาวน์โหลด -->
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
            ⬇️ .DOC
          </button>
          <button id="btnDownloadPdf" class="secondary">
            ⬇️ PDF
          </button>
        </div>
      </div>
    </div>

    <!-- 5. ผลลัพธ์ -->
    <div class="card">
      <h2>5. ผลการประเมินเชิงสถิติ</h2>
      <div id="statsContainer" class="mt-2">
        <!-- จะสร้างด้วย JS -->
      </div>
    </div>

    <div class="card">
      <h2>6. สรุปผลในภาพรวม (ข้อความพร้อมใช้รายงาน/โครงการ)</h2>
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
  </div>

  <!-- jsPDF CDN สำหรับสร้างไฟล์ PDF -->
  <script src="https://cdn.jsdelivr.net/npm/jspdf@2.5.1/dist/jspdf.umd.min.js"></script>

  <script>
    // ---------- CONFIG เริ่มต้น: รายการข้อประเมินตัวอย่าง ----------
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
    let hasResult = false; // ใช้เช็คว่าประมวลผลแล้วหรือยัง

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

    function calculateAndRender() {
      const activityName = document.getElementById("activityName").value.trim() || "กิจกรรมครั้งนี้";
      const academicYear = document.getElementById("academicYear").value.trim();
      const semester = document.getElementById("semester").value.trim();
      const responsiblePerson = document.getElementById("responsiblePerson").value.trim();
      const budgetValue = document.getElementById("budget").value.trim();

      const numParticipants = parseFloat(document.getElementById("numParticipants").value) || 0;
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

      if (items.length === 0) {
        statsContainer.innerHTML = `<p class="small">ยังไม่ได้กรอกค่าเฉลี่ยของข้อประเมินใด ๆ กรุณากรอกอย่างน้อย 1 ข้อ</p>`;
        summaryTextEl.textContent = "ยังไม่สามารถสรุปผลได้เนื่องจากไม่มีข้อมูลค่าเฉลี่ยของข้อประเมิน";
        policyTextEl.textContent = "โปรดกรอกข้อมูลการประเมินให้ครบถ้วนก่อน เพื่อให้ระบบสามารถสรุปข้อเสนอแนะเชิงนโยบายได้อย่างเหมาะสม";
        hasResult = false;
        return;
      }

      const overallMean = sumAllMeans / countMeans;
      const estimatedPercentPass = overallMean >= thresholdMean ? 100 : 60;
      const overallLevel = interpretLikert(overallMean);
      const overallPassKPI =
        overallMean >= thresholdMean && estimatedPercentPass >= thresholdPercent;

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

      const nameForText = activityName || "กิจกรรมดังกล่าว";

      let summaryText = "";
      summaryText += `${nameForText}`;
      if (semester || academicYear) {
        summaryText += ` จัดในภาคเรียน/ปีการศึกษา `;
        if (semester) summaryText += `${semester} `;
        if (academicYear) summaryText += `ปีการศึกษา ${academicYear} `;
      }
      if (responsiblePerson) {
        summaryText += `โดยมีผู้รับผิดชอบกิจกรรมคือ ${responsiblePerson} `;
      }
      summaryText += `มีผู้ตอบแบบประเมินจำนวนประมาณ ${numParticipants || "…"} คน `;
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
        : "กิจกรรมครั้งนี้ยังไม่บรรลุเป้าหมายตามตัวชี้วัดที่กำหนดอย่างเต็มที่ และควรมีการออกแบบกิจกรรม/ปรับกลยุทธ์เพิ่มเติมในครั้งถัดไป";

      summaryTextEl.textContent = summaryText;

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

      hasResult = true;
    }

    function createDocContent() {
      const activityName = document.getElementById("activityName").value.trim() || "กิจกรรมครั้งนี้";
      const academicYear = document.getElementById("academicYear").value.trim();
      const semester = document.getElementById("semester").value.trim();
      const responsiblePerson = document.getElementById("responsiblePerson").value.trim();
      const budgetValue = document.getElementById("budget").value.trim();

      const summaryText = document.getElementById("summaryText").innerText.trim();
      const policyText = document.getElementById("policyText").innerText.trim();
      const statsText = document.getElementById("statsContainer").innerText.trim();
      const now = new Date().toLocaleString("th-TH");

      let header = `รายงานการประเมินผลการดำเนินกิจกรรมออนไลน์\n`;
      header += `ชื่อกิจกรรม: ${activityName}\n`;
      if (semester || academicYear) {
        header += `ภาคเรียน/ปีการศึกษา: `;
        if (semester) header += `${semester} `;
        if (academicYear) header += `ปีการศึกษา ${academicYear} `;
        header += `\n`;
      }
      if (responsiblePerson) {
        header += `ผู้รับผิดชอบกิจกรรม: ${responsiblePerson}\n`;
      }
      if (budgetValue) {
        header += `งบประมาณ: ${budgetValue} บาท\n`;
      }
      header += `จัดทำเมื่อ: ${now}\n\n`;

      const fullText =
        header +
        `=== สรุปผลภาพรวม ===\n` +
        summaryText + `\n\n` +
        `=== ข้อเสนอแนะเชิงนโยบาย/การบริหาร ===\n` +
        policyText + `\n\n` +
        `=== สถิติโดยสรุป ===\n` +
        statsText;

      const safeText = fullText
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;");

      const docHtml =
        `<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>รายงานการประเมินกิจกรรม</title>
<style>
body { font-family: "Sarabun", "Tahoma", sans-serif; white-space: pre-wrap; }
h1 { text-align: center; }
</style>
</head>
<body>
<h1>รายงานการประเมินกิจกรรม</h1>
<pre>${safeText}</pre>
</body>
</html>`;

      return docHtml;
    }

    function downloadDoc() {
      if (!hasResult) {
        alert("กรุณากด \"ประมวลผลอัตโนมัติ\" ก่อนดาวน์โหลดไฟล์ .DOC");
        return;
      }
      const content = createDocContent();
      const blob = new Blob([content], { type: "application/msword" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "activity-eval-report.doc";
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    }

    function downloadPdf() {
      if (!hasResult) {
        alert("กรุณากด \"ประมวลผลอัตโนมัติ\" ก่อนดาวน์โหลดไฟล์ PDF");
        return;
      }
      if (!window.jspdf || !window.jspdf.jsPDF) {
        alert("ไม่สามารถโหลดไลบรารี PDF ได้ กรุณาเชื่อมต่ออินเทอร์เน็ตหรือลองใหม่อีกครั้ง");
        return;
      }

      const activityName = document.getElementById("activityName").value.trim() || "กิจกรรมครั้งนี้";
      const academicYear = document.getElementById("academicYear").value.trim();
      const semester = document.getElementById("semester").value.trim();
      const responsiblePerson = document.getElementById("responsiblePerson").value.trim();
      const budgetValue = document.getElementById("budget").value.trim();

      const summaryText = document.getElementById("summaryText").innerText.trim();
      const policyText = document.getElementById("policyText").innerText.trim();
      const statsText = document.getElementById("statsContainer").innerText.trim();
      const now = new Date().toLocaleString("th-TH");

      let header = `รายงานการประเมินผลการดำเนินกิจกรรมออนไลน์\n`;
      header += `ชื่อกิจกรรม: ${activityName}\n`;
      if (semester || academicYear) {
        header += `ภาคเรียน/ปีการศึกษา: `;
        if (semester) header += `${semester} `;
        if (academicYear) header += `ปีการศึกษา ${academicYear} `;
        header += `\n`;
      }
      if (responsiblePerson) {
        header += `ผู้รับผิดชอบกิจกรรม: ${responsiblePerson}\n`;
      }
      if (budgetValue) {
        header += `งบประมาณ: ${budgetValue} บาท\n`;
      }
      header += `จัดทำเมื่อ: ${now}\n\n`;

      const fullText =
        header +
        `=== สรุปผลภาพรวม ===\n` +
        summaryText + `\n\n` +
        `=== ข้อเสนอแนะเชิงนโยบาย/การบริหาร ===\n` +
        policyText + `\n\n` +
        `=== สถิติโดยสรุป ===\n` +
        statsText;

      const { jsPDF } = window.jspdf;
      const doc = new jsPDF({ orientation: "p", unit: "pt", format: "a4" });
      const margin = 40;
      const maxWidth = 515;
      doc.setFontSize(12);
      const lines = doc.splitTextToSize(fullText, maxWidth);
      doc.text(lines, margin, margin);
      doc.save("activity-eval-report.pdf");
    }

    document.addEventListener("DOMContentLoaded", () => {
      renderItemsTable();
      document.getElementById("btnCalculate").addEventListener("click", calculateAndRender);
      document.getElementById("btnDownloadDoc").addEventListener("click", downloadDoc);
      document.getElementById("btnDownloadPdf").addEventListener("click", downloadPdf);
    });
  </script>
</body>
</html>
