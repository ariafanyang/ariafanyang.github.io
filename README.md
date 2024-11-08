<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fan (Aria) Yang - Data Science & Architecture</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.2.19/tailwind.min.css" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.min.js"></script>
    <style>
        .geometric-bg {
            background-image: linear-gradient(30deg, #e0f7fa 12%, transparent 12.5%, transparent 87%, #e0f7fa 87.5%, #e0f7fa),
            linear-gradient(150deg, #e0f7fa 12%, transparent 12.5%, transparent 87%, #e0f7fa 87.5%, #e0f7fa),
            linear-gradient(30deg, #e0f7fa 12%, transparent 12.5%, transparent 87%, #e0f7fa 87.5%, #e0f7fa),
            linear-gradient(150deg, #e0f7fa 12%, transparent 12.5%, transparent 87%, #e0f7fa 87.5%, #e0f7fa),
            linear-gradient(60deg, #e0f7fa77 25%, transparent 25.5%, transparent 75%, #e0f7fa77 75%, #e0f7fa77),
            linear-gradient(60deg, #e0f7fa77 25%, transparent 25.5%, transparent 75%, #e0f7fa77 75%, #e0f7fa77);
            background-size: 40px 70px;
            background-position: 0 0, 0 0, 20px 35px, 20px 35px, 0 0, 20px 35px;
            position: relative;
            overflow: hidden;
        }

        .gradient-text {
            background: linear-gradient(120deg, #039be5, #0288d1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.3;
        }
    </style>
</head>
<body class="bg-white">

    <!-- Particle Background -->
    <div id="canvas-container"></div>

    <!-- Fixed Navigation Bar -->
    <nav class="fixed top-0 w-full bg-white shadow-md z-50">
        <div class="max-w-7xl mx-auto px-4">
            <div class="flex justify-between items-center h-16">
                <span class="text-xl font-bold gradient-text">Fan (Aria) Yang</span>
                <div class="flex space-x-8">
                    <a href="#about" class="text-gray-600 hover:text-blue-600 transition-colors">About</a>
                    <a href="#education" class="text-gray-600 hover:text-blue-600 transition-colors">Education</a>
                    <a href="#experience" class="text-gray-600 hover:text-blue-600 transition-colors">Experience</a>
                    <a href="#summer-schools" class="text-gray-600 hover:text-blue-600 transition-colors">Summer Schools</a>
                    <a href="#skills" class="text-gray-600 hover:text-blue-600 transition-colors">Skills</a>
                    <a href="#contact" class="text-gray-600 hover:text-blue-600 transition-colors">Contact</a>
                </div>
            </div>
        </div>
    </nav>

    <!-- About Section -->
    <div id="about" class="geometric-bg min-h-screen flex flex-col items-center justify-center text-center relative mt-16">
        <div class="max-w-4xl px-4">
            <h1 class="text-5xl font-bold mb-6 gradient-text">About</h1>
            <p class="text-lg text-gray-600 leading-relaxed mb-6">
                I am a Master's student in Computational Social Science at UC San Diego, with a background in architecture and urban design. 
                My work focuses on blending the principles of design with data science to uncover new insights into how people interact with their environments.
            </p>
            <p class="text-lg text-gray-600 leading-relaxed mb-6">
                I am currently working on a capstone project titled "DeepNominate: Deep Learning for Ideal-Point Estimation," 
                which applies deep learning techniques to analyze both non-tabular and tabular data, specifically in the context of political ideal points and decision-making patterns. 
                This project aligns with my broader interest in using machine learning and data science to analyze social dynamics and spatial patterns.
            </p>
            <p class="text-lg text-gray-600 leading-relaxed">
                My goal is to bridge the gap between built environments and computational analysis, creating data-driven insights 
                that support sustainable urban development and informed decision-making in social science.
            </p>
        </div>
    </div>

    <script>
        let sketch = function(p) {
            let particles = [];
            
            p.setup = function() {
                let canvas = p.createCanvas(p.windowWidth, p.windowHeight);
                canvas.parent('canvas-container');
                for(let i = 0; i < 100; i++) {
                    particles.push({
                        x: p.random(p.width),
                        y: p.random(p.height),
                        size: p.random(4, 8),
                        speedX: p.random(-0.7, 0.7),
                        speedY: p.random(-0.7, 0.7)
                    });
                }
            };
            
            p.draw = function() {
                p.clear();
                for(let particle of particles) {
                    p.noStroke();
                    p.fill(3, 155, 229, 150);
                    p.circle(particle.x, particle.y, particle.size);
                    
                    particle.x += particle.speedX;
                    particle.y += particle.speedY;
                    
                    if(particle.x < 0 || particle.x > p.width) particle.speedX *= -1;
                    if(particle.y < 0 || particle.y > p.height) particle.speedY *= -1;
                }
            };
            
            p.windowResized = function() {
                p.resizeCanvas(p.windowWidth, p.windowHeight);
            };
        };
        
        new p5(sketch);
    </script>

    <!-- Education Section -->
    <section id="education" class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4">
            <h2 class="text-4xl font-bold mb-12 text-center gradient-text">Education</h2>
            <div class="space-y-6">
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">University of California San Diego</h3>
                    <p>Master of Science in Computational Social Science (Jul 2024 - Present)</p>
                    <ul class="list-disc list-inside text-gray-600">
                        <li>Courses: Machine Learning for Social Scientists, Statistical Computing and Inference from Data I</li>
                        <li>Capstone Project: "DeepNominate: Deep Learning for Ideal-Point Estimation"</li>
                    </ul>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Swiss Federal Institute of Technology Zurich</h3>
                    <p>Master of Advanced Studies in Housing (Sep 2020 - Mar 2022)</p>
                    <p class="text-gray-600">Courses: Sociology, Planetary Urbanization, Urban Systems, Urban Design III, Housing Research Methods, Architecture of Territory</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Dalian University of Technology</h3>
                    <p>Bachelor of Architecture (Sep 2014 - Jun 2019)</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Professional Experience Section -->
    <section id="experience" class="py-20">
        <div class="max-w-7xl mx-auto px-4">
            <h2 class="text-4xl font-bold mb-12 text-center gradient-text">Professional Experience</h2>
            <div class="space-y-6">
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Office of the High Commissioner for Human Rights (UN Human Rights Office)</h3>
                    <p>Visualization and Design Intern at the Emergency Response Section (Apr 2024 - Jun 2024)</p>
                    <ul class="list-disc list-inside text-gray-600">
                        <li>Prepared reports and factsheets for human rights protection.</li>
                        <li>Created visualizations including maps and diagrams to support decision-making.</li>
                    </ul>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Dalian Jianfa Institute of Architectural Design</h3>
                    <p>Junior Architect (Sep 2022 - Jul 2023; Sep 2023 - Mar 2024)</p>
                    <ul class="list-disc list-inside text-gray-600">
                        <li>Developed schematic design for the adaptive reuse of dilapidated residential community.</li>
                        <li>Prepared presentation documents for architectural design proposals.</li>
                        <li>Created conceptual models and plans for an urban regeneration project.</li>
                        <li>Produced architectural plans and masterplans for a residential community design project.</li>
                    </ul>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">DSW Architekten</h3>
                    <p>Architectural Intern (May 2021 - Sep 2021)</p>
                    <ul class="list-disc list-inside text-gray-600">
                        <li>Developed conceptual design for a school design competition. Won the Second Prize.</li>
                        <li>Made digital models and drew construction details, plans, and sections for a house renovation project.</li>
                        <li>Designed plans, facades, and presentations for two office building extension projects.</li>
                        <li>Prepared presentation documents and designed masterplans for a Swiss bridge design competition.</li>
                    </ul>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Dalian Jianfa Institute of Architectural Design</h3>
                    <p>Architectural Intern (Sep 2018 - Dec 2018)</p>
                    <ul class="list-disc list-inside text-gray-600">
                        <li>Assessed and applied building energy-saving standards for a recreation center in Chongqing.</li>
                        <li>Designed and made 3D models for a university campus entrance in Lvshun.</li>
                        <li>Produced plans for the adaptive reuse of a youth hostel in Dalian.</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Summer Schools Section -->
    <section id="summer-schools" class="py-12 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4">
            <h2 class="text-4xl font-bold mb-8 text-center gradient-text">Summer Schools</h2>
            <div class="grid gap-6">
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Moscow State University of Civil Engineering</h3>
                    <p>Summer School (Aug 2019 - Sep 2019)</p>
                    <p class="text-gray-600">Course Title: 20th Century Mass-Housing RE3 (RE-valorization/RE-vitalization/RE-storation)</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">Weimar Bauhaus University</h3>
                    <p>Bauhaus Summer School (Aug 2018 - Sep 2018)</p>
                    <p class="text-gray-600">Courses: Breakup - Envisioning an Alternative Architecture (3 ECTS), Moving Traces - Design Principles and Elements (3 ECTS)</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-sm">
                    <h3 class="text-2xl font-bold">University of British Columbia</h3>
                    <p>Urban Design Summer Program (Jul 2017 - Aug 2017)</p>
                    <p class="text-gray-600">Courses: Sustainability by Design (Grade: 86%), Perspectives on City Making (92%)</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4">
            <h2 class="text-4xl font-bold mb-12 text-center gradient-text">Skills & Tools</h2>
            <div class="flex flex-wrap gap-3 justify-center">
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">Python</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">R</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">GIS</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">Deep Learning</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">Data Visualization</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">AutoCAD</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">SketchUp</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">Photoshop</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">InDesign</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">QGIS</span>
                <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full">3D Modeling</span>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <h2 class="text-4xl font-bold mb-8 gradient-text">Get in Touch</h2>
            <p class="text-xl text-gray-600 mb-12">Reach out to discuss data science, architecture, or collaborative projects.</p>
            <a href="mailto:ariafanyang@hotmail.com" class="px-8 py-4 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors">
                Email Me
            </a>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 bg-white">
        <div class="max-w-7xl mx-auto px-4">
            <p class="text-center text-gray-600">© 2024 Fan Yang. All rights reserved.</p>
        </div>
    </footer>

</body>
</html>
