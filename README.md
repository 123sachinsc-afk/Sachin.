# Sachin.
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sachin Chaugule - Interactive Professional Profile</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #fdfcf8; color: #1f2937; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 300px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 350px; } }
        .card-hover:hover { transform: translateY(-2px); box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); }
        .transition-all { transition-property: all; transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1); transition-duration: 300ms; }
        .hidden-content { display: none; }
        .active-tab { border-bottom: 2px solid #ea580c; color: #ea580c; font-weight: 600; }
    </style>
</head>
<body class="bg-[#fdfcf8] min-h-screen flex flex-col">

    <!-- Chosen Palette: Warm Neutrals (Background: #fdfcf8, Surface: #ffffff) with Burnt Orange (#ea580c) and Slate Blue (#475569) accents for professional yet creative feel. -->
    
    <!-- Application Structure Plan: 
         1. Header: Quick contact info and role definition.
         2. Dashboard Overview: High-level metrics (Years exp, awards) and a summary.
         3. Interactive Analysis Section: 
            - 'Skill Radar': Visualizing technical proficiency.
            - 'Experience Impact': Timeline with clickable details on key projects (South Korea, Database).
            - 'Competency Breakdown': Donut chart showing the split between Design, Mgmt, and Tech tasks.
         4. Credentials & Awards: Grid layout for certifications and recognition.
         This structure moves from "Who is he?" to "What can he do?" to "What has he achieved?", mimicking a hiring manager's mental evaluation process.
    -->

    <!-- Navigation -->
    <nav class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <span class="text-2xl font-bold text-slate-800 tracking-tight">SC.</span>
                </div>
                <div class="hidden md:flex space-x-8 items-center">
                    <button onclick="navTo('dashboard')" class="text-gray-600 hover:text-orange-600 transition-colors">Dashboard</button>
                    <button onclick="navTo('skills')" class="text-gray-600 hover:text-orange-600 transition-colors">Technical Arsenal</button>
                    <button onclick="navTo('experience')" class="text-gray-600 hover:text-orange-600 transition-colors">Experience</button>
                    <button onclick="navTo('awards')" class="text-gray-600 hover:text-orange-600 transition-colors">Credentials</button>
                </div>
                <div class="flex items-center md:hidden">
                    <button id="mobile-menu-btn" class="text-gray-600 hover:text-gray-900 focus:outline-none">
                        <!-- Hamburger Icon -->
                        <span class="text-2xl">☰</span>
                    </button>
                </div>
            </div>
        </div>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t border-gray-100 p-4 space-y-2 shadow-lg">
            <button onclick="navTo('dashboard')" class="block w-full text-left px-3 py-2 rounded-md hover:bg-orange-50 text-gray-700">Dashboard</button>
            <button onclick="navTo('skills')" class="block w-full text-left px-3 py-2 rounded-md hover:bg-orange-50 text-gray-700">Technical Arsenal</button>
            <button onclick="navTo('experience')" class="block w-full text-left px-3 py-2 rounded-md hover:bg-orange-50 text-gray-700">Experience</button>
            <button onclick="navTo('awards')" class="block w-full text-left px-3 py-2 rounded-md hover:bg-orange-50 text-gray-700">Credentials</button>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full">

        <!-- Header Section -->
        <header class="mb-12 text-center md:text-left md:flex md:justify-between md:items-end border-b border-gray-200 pb-8">
            <div>
                <h1 class="text-4xl md:text-5xl font-bold text-slate-900 mb-2">Sachin Chaugule</h1>
                <p class="text-xl text-orange-600 font-medium">Graphic Design & Development Specialist</p>
                <p class="text-slate-500 mt-2 max-w-2xl">
                    Specializing in brand imagery curation, workflow optimization, and high-impact visual content for APAC markets (Japan, South Korea).
                </p>
            </div>
            <div class="mt-6 md:mt-0 flex flex-col items-center md:items-end space-y-2">
                <a href="https://www.behance.net/gallery/238331813/Graphic-design-portfolio-2025" target="_blank" class="text-sm font-semibold text-slate-600 hover:text-orange-600 transition flex items-center gap-2">
                    🖼️ Behance Portfolio
                </a>
                <a href="mailto:123Sachin.sc@gmail.com" class="text-sm font-semibold text-slate-600 hover:text-orange-600 transition flex items-center gap-2">
                    ✉️ 123Sachin.sc@gmail.com
                </a>
                <span class="text-sm text-slate-600">📍 Mumbai, India</span>
                <span class="text-sm text-slate-600">📱 +91 8108271159</span>
            </div>
        </header>

        <!-- Visualization & Content Choices:
             1. Dashboard: Uses 'Big Number' cards for immediate impact (Years, Awards) and a text summary for context.
             2. Skills: Uses a Radar Chart (Chart.js) to show the balance between Design, Video, and UI tools. This is better than a list because it shows versatility visually.
             3. Competencies: A Donut Chart (Chart.js) to visualize the 'Core Competencies' list, showing he is not just a designer but a manager/collaborator.
             4. Experience: An interactive card system. No complex charts here, text is king for explaining the 'South Korea Project'.
             NO SVG or Mermaid used. All graphics are Canvas or HTML/CSS.
        -->

        <!-- DASHBOARD VIEW -->
        <section id="dashboard" class="space-y-8 animate-fade-in">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-slate-800">Executive Overview</h2>
                <p class="text-slate-600 mt-1">A snapshot of professional impact and key metrics derived from career history.</p>
            </div>

            <!-- Metrics Grid -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 card-hover text-center">
                    <div class="text-4xl font-bold text-orange-500 mb-1">4+</div>
                    <div class="text-sm text-gray-500 uppercase tracking-wide font-semibold">Years Experience</div>
                    <div class="text-xs text-gray-400 mt-2">Nielsen (2021-2025)</div>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 card-hover text-center">
                    <div class="text-4xl font-bold text-orange-500 mb-1">3x</div>
                    <div class="text-sm text-gray-500 uppercase tracking-wide font-semibold">Best Performing Employee</div>
                    <div class="text-xs text-gray-400 mt-2">Awarded at Nielsen</div>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 card-hover text-center">
                    <div class="text-4xl font-bold text-orange-500 mb-1">9+</div>
                    <div class="text-sm text-gray-500 uppercase tracking-wide font-semibold">Design Tools Mastered</div>
                    <div class="text-xs text-gray-400 mt-2">Adobe Suite, Figma, etc.</div>
                </div>
            </div>

            <!-- Competency Distribution Chart -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mt-8">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                    <h3 class="text-lg font-semibold text-slate-800 mb-4">Core Competency Distribution</h3>
                    <p class="text-sm text-slate-500 mb-6">breakdown of professional focus areas based on role responsibilities.</p>
                    <div class="chart-container">
                        <canvas id="competencyChart"></canvas>
                    </div>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex flex-col justify-center">
                    <h3 class="text-lg font-semibold text-slate-800 mb-4">Professional Profile Summary</h3>
                    <div class="prose prose-slate text-sm leading-relaxed">
                        <p class="mb-4">
                            Creative and detail-oriented professional with extensive experience managing and curating high-quality brand imagery across <strong class="text-orange-600">APAC markets</strong>, specifically Japan and South Korea.
                        </p>
                        <p class="mb-4">
                            Recognized for excellence with multiple performance awards, I possess a strong track record of <strong class="text-orange-600">streamlining workflows</strong> and managing projects end-to-end. I bridge the gap between creative execution and operational efficiency, ensuring delivery on tight deadlines while maintaining brand integrity.
                        </p>
                        <div class="bg-orange-50 border-l-4 border-orange-500 p-4 mt-4">
                            <p class="font-bold text-orange-800 text-xs uppercase">Key Strength</p>
                            <p class="text-orange-900 font-medium">Rapid mobilization of teams under manpower constraints (South Korea Project).</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SKILLS SECTION -->
        <section id="skills" class="space-y-8 hidden-content animate-fade-in">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-slate-800">Technical Proficiency</h2>
                <p class="text-slate-600 mt-1">Deep dive into software capabilities and toolsets.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- Radar Chart -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                    <h3 class="text-lg font-semibold text-slate-800 mb-4">Software Skill Matrix</h3>
                    <p class="text-sm text-slate-500 mb-4">Relative proficiency across key design and productivity tools.</p>
                    <div class="chart-container">
                        <canvas id="skillsRadar"></canvas>
                    </div>
                </div>

                <!-- Interactive Skill Lists -->
                <div class="space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 card-hover cursor-pointer" onclick="toggleSkillDetail('design-detail')">
                        <div class="flex justify-between items-center mb-2">
                            <h3 class="text-lg font-bold text-slate-800">🎨 Design & Multimedia</h3>
                            <span class="text-orange-500 text-sm">View List ▼</span>
                        </div>
                        <div class="flex flex-wrap gap-2 mb-3">
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Photoshop</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Illustrator</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">After Effects</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Figma</span>
                        </div>
                        <div id="design-detail" class="hidden text-sm text-slate-600 mt-3 pt-3 border-t border-gray-100">
                            <ul class="list-disc pl-5 space-y-1">
                                <li><strong>Adobe Creative Suite:</strong> Advanced Bootcamp (2025) in After Effects, expert in PS/AI.</li>
                                <li><strong>UI/UX:</strong> Experience with Figma and Adobe XD for interface design.</li>
                                <li><strong>Video:</strong> Premiere Pro editing capabilities.</li>
                                <li><strong>Other:</strong> Lightroom, Canva, InDesign.</li>
                            </ul>
                        </div>
                    </div>

                    <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 card-hover cursor-pointer" onclick="toggleSkillDetail('prod-detail')">
                        <div class="flex justify-between items-center mb-2">
                            <h3 class="text-lg font-bold text-slate-800">🚀 Productivity & Ops</h3>
                            <span class="text-orange-500 text-sm">View List ▼</span>
                        </div>
                        <div class="flex flex-wrap gap-2 mb-3">
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Excel</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Jira</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Teams</span>
                            <span class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-xs font-medium">Prompt Engineering</span>
                        </div>
                        <div id="prod-detail" class="hidden text-sm text-slate-600 mt-3 pt-3 border-t border-gray-100">
                            <ul class="list-disc pl-5 space-y-1">
                                <li><strong>Data Management:</strong> Daily reporting and documentation using MS Excel.</li>
                                <li><strong>Collaboration:</strong> Slack, Dropbox, OneDrive, Google Workspace.</li>
                                <li><strong>AI:</strong> Certification in "Master Prompt Engineering".</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- EXPERIENCE SECTION -->
        <section id="experience" class="space-y-8 hidden-content animate-fade-in">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-slate-800">Professional Journey</h2>
                <p class="text-slate-600 mt-1">Detailed breakdown of roles, projects, and impact at Nielsen.</p>
            </div>

            <!-- Timeline Item -->
            <div class="relative border-l-2 border-orange-200 ml-4 pl-8 pb-12">
                <div class="absolute -left-2.5 top-0 w-5 h-5 bg-orange-500 rounded-full border-4 border-white"></div>
                
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                    <div class="flex flex-col md:flex-row md:justify-between md:items-start mb-4">
                        <div>
                            <h3 class="text-xl font-bold text-slate-800">Image Editor - APAC Markets</h3>
                            <p class="text-orange-600 font-medium">Nielsen</p>
                        </div>
                        <span class="text-sm text-gray-400 font-mono mt-1 md:mt-0">2021 - Oct 2025</span>
                    </div>

                    <!-- Tabs for Job Details -->
                    <div class="flex space-x-6 border-b border-gray-100 mb-4 text-sm">
                        <button class="pb-2 active-tab transition-colors" onclick="switchExpTab(this, 'roles')">Responsibilities</button>
                        <button class="pb-2 text-gray-500 hover:text-orange-600 transition-colors" onclick="switchExpTab(this, 'achievements')">Key Achievements</button>
                    </div>

                    <div id="roles" class="exp-content">
                        <ul class="space-y-3 text-slate-600 text-sm">
                            <li class="flex items-start">
                                <span class="mr-2 text-orange-500">▪</span>
                                Edit, curate, and maintain high-quality brand imagery for Japan, South Korea, and APAC markets.
                            </li>
                            <li class="flex items-start">
                                <span class="mr-2 text-orange-500">▪</span>
                                Review and interpret client briefs to execute design requirements aligned with strict brand standards.
                            </li>
                            <li class="flex items-start">
                                <span class="mr-2 text-orange-500">▪</span>
                                Perform daily reporting, documentation, and data entry using Microsoft Excel.
                            </li>
                            <li class="flex items-start">
                                <span class="mr-2 text-orange-500">▪</span>
                                Collaborate with cross-functional teams to develop presentation materials and expand image databases.
                            </li>
                        </ul>
                    </div>

                    <div id="achievements" class="exp-content hidden">
                        <ul class="space-y-4 text-slate-600 text-sm">
                            <li class="bg-orange-50 p-3 rounded-lg border border-orange-100">
                                <strong class="block text-orange-800 mb-1">South Korea Project Leadership</strong>
                                Led a critical project under severe manpower constraints by rapidly mobilizing and training a backup team, ensuring on-time delivery despite heavy workload.
                            </li>
                            <li class="bg-gray-50 p-3 rounded-lg border border-gray-100">
                                <strong class="block text-gray-800 mb-1">Workflow Optimization</strong>
                                Streamlined workflows for multiple market teams by acquiring new skills and managing projects end-to-end, enhancing operational efficiency.
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- AWARDS & CERTS -->
        <section id="awards" class="space-y-8 hidden-content animate-fade-in">
             <div class="mb-6">
                <h2 class="text-2xl font-bold text-slate-800">Credentials & Recognition</h2>
                <p class="text-slate-600 mt-1">Formal education, certifications, and awards received.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Certifications -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                    <h3 class="text-lg font-bold text-slate-800 mb-4 border-b pb-2">Certifications</h3>
                    <div class="space-y-4">
                        <div class="flex items-start">
                            <div class="bg-orange-100 text-orange-600 p-2 rounded-lg mr-4 text-xs font-bold">2025</div>
                            <div>
                                <h4 class="font-semibold text-sm">Adobe After Effects CC Bootcamp: Advanced</h4>
                                <p class="text-xs text-gray-500">Udemy</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="bg-orange-100 text-orange-600 p-2 rounded-lg mr-4 text-xs font-bold">AI</div>
                            <div>
                                <h4 class="font-semibold text-sm">Master Prompt Engineering</h4>
                                <p class="text-xs text-gray-500">Udemy</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="bg-orange-100 text-orange-600 p-2 rounded-lg mr-4 text-xs font-bold">GD</div>
                            <div>
                                <h4 class="font-semibold text-sm">Graphic Designing Certification</h4>
                                <p class="text-xs text-gray-500">Shankar Multimedia Institute</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Education -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                     <h3 class="text-lg font-bold text-slate-800 mb-4 border-b pb-2">Education</h3>
                     <div class="flex items-start">
                        <div class="bg-slate-100 text-slate-600 p-2 rounded-lg mr-4 text-2xl">🎓</div>
                        <div>
                            <h4 class="font-semibold text-slate-800">Bachelor of Commerce (B.Com)</h4>
                            <p class="text-sm text-gray-600">Vidya Vikas Universal College, Mumbai</p>
                            <p class="text-xs text-gray-400 mt-1">Graduated 2020</p>
                        </div>
                    </div>
                </div>

                <!-- Awards -->
                <div class="bg-gradient-to-br from-slate-800 to-slate-900 p-6 rounded-xl shadow-md border border-gray-700 text-white md:col-span-2">
                    <h3 class="text-lg font-bold text-white mb-4">🏆 Awards & Honors</h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div class="bg-white/10 p-4 rounded-lg backdrop-blur-sm">
                            <p class="font-bold text-orange-400">Best Performing Employee (x3)</p>
                            <p class="text-xs text-gray-300 mt-1">Recognized three separate times at Nielsen for outstanding contribution and efficiency.</p>
                        </div>
                        <div class="bg-white/10 p-4 rounded-lg backdrop-blur-sm">
                            <p class="font-bold text-orange-400">CCL Cricket Tournament Winner</p>
                            <p class="text-xs text-gray-300 mt-1">Represented office team in 2024, demonstrating teamwork and competitive spirit.</p>
                        </div>
                        <!-- New Behance Portfolio Link Card -->
                        <a href="https://www.behance.net/gallery/238331813/Graphic-design-portfolio-2025" target="_blank" class="bg-orange-600/90 p-4 rounded-lg backdrop-blur-sm hover:bg-orange-700 transition-colors block">
                            <p class="font-bold text-white">View Design Portfolio</p>
                            <p class="text-xs text-orange-100 mt-1">Direct link to Behance for visual work samples.</p>
                        </a>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-gray-200 mt-auto">
        <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8 flex justify-center text-xs text-gray-400">
            <p>© 2025 Sachin Chaugule Interactive Portfolio. Generated for Evoplay Application.</p>
        </div>
    </footer>

    <!-- JavaScript Logic -->
    <script>
        // --- State Management ---
        const state = {
            currentTab: 'dashboard',
            chartsInitialized: false
        };

        // --- Data Storage ---
        const competencyData = {
            labels: ['Brand Imagery', 'Project Mgmt', 'UI/UX Design', 'Data/Reporting', 'Team Coord'],
            data: [35, 25, 15, 15, 10], // Estimated split based on resume emphasis
            colors: ['#ea580c', '#f97316', '#fb923c', '#fdba74', '#94a3b8']
        };

        const skillsData = {
            labels: ['Photoshop', 'Illustrator', 'After Effects', 'Figma', 'Excel', 'Jira'],
            data: [95, 90, 85, 80, 85, 75], // High proficiency implied by "Skilled in" and certifications
        };

        // --- Navigation Logic ---
        function navTo(sectionId) {
            // Hide all sections
            document.querySelectorAll('main > section').forEach(el => {
                el.classList.add('hidden-content');
                el.classList.remove('block');
            });

            // Show target section
            const target = document.getElementById(sectionId);
            if(target) {
                target.classList.remove('hidden-content');
                target.classList.add('block');
            }

            // Update mobile menu visibility
            document.getElementById('mobile-menu').classList.add('hidden');

            // Initialize charts if entering dashboard or skills for the first time
            if (!state.chartsInitialized) {
                initCharts();
                state.chartsInitialized = true;
            } else {
                // Resize charts slightly to force redraw in case of layout shifts
                if (sectionId === 'skills' && skillsChart) skillsChart.resize();
                if (sectionId === 'dashboard' && compChart) compChart.resize();
            }

            state.currentTab = sectionId;
        }

        // --- Mobile Menu Toggle ---
        document.getElementById('mobile-menu-btn').addEventListener('click', () => {
            document.getElementById('mobile-menu').classList.toggle('hidden');
        });

        // --- Interactive Details ---
        function toggleSkillDetail(id) {
            const el = document.getElementById(id);
            if (el.classList.contains('hidden')) {
                el.classList.remove('hidden');
            } else {
                el.classList.add('hidden');
            }
        }

        function switchExpTab(btn, tabId) {
            // Reset button styles
            const parent = btn.parentElement;
            parent.querySelectorAll('button').forEach(b => {
                b.classList.remove('active-tab', 'text-orange-600', 'font-semibold');
                b.classList.add('text-gray-500');
            });
            
            // Set active button style
            btn.classList.add('active-tab');
            btn.classList.remove('text-gray-500');

            // Show content
            const container = btn.closest('.bg-white');
            container.querySelectorAll('.exp-content').forEach(c => c.classList.add('hidden'));
            document.getElementById(tabId).classList.remove('hidden');
        }

        // --- Charts Implementation (Chart.js) ---
        let compChart, skillsChart;

        function initCharts() {
            // Competency Donut Chart
            const ctxComp = document.getElementById('competencyChart');
            if (ctxComp) {
                compChart = new Chart(ctxComp, {
                    type: 'doughnut',
                    data: {
                        labels: competencyData.labels,
                        datasets: [{
                            data: competencyData.data,
                            backgroundColor: competencyData.colors,
                            borderWidth: 0,
                            hoverOffset: 4
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: { position: 'right', labels: { boxWidth: 12, font: { size: 11 } } },
                            tooltip: {
                                callbacks: {
                                    label: function(context) {
                                        return ` ${context.label}: ${context.raw}% Focus`;
                                    }
                                }
                            }
                        }
                    }
                });
            }

            // Skills Radar Chart
            const ctxSkills = document.getElementById('skillsRadar');
            if (ctxSkills) {
                skillsChart = new Chart(ctxSkills, {
                    type: 'radar',
                    data: {
                        labels: skillsData.labels,
                        datasets: [{
                            label: 'Proficiency Level',
                            data: skillsData.data,
                            fill: true,
                            backgroundColor: 'rgba(234, 88, 12, 0.2)',
                            borderColor: 'rgba(234, 88, 12, 1)',
                            pointBackgroundColor: 'rgba(234, 88, 12, 1)',
                            pointBorderColor: '#fff',
                            pointHoverBackgroundColor: '#fff',
                            pointHoverBorderColor: 'rgba(234, 88, 12, 1)'
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        elements: { line: { borderWidth: 2 } },
                        scales: {
                            r: {
                                angleLines: { display: true, color: '#e5e7eb' },
                                suggestedMin: 0,
                                suggestedMax: 100,
                                ticks: { display: false } // Hide numbers for cleaner UI
                            }
                        },
                        plugins: {
                            legend: { display: false }
                        }
                    }
                });
            }
        }

        // Initial Load
        window.addEventListener('DOMContentLoaded', () => {
            initCharts();
            state.chartsInitialized = true;
        });

    </script>
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. All visuals via Chart.js Canvas or HTML/CSS -->
</body>
</html>
