# student-login-system

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>StudentHub · login</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: system-ui, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
    }

    body {
      background: linear-gradient(135deg, #eef2ff 0%, #e0e7ff 50%, #f1f5f9 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .app {
      max-width: 1100px;
      width: 100%;
      display: flex;
      background: rgba(255, 255, 255, 0.7);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border-radius: 42px;
      box-shadow: 0 30px 60px -20px rgba(0, 20, 50, 0.3),
                  inset 0 1px 4px rgba(255, 255, 255, 0.9);
      overflow: hidden;
      border: 1px solid rgba(255, 255, 255, 0.6);
      min-height: 640px;
    }

    /* ---------- left decorative panel ---------- */
    .side-panel {
      flex: 0 0 340px;
      background: linear-gradient(145deg, #1e293b, #0f172a);
      color: white;
      padding: 48px 32px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      position: relative;
      overflow: hidden;
    }

    .side-panel::before {
      content: "";
      position: absolute;
      width: 400px;
      height: 400px;
      background: radial-gradient(circle, #3b82f640 0%, transparent 70%);
      top: -100px;
      right: -150px;
      border-radius: 50%;
    }

    .side-panel::after {
      content: "";
      position: absolute;
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, #8b5cf640 0%, transparent 70%);
      bottom: -80px;
      left: -100px;
      border-radius: 50%;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 14px;
      font-size: 1.6rem;
      font-weight: 700;
      letter-spacing: -0.5px;
      position: relative;
      z-index: 2;
    }

    .brand-icon {
      width: 44px;
      height: 44px;
      background: #3b82f6;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      box-shadow: 0 8px 16px -6px #3b82f6;
    }

    .side-content {
      position: relative;
      z-index: 2;
    }

    .side-content h2 {
      font-size: 2rem;
      font-weight: 700;
      line-height: 1.2;
      margin-bottom: 16px;
      letter-spacing: -1px;
    }

    .side-content p {
      color: #cbd5e1;
      font-size: 0.95rem;
      line-height: 1.6;
      margin-bottom: 28px;
    }

    .feature-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 14px;
    }

    .feature-list li {
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: 0.9rem;
      color: #e2e8f0;
      font-weight: 500;
    }

    .feature-list .dot {
      width: 26px;
      height: 26px;
      background: #3b82f625;
      border: 1px solid #3b82f650;
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.8rem;
    }

    .side-footer {
      position: relative;
      z-index: 2;
      font-size: 0.8rem;
      color: #64748b;
    }

    /* ---------- right form panel ---------- */
    .form-panel {
      flex: 1;
      padding: 48px 44px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      background: #ffffffb0;
    }

    .form-header {
      margin-bottom: 36px;
    }

    .form-header h1 {
      font-size: 1.9rem;
      font-weight: 700;
      color: #0f172a;
      letter-spacing: -0.6px;
      margin-bottom: 8px;
    }

    .form-header p {
      color: #64748b;
      font-size: 0.95rem;
    }

    .input-field {
      margin-bottom: 20px;
      position: relative;
    }

    .input-field label {
      display: block;
      font-size: 0.8rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      color: #475569;
      margin-bottom: 8px;
    }

    .input-wrapper {
      position: relative;
      display: flex;
      align-items: center;
    }

    .input-wrapper .icon {
      position: absolute;
      left: 16px;
      font-size: 1.1rem;
      color: #94a3b8;
      pointer-events: none;
      transition: 0.2s;
    }

    .input-field input {
      width: 100%;
      padding: 16px 18px 16px 48px;
      background: #ffffff;
      border: 1.5px solid #e2e8f0;
      border-radius: 18px;
      font-size: 0.95rem;
      font-weight: 500;
      color: #0f172a;
      outline: none;
      transition: all 0.2s;
    }

    .input-field input:focus {
      border-color: #3b82f6;
      box-shadow: 0 0 0 4px #3b82f620;
    }

    .input-field input:focus + .icon {
      color: #3b82f6;
    }

    .input-field input::placeholder {
      color: #94a3b8;
      font-weight: 400;
    }

    .toggle-password {
      position: absolute;
      right: 16px;
      background: none;
      border: none;
      cursor: pointer;
      font-size: 1.1rem;
      color: #94a3b8;
      padding: 4px;
      transition: 0.2s;
    }

    .toggle-password:hover {
      color: #3b82f6;
    }

    .form-options {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 28px;
      font-size: 0.85rem;
    }

    .checkbox-wrap {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #334155;
      cursor: pointer;
      user-select: none;
    }

    .checkbox-wrap input[type="checkbox"] {
      width: 18px;
      height: 18px;
      accent-color: #3b82f6;
      cursor: pointer;
    }

    .forgot-link {
      color: #3b82f6;
      text-decoration: none;
      font-weight: 500;
      transition: 0.2s;
    }

    .forgot-link:hover {
      color: #2563eb;
      text-decoration: underline;
    }

    .login-btn {
      width: 100%;
      padding: 17px;
      background: #0f172a;
      color: white;
      border: none;
      border-radius: 40px;
      font-size: 1rem;
      font-weight: 700;
      letter-spacing: 0.3px;
      cursor: pointer;
      transition: 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      box-shadow: 0 14px 28px -12px #0f172a90;
    }

    .login-btn:hover {
      background: #1e293b;
      transform: translateY(-1px);
      box-shadow: 0 18px 32px -12px #0f172aa0;
    }

    .login-btn:active {
      transform: translateY(0) scale(0.99);
    }

    .login-btn:disabled {
      background: #94a3b8;
      cursor: not-allowed;
      transform: none;
      box-shadow: none;
    }

    .message-box {
      margin-top: 20px;
      padding: 14px 18px;
      border-radius: 16px;
      font-size: 0.9rem;
      font-weight: 500;
      display: none;
      align-items: center;
      gap: 10px;
    }

    .message-box.error {
      display: flex;
      background: #fee2e2;
      color: #991b1b;
      border: 1px solid #fca5a5;
    }

    .message-box.success {
      display: flex;
      background: #dcfce7;
      color: #166534;
      border: 1px solid #86efac;
    }

    .demo-hint {
      margin-top: 28px;
      padding: 16px 20px;
      background: #f1f5f9;
      border-radius: 18px;
      border-left: 4px solid #3b82f6;
      font-size: 0.82rem;
      color: #475569;
      line-height: 1.6;
    }

    .demo-hint strong {
      color: #0f172a;
      display: block;
      margin-bottom: 4px;
      font-size: 0.85rem;
    }

    .demo-hint code {
      background: #e2e8f0;
      padding: 2px 8px;
      border-radius: 6px;
      font-family: ui-monospace, monospace;
      color: #0f172a;
      font-weight: 600;
      font-size: 0.8rem;
    }

    /* ---------- dashboard (hidden initially) ---------- */
    .dashboard {
      display: none;
      flex: 1;
      padding: 44px 44px;
      background: #ffffffb0;
      flex-direction: column;
      overflow-y: auto;
      max-height: 640px;
    }

    .dashboard.active {
      display: flex;
    }

    .dashboard-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 32px;
      flex-wrap: wrap;
      gap: 16px;
    }

    .welcome-badge {
      display: flex;
      align-items: center;
      gap: 16px;
    }

    .avatar {
      width: 56px;
      height: 56px;
      background: linear-gradient(145deg, #3b82f6, #8b5cf6);
      border-radius: 18px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: 700;
      font-size: 1.3rem;
      box-shadow: 0 10px 20px -8px #3b82f6;
    }

    .welcome-badge h2 {
      font-size: 1.4rem;
      font-weight: 700;
      color: #0f172a;
      letter-spacing: -0.4px;
    }

    .welcome-badge p {
      font-size: 0.85rem;
      color: #64748b;
    }

    .logout-btn {
      padding: 12px 24px;
      background: #fee2e2;
      color: #b91c1c;
      border: 1px solid #fecaca;
      border-radius: 30px;
      font-weight: 600;
      font-size: 0.85rem;
      cursor: pointer;
      transition: 0.2s;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .logout-btn:hover {
      background: #fecaca;
      border-color: #fca5a5;
    }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 16px;
      margin-bottom: 32px;
    }

    .stat-card {
      background: #f8fafc;
      border-radius: 22px;
      padding: 22px 20px;
      border: 1px solid #e2e8f0;
      transition: 0.2s;
    }

    .stat-card:hover {
      border-color: #cbd5e1;
      box-shadow: 0 10px 20px -14px #0f172a30;
    }

    .stat-card .label {
      font-size: 0.75rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      color: #64748b;
      margin-bottom: 8px;
    }

    .stat-card .value {
      font-size: 1.8rem;
      font-weight: 700;
      color: #0f172a;
      letter-spacing: -0.8px;
    }

    .stat-card .value small {
      font-size: 0.9rem;
      font-weight: 500;
      color: #64748b;
    }

    .info-panel {
      background: #f8fafc;
      border-radius: 24px;
      padding: 26px 28px;
      border: 1px solid #e2e8f0;
    }

    .info-panel h3 {
      font-size: 1.05rem;
      font-weight: 600;
      color: #0f172a;
      margin-bottom: 18px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .info-row {
      display: flex;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid #e2e8f0;
      font-size: 0.9rem;
    }

    .info-row:last-child {
      border-bottom: none;
    }

    .info-row .key {
      color: #64748b;
      font-weight: 500;
    }

    .info-row .val {
      color: #0f172a;
      font-weight: 600;
    }

    .course-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 8px;
    }

    .course-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px 18px;
      background: white;
      border-radius: 16px;
      border: 1px solid #e2e8f0;
      font-size: 0.88rem;
      transition: 0.2s;
    }

    .course-item:hover {
      border-color: #93c5fd;
      background: #f0f9ff;
    }

    .course-item .code {
      font-weight: 700;
      color: #1e40af;
      background: #dbeafe;
      padding: 4px 12px;
      border-radius: 20px;
      font-size: 0.78rem;
    }

    .course-item .grade {
      font-weight: 700;
      color: #059669;
    }

    /* ---------- responsive ---------- */
    @media (max-width: 900px) {
      .app {
        flex-direction: column;
        min-height: auto;
      }
      .side-panel {
        flex: 0 0 auto;
        padding: 36px 28px;
      }
      .side-content h2 {
        font-size: 1.6rem;
      }
      .form-panel, .dashboard {
        padding: 36px 28px;
      }
    }

    @media (max-width: 480px) {
      body {
        padding: 10px;
      }
      .app {
        border-radius: 28px;
      }
      .form-header h1 {
        font-size: 1.5rem;
      }
      .side-panel {
        padding: 28px 20px;
      }
    }
  </style>
</head>
<body>
<div class="app">

  <!-- ========== LEFT DECORATIVE PANEL ========== -->
  <aside class="side-panel" id="sidePanel">
    <div class="brand">
      <div class="brand-icon">🎓</div>
      StudentHub
    </div>
    <div class="side-content">
      <h2>Your academic journey starts here.</h2>
      <p>Access courses, grades, schedules, and campus resources — all in one secure place.</p>
      <ul class="feature-list">
        <li><span class="dot">📚</span> Course materials & assignments</li>
        <li><span class="dot">📊</span> Real‑time grades & GPA</li>
        <li><span class="dot">🗓️</span> Personalized timetable</li>
        <li><span class="dot">🔔</span> Campus announcements</li>
      </ul>
    </div>
    <div class="side-footer">
      © 2025 StudentHub · Secure portal
    </div>
  </aside>

  <!-- ========== LOGIN FORM PANEL ========== -->
  <main class="form-panel" id="loginPanel">
    <div class="form-header">
      <h1>Welcome back 👋</h1>
      <p>Sign in to your student account to continue.</p>
    </div>

    <form id="loginForm" autocomplete="off">
      <div class="input-field">
        <label for="studentId">Student ID or Email</label>
        <div class="input-wrapper">
          <span class="icon">🆔</span>
          <input type="text" id="studentId" placeholder="e.g. STU-2025-001" required>
        </div>
      </div>

      <div class="input-field">
        <label for="password">Password</label>
        <div class="input-wrapper">
          <span class="icon">🔒</span>
          <input type="password" id="password" placeholder="Enter your password" required>
          <button type="button" class="toggle-password" id="togglePassword" aria-label="Show password">👁️</button>
        </div>
      </div>

      <div class="form-options">
        <label class="checkbox-wrap">
          <input type="checkbox" id="rememberMe"> Remember me
        </label>
        <a href="#" class="forgot-link" id="forgotLink">Forgot password?</a>
      </div>

      <button type="submit" class="login-btn" id="loginBtn">
        🔐 Sign in
      </button>

      <div class="message-box" id="messageBox"></div>
    </form>

    <div class="demo-hint">
      <strong>🔑 Demo credentials</strong>
      Student ID: <code>STU-2025-001</code> · Password: <code>student123</code><br>
      Or use: <code>alex.johnson@university.edu</code> · <code>alex2025</code>
    </div>
  </main>

  <!-- ========== DASHBOARD (shown after login) ========== -->
  <main class="dashboard" id="dashboard">
    <div class="dashboard-header">
      <div class="welcome-badge">
        <div class="avatar" id="avatarInitials">AJ</div>
        <div>
          <h2 id="welcomeName">Welcome, Alex!</h2>
          <p id="welcomeMeta">Student ID: STU-2025-001 · Computer Science</p>
        </div>
      </div>
      <button class="logout-btn" id="logoutBtn">
        🚪 Log out
      </button>
    </div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="label">GPA</div>
        <div class="value" id="statGpa">3.82<small> / 4.0</small></div>
      </div>
      <div class="stat-card">
        <div class="label">Credits</div>
        <div class="value" id="statCredits">94<small> earned</small></div>
      </div>
      <div class="stat-card">
        <div class="label">Courses</div>
        <div class="value" id="statCourses">4<small> enrolled</small></div>
      </div>
      <div class="stat-card">
        <div class="label">Attendance</div>
        <div class="value" id="statAttendance">96<small>%</small></div>
      </div>
    </div>

    <div class="info-panel">
      <h3>📋 Personal information</h3>
      <div class="info-row">
        <span class="key">Full name</span>
        <span class="val" id="infoName">Alex Johnson</span>
      </div>
      <div class="info-row">
        <span class="key">Email</span>
        <span class="val" id="infoEmail">alex.johnson@university.edu</span>
      </div>
      <div class="info-row">
        <span class="key">Major</span>
        <span class="val" id="infoMajor">Computer Science</span>
      </div>
      <div class="info-row">
        <span class="key">Year</span>
        <span class="val" id="infoYear">Junior (3rd year)</span>
      </div>
      <div class="info-row">
        <span class="key">Advisor</span>
        <span class="val" id="infoAdvisor">Dr. Maria Chen</span>
      </div>
    </div>

    <div class="info-panel" style="margin-top: 20px;">
      <h3>📚 Current courses</h3>
      <div class="course-list" id="courseList">
        <!-- dynamically injected -->
      </div>
    </div>
  </main>
</div>

<script>
  (function() {
    // ---------- student database (demo) ----------
    const students = [
      {
        id: 'STU-2025-001',
        email: 'alex.johnson@university.edu',
        password: 'student123',          // also alex2025 works for email
        firstName: 'Alex',
        lastName: 'Johnson',
        fullName: 'Alex Johnson',
        major: 'Computer Science',
        year: 'Junior (3rd year)',
        advisor: 'Dr. Maria Chen',
        gpa: 3.82,
        creditsEarned: 94,
        attendance: 96,
        courses: [
          { code: 'CS 301', title: 'Data Structures & Algorithms', grade: 'A' },
          { code: 'CS 310', title: 'Database Systems', grade: 'A-' },
          { code: 'MATH 221', title: 'Linear Algebra', grade: 'B+' },
          { code: 'CS 350', title: 'Operating Systems', grade: 'A' }
        ]
      },
      {
        id: 'STU-2025-002',
        email: 'priya.patel@university.edu',
        password: 'priya2025',
        firstName: 'Priya',
        lastName: 'Patel',
        fullName: 'Priya Patel',
        major: 'Electrical Engineering',
        year: 'Senior (4th year)',
        advisor: 'Dr. James Wilson',
        gpa: 3.95,
        creditsEarned: 118,
        attendance: 98,
        courses: [
          { code: 'EE 401', title: 'Digital Signal Processing', grade: 'A' },
          { code: 'EE 420', title: 'Power Systems', grade: 'A' },
          { code: 'CS 350', title: 'Operating Systems', grade: 'A-' },
          { code: 'PHYS 301', title: 'Quantum Mechanics', grade: 'B+' }
        ]
      },
      {
        id: 'STU-2025-003',
        email: 'marcus.lee@university.edu',
        password: 'marcus2025',
        firstName: 'Marcus',
        lastName: 'Lee',
        fullName: 'Marcus Lee',
        major: 'Business Administration',
        year: 'Sophomore (2nd year)',
        advisor: 'Dr. Sarah Kim',
        gpa: 3.45,
        creditsEarned: 52,
        attendance: 89,
        courses: [
          { code: 'BUS 201', title: 'Principles of Marketing', grade: 'B+' },
          { code: 'BUS 210', title: 'Financial Accounting', grade: 'B' },
          { code: 'ECON 101', title: 'Microeconomics', grade: 'A-' },
          { code: 'BUS 220', title: 'Business Statistics', grade: 'B' }
        ]
      }
    ];

    // ---------- DOM elements ----------
    const loginPanel = document.getElementById('loginPanel');
    const dashboard = document.getElementById('dashboard');
    const loginForm = document.getElementById('loginForm');
    const studentIdInput = document.getElementById('studentId');
    const passwordInput = document.getElementById('password');
    const togglePassword = document.getElementById('togglePassword');
    const messageBox = document.getElementById('messageBox');
    const loginBtn = document.getElementById('loginBtn');
    const logoutBtn = document.getElementById('logoutBtn');
    const forgotLink = document.getElementById('forgotLink');

    // dashboard fields
    const avatarInitials = document.getElementById('avatarInitials');
    const welcomeName = document.getElementById('welcomeName');
    const welcomeMeta = document.getElementById('welcomeMeta');
    const statGpa = document.getElementById('statGpa');
    const statCredits = document.getElementById('statCredits');
    const statCourses = document.getElementById('statCourses');
    const statAttendance = document.getElementById('statAttendance');
    const infoName = document.getElementById('infoName');
    const infoEmail = document.getElementById('infoEmail');
    const infoMajor = document.getElementById('infoMajor');
    const infoYear = document.getElementById('infoYear');
    const infoAdvisor = document.getElementById('infoAdvisor');
    const courseList = document.getElementById('courseList');

    // ---------- toggle password visibility ----------
    togglePassword.addEventListener('click', function() {
      const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
      passwordInput.setAttribute('type', type);
      this.textContent = type === 'password' ? '👁️' : '🙈';
    });

    // ---------- helper: show message ----------
    function showMessage(text, type = 'error') {
      messageBox.textContent = text;
      messageBox.className = `message-box ${type}`;
      // auto-hide success messages after 4s
      if (type === 'success') {
        setTimeout(() => {
          messageBox.style.display = 'none';
          messageBox.className = 'message-box';
        }, 4000);
      }
    }

    function clearMessage() {
      messageBox.textContent = '';
      messageBox.className = 'message-box';
      messageBox.style.display = 'none';
    }

    // ---------- find student by identifier (id or email) ----------
    function findStudent(identifier) {
      const trimmed = identifier.trim().toLowerCase();
      return students.find(s =>
        s.id.toLowerCase() === trimmed ||
        s.email.toLowerCase() === trimmed
      );
    }

    // ---------- populate dashboard ----------
    function populateDashboard(student) {
      // avatar initials
      const initials = student.firstName.charAt(0).toUpperCase() + student.lastName.charAt(0).toUpperCase();
      avatarInitials.textContent = initials;

      // welcome
      welcomeName.textContent = `Welcome, ${student.firstName}!`;
      welcomeMeta.textContent = `Student ID: ${student.id} · ${student.major}`;

      // stats
      statGpa.innerHTML = `${student.gpa.toFixed(2)}<small> / 4.0</small>`;
      statCredits.innerHTML = `${student.creditsEarned}<small> earned</small>`;
      statCourses.innerHTML = `${student.courses.length}<small> enrolled</small>`;
      statAttendance.innerHTML = `${student.attendance}<small>%</small>`;

      // personal info
      infoName.textContent = student.fullName;
      infoEmail.textContent = student.email;
      infoMajor.textContent = student.major;
      infoYear.textContent = student.year;
      infoAdvisor.textContent = student.advisor;

      // courses
      courseList.innerHTML = student.courses.map(c =>
        `<div class="course-item">
           <span><span class="code">${c.code}</span> ${c.title}</span>
           <span class="grade">${c.grade}</span>
         </div>`
      ).join('');
    }

    // ---------- login handler ----------
    loginForm.addEventListener('submit', function(e) {
      e.preventDefault();
      clearMessage();

      const identifier = studentIdInput.value.trim();
      const password = passwordInput.value.trim();

      if (!identifier || !password) {
        showMessage('⚠️ Please fill in both fields.', 'error');
        return;
      }

      const student = findStudent(identifier);

      // special case: email "alex.johnson@university.edu" also accepts "alex2025"
      let passwordMatch = false;
      if (student) {
        if (student.password === password) {
          passwordMatch = true;
        }
        // additional demo: allow alex2025 for the first student's email
        if (student.id === 'STU-2025-001' && password === 'alex2025') {
          passwordMatch = true;
        }
      }

      if (!student || !passwordMatch) {
        showMessage('❌ Invalid credentials. Please check your Student ID/email and password.', 'error');
        passwordInput.value = '';
        passwordInput.focus();
        return;
      }

      // successful login
      showMessage(`✅ Login successful! Welcome, ${student.firstName}.`, 'success');

      // disable button briefly to simulate loading
      loginBtn.disabled = true;
      loginBtn.innerHTML = '⏳ Signing in...';

      setTimeout(() => {
        // switch panels
        loginPanel.style.display = 'none';
        dashboard.classList.add('active');

        // populate dashboard with student data
        populateDashboard(student);

        // re-enable login button for next time
        loginBtn.disabled = false;
        loginBtn.innerHTML = '🔐 Sign in';

        // clear form (optional)
        // studentIdInput.value = '';
        // passwordInput.value = '';
        clearMessage();
      }, 600);
    });

    // ---------- logout handler ----------
    logoutBtn.addEventListener('click', function() {
      // hide dashboard, show login
      dashboard.classList.remove('active');
      loginPanel.style.display = 'flex';

      // reset form
      loginForm.reset();
      passwordInput.setAttribute('type', 'password');
      togglePassword.textContent = '👁️';
      clearMessage();

      // focus on student id
      studentIdInput.focus();
    });

    // ---------- forgot password (demo) ----------
    forgotLink.addEventListener('click', function(e) {
      e.preventDefault();
      alert('📧 Password reset link would be sent to your university email.\n\n(Demo: use your Student ID and the provided password.)');
    });

    // ---------- prefill demo credentials on double-click for convenience ----------
    // (just a small easter egg: double-click on student ID field fills demo)
    studentIdInput.addEventListener('dblclick', function() {
      studentIdInput.value = 'STU-2025-001';
      passwordInput.value = 'student123';
    });

    // ---------- keyboard: allow Enter on password to submit (already handled by form) ----------

    // ---------- initial focus ----------
    window.addEventListener('load', function() {
      studentIdInput.focus();
    });

    // ---------- quick demo: if user types STU-2025-001, hint password ----------
    // (not necessary but nice)
  })();
</script>
</body>
</html>
