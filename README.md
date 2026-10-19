<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MEDIA PEMBELAJARAN INTERAKTIF ATLETIK: LEMPAR CAKRAM</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        navy: {
                            800: '#1e3a8a',
                            900: '#0f172a',
                        },
                        sportBlue: {
                            500: '#0284c7',
                            600: '#0284c7',
                            700: '#0369a1',
                        },
                        accentOrange: {
                            500: '#f97316',
                            600: '#ea580c',
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        /* Custom animations & smooth transitions */
        .fade-in {
            animation: fadeIn 0.3s ease-in-out forwards;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-100 text-slate-800 font-sans min-h-screen flex flex-col selection:bg-orange-500 selection:text-white">

    <!-- Header / Navbar -->
    <header class="bg-navy-900 text-white shadow-lg sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchView('dashboard')">
                <div class="bg-gradient-to-tr from-accentOrange-500 to-amber-400 p-2.5 rounded-xl shadow-md text-white font-black text-xl flex items-center justify-center w-12 h-12">
                    <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <circle cx="12" cy="12" r="9" stroke-width="2.5"></circle>
                        <circle cx="12" cy="12" r="3" fill="currentColor"></circle>
                    </svg>
                </div>
                <div>
                    <h1 class="font-extrabold text-lg sm:text-xl tracking-tight leading-none text-white">LEMPAR CAKRAM</h1>
                    <p class="text-xs text-orange-400 font-medium mt-1">PJOK Kelas XII SMA</p>
                </div>
            </div>

            <!-- Desktop Nav Menu -->
            <nav class="hidden md:flex items-center space-x-1 lg:space-x-2">
                <button onclick="switchView('dashboard')" id="nav-dashboard" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold transition-all hover:bg-slate-800 text-slate-200">Beranda</button>
                <button onclick="switchView('learning')" id="nav-learning" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold transition-all hover:bg-slate-800 text-slate-200">Belajar</button>
                <button onclick="switchView('play')" id="nav-play" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold transition-all hover:bg-slate-800 text-slate-200">Bermain</button>
                <button onclick="switchView('scores')" id="nav-scores" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold transition-all hover:bg-slate-800 text-slate-200">Skor</button>
                <button onclick="switchView('developer')" id="nav-developer" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold transition-all hover:bg-slate-800 text-slate-200">Pengembang</button>
            </nav>

            <!-- Top Header Controls (Audio & Fullscreen) -->
            <div class="flex items-center space-x-2">
                <button id="audio-toggle-btn" onclick="toggleAudio()" aria-label="Audio Toggle" class="p-2.5 bg-slate-800 hover:bg-slate-700 text-slate-200 rounded-xl transition-all flex items-center justify-center text-sm font-medium border border-slate-700 shadow-sm" title="Aktifkan/Matikan Suara">
                    <svg id="audio-icon-on" class="w-5 h-5 text-emerald-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"></path>
                    </svg>
                    <svg id="audio-icon-off" class="w-5 h-5 text-rose-400 hidden" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2"></path>
                    </svg>
                </button>
                <button onclick="toggleFullscreen()" aria-label="Fullscreen Toggle" class="p-2.5 bg-slate-800 hover:bg-slate-700 text-slate-200 rounded-xl transition-all flex items-center justify-center text-sm font-medium border border-slate-700 shadow-sm" title="Layar Penuh">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8V4m0 0h4M4 4l5 5m11-1V4m0 0h-4m4 0l-5 5M4 16v4m0 0h4m-4 0l5-5m11 5l-5-5m5 5v-4m0 4h-4"></path>
                    </svg>
                </button>
                <!-- Mobile Hamburger Button -->
                <button onclick="toggleMobileMenu()" aria-label="Mobile Menu" class="md:hidden p-2.5 bg-slate-800 hover:bg-slate-700 text-slate-200 rounded-xl transition-all">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile Menu Drawer -->
        <div id="mobile-menu" class="hidden md:hidden bg-slate-900 border-t border-slate-800 px-4 pt-2 pb-4 space-y-1">
            <button onclick="switchView('dashboard'); toggleMobileMenu();" class="w-full text-left px-3 py-2 rounded-lg text-sm font-semibold hover:bg-slate-800">Beranda</button>
            <button onclick="switchView('learning'); toggleMobileMenu();" class="w-full text-left px-3 py-2 rounded-lg text-sm font-semibold hover:bg-slate-800">Belajar</button>
            <button onclick="switchView('play'); toggleMobileMenu();" class="w-full text-left px-3 py-2 rounded-lg text-sm font-semibold hover:bg-slate-800">Bermain</button>
            <button onclick="switchView('scores'); toggleMobileMenu();" class="w-full text-left px-3 py-2 rounded-lg text-sm font-semibold hover:bg-slate-800">Skor</button>
            <button onclick="switchView('developer'); toggleMobileMenu();" class="w-full text-left px-3 py-2 rounded-lg text-sm font-semibold hover:bg-slate-800">Pengembang</button>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 sm:py-8">

        <!-- VIEW: DASHBOARD -->
        <section id="view-dashboard" class="view-section fade-in space-y-8">
            <!-- Hero Banner Card -->
            <div class="relative overflow-hidden bg-gradient-to-r from-navy-900 via-blue-900 to-sportBlue-600 rounded-3xl shadow-2xl text-white p-6 sm:p-12">
                <div class="absolute right-0 top-0 bottom-0 w-1/3 opacity-20 hidden lg:flex items-center justify-center pointer-events-none">
                    <svg class="w-96 h-96 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <circle cx="12" cy="12" r="10" fill="none" stroke="currentColor" stroke-width="1.5"></circle>
                        <circle cx="12" cy="12" r="6" fill="none" stroke="currentColor" stroke-width="1.5"></circle>
                        <circle cx="12" cy="12" r="2" fill="currentColor"></circle>
                    </svg>
                </div>
                <div class="relative z-10 max-w-2xl space-y-4">
                    <div class="inline-flex items-center space-x-2 bg-orange-500/20 text-orange-400 px-3.5 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider border border-orange-500/30">
                        <span>PJOK | Kelas XII SMA</span>
                    </div>
                    <h2 class="text-3xl sm:text-5xl font-extrabold tracking-tight leading-tight">
                        MEDIA PEMBELAJARAN INTERAKTIF ATLETIK: LEMPAR CAKRAM
                    </h2>
                    <p class="text-slate-300 text-sm sm:text-base leading-relaxed">
                        Pelajari teknik, peralatan, dan prinsip dasar lempar cakram secara komprehensif. Uji pemahamanmu melalui permainan interaktif, kuis menantang, dan pantau progres belajarmu secara mandiri!
                    </p>
                    <div class="pt-4 flex flex-wrap gap-4">
                        <button onclick="switchView('learning')" class="bg-orange-500 hover:bg-orange-600 text-white font-bold px-6 py-3.5 rounded-xl shadow-lg transition-all flex items-center space-x-2 text-base transform hover:-translate-y-0.5">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
                            <span>Ayo Belajar</span>
                        </button>
                        <button onclick="checkLoginAndPlay()" class="bg-white hover:bg-slate-100 text-navy-900 font-bold px-6 py-3.5 rounded-xl shadow-lg transition-all flex items-center space-x-2 text-base transform hover:-translate-y-0.5">
                            <svg class="w-5 h-5 text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                            <span>Ayo Bermain</span>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Stats & Progress Overview Grid -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Progres Belajar Card -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="font-bold text-slate-900 text-base">Progres Belajar Materi</h3>
                            <span id="dash-learning-percent" class="text-xs font-bold px-2.5 py-1 bg-blue-50 text-blue-700 rounded-full">0% Selesai</span>
                        </div>
                        <div class="w-full bg-slate-100 rounded-full h-3 mb-3">
                            <div id="dash-learning-bar" class="bg-blue-600 h-3 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <p class="text-xs text-slate-500">Menyelesaikan checklist pemahaman pada setiap subbab materi.</p>
                    </div>
                    <button onclick="switchView('learning')" class="mt-6 text-sm font-semibold text-blue-600 hover:text-blue-700 flex items-center space-x-1">
                        <span>Lanjutkan Belajar</span>
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                    </button>
                </div>

                <!-- Status Permainan Card -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="font-bold text-slate-900 text-base">Status Peserta</h3>
                            <span id="dash-login-badge" class="text-xs font-bold px-2.5 py-1 bg-amber-50 text-amber-700 rounded-full">Belum Login</span>
                        </div>
                        <div id="dash-student-info" class="space-y-1 mb-3">
                            <p class="text-sm font-medium text-slate-700">Nama: <span id="dash-student-name" class="font-bold text-slate-900">-</span></p>
                            <p class="text-sm font-medium text-slate-700">Sekolah: <span id="dash-student-school" class="font-bold text-slate-900">-</span></p>
                        </div>
                        <p class="text-xs text-slate-500">Identitas digunakan untuk pencatatan skor latihan.</p>
                    </div>
                    <button onclick="checkLoginAndPlay()" class="mt-6 text-sm font-semibold text-orange-600 hover:text-orange-700 flex items-center space-x-1">
                        <span id="dash-play-btn-text">Mulai Bermain / Masuk</span>
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                    </button>
                </div>

                <!-- Total Skor Terbaik Card -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="font-bold text-slate-900 text-base">Skor Tertinggi</h3>
                            <span class="text-xs font-bold px-2.5 py-1 bg-emerald-50 text-emerald-700 rounded-full">Performa</span>
                        </div>
                        <div class="flex items-baseline space-x-2 mb-3">
                            <span id="dash-top-score" class="text-3xl font-extrabold text-navy-900">0</span>
                            <span class="text-sm text-slate-500 font-medium">/ 100 Poin</span>
                        </div>
                        <p class="text-xs text-slate-500">Akumulasi terbaik dari Matching, Urutan Teknik, dan Kuis.</p>
                    </div>
                    <button onclick="switchView('scores')" class="mt-6 text-sm font-semibold text-emerald-600 hover:text-emerald-700 flex items-center space-x-1">
                        <span>Lihat Riwayat Skor</span>
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                    </button>
                </div>
            </div>
        </section>

        <!-- VIEW: AYO BELAJAR (LEARNING) -->
        <section id="view-learning" class="view-section hidden fade-in space-y-6">
            <div class="bg-white p-6 sm:p-8 rounded-2xl shadow-sm border border-slate-200">
                <div class="flex flex-col md:flex-row md:items-center justify-between pb-6 border-b border-slate-100 gap-4">
                    <div>
                        <div class="text-xs font-bold text-orange-600 uppercase tracking-wider mb-1">Materi Pembelajaran PJOK</div>
                        <h2 class="text-2xl sm:text-3xl font-extrabold text-navy-900">Atletik: Lempar Cakram</h2>
                    </div>
                    <!-- Subchapter Tabs -->
                    <div class="flex flex-wrap gap-2">
                        <button onclick="switchSubTab('subA')" id="btn-subA" class="subtab-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-bold transition-all bg-blue-600 text-white shadow-sm">A. Pengertian</button>
                        <button onclick="switchSubTab('subB')" id="btn-subB" class="subtab-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-bold transition-all bg-slate-100 text-slate-700 hover:bg-slate-200">B. Teknik Dasar</button>
                        <button onclick="switchSubTab('subC')" id="btn-subC" class="subtab-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-bold transition-all bg-slate-100 text-slate-700 hover:bg-slate-200">C. Peralatan & Lapangan</button>
                        <button onclick="switchSubTab('subD')" id="btn-subD" class="subtab-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-bold transition-all bg-slate-100 text-slate-700 hover:bg-slate-200">D. Prinsip & Inti</button>
                    </div>
                </div>

                <!-- Subchapter Content Area -->
                <div class="py-6">
                    <!-- SUB A -->
                    <div id="content-subA" class="subtab-content space-y-6">
                        <h3 class="text-xl font-bold text-navy-900 border-l-4 border-orange-500 pl-3">A. Pengertian dan Hakikat Lempar Cakram</h3>
                        <p class="text-slate-600 leading-relaxed">
                            Lempar cakram (discus throw) merupakan salah satu nomor perlombaan atletik yang menuntut kekuatan, kecepatan rotasi, koordinasi tubuh, serta teknik pelepasan yang presisi untuk melempar benda berbentuk piringan sejauh mungkin ke sektor pendaratan yang ditentukan.
                        </p>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 pt-2">
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <h4 class="font-bold text-navy-900 mb-2 flex items-center space-x-2">
                                    <svg class="w-5 h-5 text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>Tujuan dan Prinsip Dasar</span>
                                </h4>
                                <ul class="space-y-2 text-sm text-slate-600 list-disc list-inside">
                                    <li>Mencapai jarak lemparan terjauh yang sah di dalam sektor sudut 34,92 derajat.</li>
                                    <li>Memanfaatkan gaya sentrifugal dan putaran badan secara optimal.</li>
                                    <li>Menjaga keseimbangan tubuh agar tidak keluar batas lingkaran lempar.</li>
                                </ul>
                            </div>
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <h4 class="font-bold text-navy-900 mb-2 flex items-center space-x-2">
                                    <svg class="w-5 h-5 text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>Sejarah Singkat</span>
                                </h4>
                                <p class="text-sm text-slate-600 leading-relaxed">
                                    Lempar cakram adalah salah satu cabang olahraga tertua yang telah dipertandingkan sejak zaman Olimpiade Kuno di Yunani (berasal dari kebiasaan melempar batu atau lempengan logam). Masuk ke dalam program Olimpiade modern sejak tahun 1896 di Athena.
                                </p>
                            </div>
                        </div>
                    </div>

                    <!-- SUB B -->
                    <div id="content-subB" class="subtab-content hidden space-y-6">
                        <h3 class="text-xl font-bold text-navy-900 border-l-4 border-orange-500 pl-3">B. Teknik Dasar Lempar Cakram</h3>
                        <p class="text-slate-600 leading-relaxed">
                            Penguasaan teknik yang benar sangat menentukan keberhasilan lemparan dan keselamatan atlet. Berikut adalah 5 tahapan utama teknik lempar cakram:
                        </p>
                        
                        <div class="space-y-4">
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <span class="text-xs font-bold text-orange-600 uppercase">Tahap 1</span>
                                <h4 class="font-bold text-navy-900 text-lg">Teknik Memegang Cakram</h4>
                                <p class="text-sm text-slate-600 mt-1">Cakram diletakkan pada ruas jari-jari tangan yang terakhir (ruas ujung). Jari-jari diregangkan menutupi tepi cakram, sementara ibu jari diletakkan santai di atas permukaan cakram untuk kestabilan.</p>
                                <div class="mt-3 grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Poin Penting:</strong> Pegangan tidak boleh terlalu kaku agar pergelangan tangan tetap fleksibel saat pelepasan.</div>
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Kesalahan Umum:</strong> Cakram dipegang terlalu dalam di telapak tangan sehingga sulit dilepas dengan putaran.</div>
                                </div>
                            </div>

                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <span class="text-xs font-bold text-orange-600 uppercase">Tahap 2</span>
                                <h4 class="font-bold text-navy-900 text-lg">Teknik Awalan dan Posisi Awal</h4>
                                <p class="text-sm text-slate-600 mt-1">Atlet berdiri di bagian belakang lingkaran lempar dengan membelakangi arah lemparan. Kaki dibuka selebar bahu, lutut sedikit ditekuk, dan melakukan ayunan pendahuluan (pre-swings) untuk mendapatkan ritme.</p>
                                <div class="mt-3 grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Poin Penting:</strong> Menjaga pusat gravitasi tetap rendah dan stabil sebelum memulai putaran.</div>
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Kesalahan Umum:</strong> Posisi badan terlalu tegak dan kaku saat memulai ayunan.</div>
                                </div>
                            </div>

                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <span class="text-xs font-bold text-orange-600 uppercase">Tahap 3</span>
                                <h4 class="font-bold text-navy-900 text-lg">Teknik Memutar Badan (Rotasi)</h4>
                                <p class="text-sm text-slate-600 mt-1">Melakukan putaran 1,5 putaran di dalam lingkaran dengan memanfaatkan tolakan kaki depan dan putaran poros tumit serta ujung kaki secara berkesinambungan.</p>
                                <div class="mt-3 grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Poin Penting:</strong> Koordinasi kecepatan putaran kaki dan pinggul mendahului posisi lengan pembawa cakram.</div>
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Kesalahan Umum:</strong> Kehilangan keseimbangan atau terpeleset di dalam lingkaran saat berputar.</div>
                                </div>
                            </div>

                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <span class="text-xs font-bold text-orange-600 uppercase">Tahap 4</span>
                                <h4 class="font-bold text-navy-900 text-lg">Teknik Melepaskan Cakram</h4>
                                <p class="text-sm text-slate-600 mt-1">Cakram dilepaskan dari tangan pada ketinggian sebahu atau sedikit di atasnya dengan sudut pelepasan ideal sekitar 30 hingga 35 derajat, disertai jentikan pergelangan tangan (flick) untuk memberikan putaran (spin).</p>
                                <div class="mt-3 grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Poin Penting:</strong> Cakram harus lepas dari jari telunjuk sebagai titik tumpuan terakhir putaran cakram.</div>
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Kesalahan Umum:</strong> Melempar terlalu mendatar (sudut terlalu kecil) atau terlalu tinggi melambung.</div>
                                </div>
                            </div>

                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <span class="text-xs font-bold text-orange-600 uppercase">Tahap 5</span>
                                <h4 class="font-bold text-navy-900 text-lg">Teknik Sikap Akhir dan Pemulihan</h4>
                                <p class="text-sm text-slate-600 mt-1">Setelah cakram lepas, atlet harus meredam momentum ke depan dengan memindahkan berat badan dan melangkah ke belakang di dalam lingkaran agar tidak menginjak garis atau keluar lingkaran.</p>
                                <div class="mt-3 grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Poin Penting:</strong> Menjaga keseimbangan total dan menunggu hingga cakram mendarat sebelum meninggalkan lingkaran dari bagian belakang.</div>
                                    <div class="bg-white p-3 rounded-xl border border-slate-200 text-slate-700"><strong>Kesalahan Umum:</strong> Melangkah keluar melewati garis depan lingkaran sehingga lemparan didiskualifikasi.</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- SUB C -->
                    <div id="content-subC" class="subtab-content hidden space-y-6">
                        <h3 class="text-xl font-bold text-navy-900 border-l-4 border-orange-500 pl-3">C. Peralatan dan Lapangan Lempar Cakram</h3>
                        <p class="text-slate-600 leading-relaxed">
                            Standar peralatan dan lapangan diatur ketat oleh World Athletics serta disesuaikan untuk tingkat pembelajaran di sekolah menengah.
                        </p>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 space-y-3">
                                <h4 class="font-bold text-navy-900 text-base">Spesifikasi Cakram (Discus)</h4>
                                <ul class="space-y-2 text-sm text-slate-600">
                                    <li><strong>Bahan:</strong> Badan kayu atau bahan synthetic dengan pinggiran melingkar dari besi/baja.</li>
                                    <li><strong>Kompetisi Resmi Senior Putra:</strong> Berat 2 kg, diameter 219–221 mm.</li>
                                    <li><strong>Kompetisi Resmi Senior Putri:</strong> Berat 1 kg, diameter 180–182 mm.</li>
                                    <li><strong>Pembelajaran SMA (Putra/Putri):</strong> Umumnya menggunakan berat 1 kg hingga 1,5 kg sesuai kapasitas fisik siswa.</li>
                                </ul>
                            </div>

                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 space-y-3">
                                <h4 class="font-bold text-navy-900 text-base">Area Lapangan & Sangkar (Cage)</h4>
                                <ul class="space-y-2 text-sm text-slate-600">
                                    <li><strong>Lingkaran Lempar:</strong> Diameter 2,5 meter terbuat dari besi, dikelilingi semen/beton.</li>
                                    <li><strong>Sangkar Pelindung (Cage):</strong> Berbentuk huruf U dengan jaring pengaman tinggi minimal 4 meter untuk keamanan penonton dan juri.</li>
                                    <li><strong>Sektor Pendaratan:</strong> Membentuk sudut 34,92 derajat dari pusat lingkaran lempar.</li>
                                </ul>
                            </div>
                        </div>

                        <!-- SVG Field Diagram -->
                        <div class="bg-slate-900 p-6 rounded-2xl text-white flex flex-col items-center justify-center space-y-4">
                            <h4 class="font-bold text-orange-400 text-sm tracking-wide uppercase">Diagram Sektor Lapangan Lempar Cakram</h4>
                            <div class="w-full max-w-md bg-slate-950 p-4 rounded-xl border border-slate-800 flex justify-center">
                                <svg viewBox="0 0 400 300" class="w-full h-auto max-h-64">
                                    <!-- Landing Sector -->
                                    <path d="M 200 270 L 40 40 A 250 250 0 0 1 360 40 Z" fill="#0369a1" opacity="0.3" stroke="#0284c7" stroke-width="2"/>
                                    <line x1="200" y1="270" x2="40" y2="40" stroke="#f97316" stroke-width="2" stroke-dasharray="5,5"/>
                                    <line x1="200" y1="270" x2="360" y2="40" stroke="#f97316" stroke-width="2" stroke-dasharray="5,5"/>
                                    <!-- Throwing Circle -->
                                    <circle cx="200" cy="270" r="25" fill="#1e293b" stroke="#f97316" stroke-width="3"/>
                                    <circle cx="200" cy="270" r="3" fill="#ffffff"/>
                                    <!-- Protective Cage U Shape -->
                                    <path d="M 175 245 L 175 295 M 225 245 L 225 295 M 175 245 Q 200 230 225 245" fill="none" stroke="#94a3b8" stroke-width="3"/>
                                    <!-- Labels -->
                                    <text x="200" y="274" fill="white" font-size="10" text-anchor="middle" font-weight="bold">Lingkaran</text>
                                    <text x="200" y="120" fill="white" font-size="12" text-anchor="middle" font-weight="bold">Sektor Pendaratan (34,92°)</text>
                                    <text x="75" y="70" fill="#f97316" font-size="10" font-weight="bold">Garis Batas</text>
                                </svg>
                            </div>
                            <p class="text-xs text-slate-400 text-center">Lemparan dinyatakan sah apabila cakram jatuh di dalam garis sudut sektor pendaratan dan atlet tidak menginjak garis luar lingkaran.</p>
                        </div>
                    </div>

                    <!-- SUB D -->
                    <div id="content-subD" class="subtab-content hidden space-y-6">
                        <h3 class="text-xl font-bold text-navy-900 border-l-4 border-orange-500 pl-3">D. Prinsip dan Keselamatan Latihan</h3>
                        <p class="text-slate-600 leading-relaxed">
                            Keberhasilan dalam lempar cakram sangat bergantung pada penerapan prinsip biomekanika dan prosedur keselamatan yang ketat di lapangan.
                        </p>
                        
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <h4 class="font-bold text-navy-900 mb-2">Prinsip Biomekanika</h4>
                                <ul class="space-y-1.5 text-sm text-slate-600 list-disc list-inside">
                                    <li><strong>Kecepatan Rotasi:</strong> Kecepatan putaran badan yang progresif dari lambat ke cepat.</li>
                                    <li><strong>Sudut Pelepasan:</strong> Sudut optimal 30°–35° untuk jarak maksimal.</li>
                                    <li><strong>Keseimbangan:</strong> Stabilitas titik berat badan selama rotasi.</li>
                                </ul>
                            </div>
                            <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200">
                                <h4 class="font-bold text-navy-900 mb-2">Keselamatan Latihan (Safety)</h4>
                                <ul class="space-y-1.5 text-sm text-slate-600 list-disc list-inside">
                                    <li>Pastikan sektor lemparan steril dari orang sebelum melempar.</li>
                                    <li>Gunakan sangkar pelindung saat latihan kelompok.</li>
                                    <li>Lakukan pemanasan (stretching) otot lengan, pinggang, dan kaki secara menyeluruh.</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Learning Progress Checklist & Navigation Footer -->
                <div class="pt-6 border-t border-slate-100 flex flex-col sm:flex-row items-center justify-between gap-4">
                    <label class="flex items-center space-x-3 cursor-pointer bg-blue-50 hover:bg-blue-100 px-4 py-3 rounded-xl border border-blue-200 transition-all select-none w-full sm:w-auto">
                        <input type="checkbox" id="learning-checkbox" onchange="updateLearningProgress()" class="w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-sm font-bold text-blue-900">Saya sudah memahami materi subbab ini</span>
                    </label>

                    <div class="flex items-center space-x-3 w-full sm:w-auto justify-end">
                        <button onclick="navigateSubTab(-1)" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold rounded-xl text-sm transition-all">Sebelumnya</button>
                        <button onclick="navigateSubTab(1)" class="px-4 py-2.5 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-xl text-sm transition-all">Berikutnya</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- VIEW: AYO BERMAIN / LOGIN & MENU PERMAINAN -->
        <section id="view-play" class="view-section hidden fade-in space-y-6">
            <!-- Login Sub-view -->
            <div id="play-login-card" class="max-w-md mx-auto bg-white p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="text-center space-y-2">
                    <div class="inline-flex bg-orange-500/10 text-orange-600 p-3 rounded-2xl mb-1">
                        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path></svg>
                    </div>
                    <h3 class="text-2xl font-extrabold text-navy-900">Siap Menguji Pemahamanmu?</h3>
                    <p class="text-sm text-slate-500">Masukkan identitas siswa untuk memulai latihan interaktif lempar cakram.</p>
                </div>

                <div id="login-error-msg" class="hidden bg-rose-50 text-rose-700 p-3 rounded-xl text-xs font-semibold border border-rose-200 text-center"></div>

                <div class="space-y-4">
                    <div>
                        <label class="block text-xs font-bold text-slate-700 uppercase tracking-wider mb-1">Nama Lengkap Siswa</label>
                        <input type="text" id="input-student-name" placeholder="Contoh: Budi Santoso" class="w-full px-4 py-3 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm font-medium">
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-700 uppercase tracking-wider mb-1">Nama Sekolah</label>
                        <input type="text" id="input-student-school" placeholder="Contoh: SMAN 1 Jakarta" class="w-full px-4 py-3 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm font-medium">
                    </div>
                    <button onclick="handleStudentLogin()" class="w-full bg-orange-500 hover:bg-orange-600 text-white font-bold py-3.5 rounded-xl shadow-lg transition-all text-base">Mulai Bermain</button>
                </div>
            </div>

            <!-- Game Dashboard Sub-view (Hidden until logged in) -->
            <div id="play-menu-card" class="hidden space-y-6">
                <div class="bg-gradient-to-r from-navy-900 to-blue-900 p-6 sm:p-8 rounded-3xl text-white flex flex-col sm:flex-row items-center justify-between gap-4 shadow-xl">
                    <div>
                        <div class="text-xs text-orange-400 font-bold uppercase">Selamat Datang, Peserta</div>
                        <h3 id="welcome-student-display" class="text-2xl font-extrabold">-</h3>
                        <p id="welcome-school-display" class="text-sm text-slate-300">-</p>
                    </div>
                    <button onclick="resetStudentLogin()" class="px-4 py-2 bg-slate-800 hover:bg-slate-700 text-slate-200 rounded-xl text-xs font-bold transition-all border border-slate-700">Ganti Identitas</button>
                </div>

                <h3 class="text-xl font-bold text-navy-900">Pilih Menu Permainan & Latihan</h3>
                
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <!-- Game 1 Card -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between hover:border-blue-500 transition-all cursor-pointer group" onclick="startMatchingGame()">
                        <div>
                            <div class="bg-blue-50 text-blue-600 p-3 rounded-xl w-fit mb-4 group-hover:bg-blue-600 group-hover:text-white transition-all">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"></path></svg>
                            </div>
                            <h4 class="font-bold text-navy-900 text-lg mb-1">Permainan 1: Mencocokkan</h4>
                            <p class="text-xs text-slate-500">Pasangkan istilah penting lempar cakram dengan definisi atau penjelasannya secara tepat.</p>
                        </div>
                        <div class="mt-6 flex items-center justify-between pt-4 border-t border-slate-100">
                            <span id="score-badge-matching" class="text-xs font-bold px-2.5 py-1 bg-slate-100 text-slate-700 rounded-full">Belum Dimainkan</span>
                            <span class="text-sm font-bold text-blue-600 group-hover:translate-x-1 transition-transform">Mainkan &rarr;</span>
                        </div>
                    </div>

                    <!-- Game 2 Card -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between hover:border-orange-500 transition-all cursor-pointer group" onclick="startDragDropGame()">
                        <div>
                            <div class="bg-orange-50 text-orange-600 p-3 rounded-xl w-fit mb-4 group-hover:bg-orange-500 group-hover:text-white transition-all">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4"></path></svg>
                            </div>
                            <h4 class="font-bold text-navy-900 text-lg mb-1">Permainan 2: Urutan Teknik</h4>
                            <p class="text-xs text-slate-500">Susun tahapan teknik dasar lempar cakram mulai dari awal hingga pemulihan dengan benar.</p>
                        </div>
                        <div class="mt-6 flex items-center justify-between pt-4 border-t border-slate-100">
                            <span id="score-badge-dragdrop" class="text-xs font-bold px-2.5 py-1 bg-slate-100 text-slate-700 rounded-full">Belum Dimainkan</span>
                            <span class="text-sm font-bold text-orange-600 group-hover:translate-x-1 transition-transform">Mainkan &rarr;</span>
                        </div>
                    </div>

                    <!-- Game 3 Card (Quiz) -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between hover:border-emerald-500 transition-all cursor-pointer group" onclick="startQuiz()">
                        <div>
                            <div class="bg-emerald-50 text-emerald-600 p-3 rounded-xl w-fit mb-4 group-hover:bg-emerald-600 group-hover:text-white transition-all">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                            </div>
                            <h4 class="font-bold text-navy-900 text-lg mb-1">Kuis Pilihan Ganda</h4>
                            <p class="text-xs text-slate-500">Uji pengetahuan dengan 10 soal komprehensif tentang teori dan praktik lempar cakram.</p>
                        </div>
                        <div class="mt-6 flex items-center justify-between pt-4 border-t border-slate-100">
                            <span id="score-badge-quiz" class="text-xs font-bold px-2.5 py-1 bg-slate-100 text-slate-700 rounded-full">Belum Dimainkan</span>
                            <span class="text-sm font-bold text-emerald-600 group-hover:translate-x-1 transition-transform">Mulai Kuis &rarr;</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- MATCHING GAME MODAL/CONTAINER -->
            <div id="game-matching-container" class="hidden bg-white p-6 sm:p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="flex items-center justify-between border-b border-slate-100 pb-4">
                    <div>
                        <span class="text-xs font-bold text-blue-600 uppercase">Permainan 1</span>
                        <h3 class="text-xl font-extrabold text-navy-900">Mencocokkan Istilah & Definisi</h3>
                    </div>
                    <button onclick="closeActiveGame()" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-xl text-xs font-bold">Kembali ke Menu</button>
                </div>
                <p class="text-sm text-slate-600">Klik sebuah istilah di kolom kiri, lalu klik definisi yang sesuai di kolom kanan untuk memasangkannya.</p>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="space-y-3">
                        <h4 class="font-bold text-slate-900 text-sm">Istilah</h4>
                        <div id="matching-terms-list" class="space-y-2"></div>
                    </div>
                    <div class="space-y-3">
                        <h4 class="font-bold text-slate-900 text-sm">Definisi</h4>
                        <div id="matching-defs-list" class="space-y-2"></div>
                    </div>
                </div>

                <div id="matching-result-box" class="hidden p-4 rounded-2xl bg-emerald-50 text-emerald-800 text-center font-bold text-sm"></div>

                <div class="flex justify-end pt-4 border-t border-slate-100">
                    <button onclick="initMatchingGame()" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold rounded-xl text-sm">Ulangi Permainan</button>
                </div>
            </div>

            <!-- DRAG & DROP / ORDER GAME CONTAINER -->
            <div id="game-dragdrop-container" class="hidden bg-white p-6 sm:p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="flex items-center justify-between border-b border-slate-100 pb-4">
                    <div>
                        <span class="text-xs font-bold text-orange-600 uppercase">Permainan 2</span>
                        <h3 class="text-xl font-extrabold text-navy-900">Susun Urutan Teknik Lempar Cakram</h3>
                    </div>
                    <button onclick="closeActiveGame()" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-xl text-xs font-bold">Kembali ke Menu</button>
                </div>
                <p class="text-sm text-slate-600">Seret kartu atau gunakan tombol panah (Naik/Turun) untuk menyusun tahapan teknik lempar cakram dari awal hingga akhir dengan benar.</p>
                
                <div id="dragdrop-list" class="space-y-3"></div>

                <div id="dragdrop-result-box" class="hidden p-4 rounded-2xl text-center font-bold text-sm"></div>

                <div class="flex items-center justify-between pt-4 border-t border-slate-100">
                    <button onclick="initDragDropGame()" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold rounded-xl text-sm">Acak Ulang</button>
                    <button onclick="checkDragDropAnswer()" class="px-6 py-2.5 bg-orange-500 hover:bg-orange-600 text-white font-bold rounded-xl text-sm shadow-md">Periksa Jawaban</button>
                </div>
            </div>

            <!-- QUIZ CONTAINER -->
            <div id="game-quiz-container" class="hidden bg-white p-6 sm:p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="flex items-center justify-between border-b border-slate-100 pb-4">
                    <div>
                        <span class="text-xs font-bold text-emerald-600 uppercase">Kuis Pilihan Ganda</span>
                        <h3 id="quiz-title-header" class="text-xl font-extrabold text-navy-900">Evaluasi Pemahaman Lempar Cakram</h3>
                    </div>
                    <button onclick="closeActiveGame()" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-xl text-xs font-bold">Keluar Kuis</button>
                </div>

                <!-- Quiz Question Box -->
                <div id="quiz-question-card" class="space-y-4">
                    <div class="flex items-center justify-between">
                        <span id="quiz-progress-indicator" class="text-xs font-bold px-3 py-1 bg-emerald-50 text-emerald-700 rounded-full">Soal 1 dari 10</span>
                        <span id="quiz-score-live" class="text-xs font-bold text-slate-500">Skor: 0</span>
                    </div>
                    <h4 id="quiz-question-text" class="text-lg font-bold text-navy-900 leading-snug">Pertanyaan akan dimuat di sini...</h4>
                    <div id="quiz-options-list" class="space-y-3 pt-2"></div>
                </div>

                <!-- Quiz Result Summary Card -->
                <div id="quiz-result-card" class="hidden text-center space-y-6 py-6">
                    <div class="inline-flex bg-emerald-100 text-emerald-700 p-4 rounded-full">
                        <svg class="w-12 h-12" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                    </div>
                    <div class="space-y-2">
                        <h3 class="text-2xl font-extrabold text-navy-900">Kuis Selesai!</h3>
                        <p class="text-slate-600 text-sm">Terima kasih telah menyelesaikan evaluasi pembelajaran lempar cakram.</p>
                    </div>
                    <div class="bg-slate-50 p-6 rounded-2xl max-w-sm mx-auto border border-slate-200 space-y-2">
                        <p class="text-sm font-medium text-slate-600">Nilai Akhir Anda:</p>
                        <p id="quiz-final-score-val" class="text-4xl font-extrabold text-navy-900">0</p>
                        <p id="quiz-final-percent-val" class="text-xs font-semibold text-emerald-600">Persentase benar: 0%</p>
                    </div>
                    <div class="flex justify-center space-x-3">
                        <button onclick="startQuiz()" class="px-6 py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-bold rounded-xl text-sm shadow-md">Ulangi Kuis</button>
                        <button onclick="closeActiveGame()" class="px-6 py-3 bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold rounded-xl text-sm">Kembali ke Menu</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- VIEW: SKOR (SCORES & HISTORY) -->
        <section id="view-scores" class="view-section hidden fade-in space-y-6">
            <div class="bg-white p-6 sm:p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="flex flex-col sm:flex-row sm:items-center justify-between pb-6 border-b border-slate-100 gap-4">
                    <div>
                        <span class="text-xs font-bold text-emerald-600 uppercase">Rekapitulasi Nilai</span>
                        <h2 class="text-2xl sm:text-3xl font-extrabold text-navy-900">Riwayat Skor & Progres</h2>
                    </div>
                    <div class="flex items-center space-x-3">
                        <button onclick="confirmClearScores()" class="px-4 py-2.5 bg-rose-50 hover:bg-rose-100 text-rose-700 font-bold rounded-xl text-xs transition-all border border-rose-200">Hapus Riwayat Skor</button>
                        <button onclick="confirmResetProgress()" class="px-4 py-2.5 bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold rounded-xl text-xs transition-all border border-slate-200">Reset Progres Belajar</button>
                    </div>
                </div>

                <!-- Participant Info Summary -->
                <div class="bg-slate-50 p-6 rounded-2xl border border-slate-200 grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <div>
                        <p class="text-xs font-bold text-slate-400 uppercase">Nama Peserta</p>
                        <p id="score-view-name" class="text-base font-extrabold text-navy-900 mt-0.5">Belum Login</p>
                    </div>
                    <div>
                        <p class="text-xs font-bold text-slate-400 uppercase">Sekolah</p>
                        <p id="score-view-school" class="text-base font-extrabold text-navy-900 mt-0.5">-</p>
                    </div>
                    <div>
                        <p class="text-xs font-bold text-slate-400 uppercase">Total Akumulasi Skor</p>
                        <p id="score-view-total" class="text-xl font-extrabold text-orange-600 mt-0.5">0 Poin</p>
                    </div>
                </div>

                <!-- History Table / Cards -->
                <div class="space-y-3">
                    <h3 class="font-bold text-navy-900 text-base">Riwayat Latihan Tersimpan</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-700 text-xs font-bold uppercase tracking-wider">
                                    <th class="p-3.5 rounded-l-xl">Tanggal & Waktu</th>
                                    <th class="p-3.5">Mencocokkan</th>
                                    <th class="p-3.5">Urutan Teknik</th>
                                    <th class="p-3.5">Kuis</th>
                                    <th class="p-3.5 rounded-r-xl">Total Skor</th>
                                </tr>
                            </thead>
                            <tbody id="score-history-tbody" class="text-sm font-medium text-slate-600">
                                <!-- Populated by JS -->
                            </tbody>
                        </table>
                    </div>
                    <p class="text-xs text-slate-400 italic pt-2">Catatan: Data tersimpan secara lokal di browser perangkat Anda dan tidak otomatis tersinkron ke perangkat lain.</p>
                </div>
            </div>
        </section>

        <!-- VIEW: PENGEMBANG (DEVELOPER) -->
        <section id="view-developer" class="view-section hidden fade-in space-y-6">
            <div class="max-w-3xl mx-auto bg-white p-8 rounded-3xl shadow-xl border border-slate-200 space-y-6">
                <div class="text-center space-y-2 pb-6 border-b border-slate-100">
                    <div class="inline-flex bg-blue-50 text-blue-600 p-4 rounded-2xl mb-1 shadow-sm">
                        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path></svg>
                    </div>
                    <h2 class="text-2xl font-extrabold text-navy-900">Tentang Pengembang</h2>
                    <p class="text-sm text-slate-500">Informasi identitas pembuat media pembelajaran interaktif.</p>
                </div>

                <!-- Developer Details Card -->
                <div class="bg-slate-50 p-6 rounded-2xl border border-slate-200 space-y-4 text-sm">
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Nama Pengembang</p>
                            <p id="dev-name" class="font-bold text-navy-900 text-base mt-0.5">[ISI NAMA PENULIS]</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">NIM / Nomor Induk</p>
                            <p id="dev-nim" class="font-bold text-navy-900 text-base mt-0.5">[ISI NIM]</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Program Studi</p>
                            <p id="dev-prodi" class="font-bold text-navy-900 text-base mt-0.5">[ISI PROGRAM STUDI]</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Institusi / Universitas</p>
                            <p id="dev-institution" class="font-bold text-navy-900 text-base mt-0.5">[ISI NAMA INSTITUSI]</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Mata Pelajaran</p>
                            <p class="font-bold text-navy-900 text-base mt-0.5">PJOK</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Materi</p>
                            <p class="font-bold text-navy-900 text-base mt-0.5">Atletik – Lempar Cakram</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Jenjang Kelas</p>
                            <p class="font-bold text-navy-900 text-base mt-0.5">Kelas XII SMA</p>
                        </div>
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase">Tahun Pembuatan</p>
                            <p class="font-bold text-navy-900 text-base mt-0.5">2026</p>
                        </div>
                    </div>
                </div>

                <div class="p-5 bg-blue-50/50 rounded-2xl border border-blue-100 text-slate-600 text-sm leading-relaxed">
                    <p class="font-bold text-navy-900 mb-1">Deskripsi Media Pembelajaran:</p>
                    "Media pembelajaran interaktif ini dikembangkan sebagai sarana belajar mandiri untuk membantu siswa memahami konsep dan teknik dasar lempar cakram melalui materi visual dan latihan berbasis permainan."
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-navy-900 text-slate-400 py-8 mt-12 border-t border-slate-800 text-center text-xs">
        <div class="max-w-7xl mx-auto px-4 space-y-2">
            <p class="font-semibold text-slate-300">MEDIA PEMBELAJARAN INTERAKTIF ATLETIK: LEMPAR CAKRAM</p>
            <p>Pendidikan Jasmani, Olahraga, dan Kesehatan (PJOK) Kelas XII SMA &copy; 2026</p>
        </div>
    </footer>

    <!-- JavaScript Application Logic -->
    <script>
        // --- DEVELOPER CONFIGURATION VARIABLES ---
        const DEVELOPER_CONFIG = {
            name: "Ahmad Fauzi, S.Pd.",
            nim: "2201982736",
            prodi: "Pendidikan Jasmani dan Kesehatan",
            institution: "Universitas Negeri Pendidikan Indonesia"
        };

        // --- LOCAL STORAGE STATE MANAGEMENT ---
        const STORAGE_KEY = "pjok_lempar_cakram_v1";
        
        let appState = {
            studentName: "",
            studentSchool: "",
            learningProgress: {
                subA: false,
                subB: false,
                subC: false,
                subD: false
            },
            scores: {
                matching: 0,
                dragdrop: 0,
                quiz: 0
            },
            history: [],
            audioEnabled: true
        };

        function loadAppData() {
            try {
                const saved = localStorage.getItem(STORAGE_KEY);
                if (saved) {
                    const parsed = JSON.parse(saved);
                    appState = { ...appState, ...parsed };
                }
            } catch (e) {
                console.error("Error loading local storage data", e);
            }
        }

        function saveAppData() {
            try {
                localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));
            } catch (e) {
                console.error("Error saving local storage data", e);
            }
        }

        // --- WEB AUDIO API SOUND SYNTHESIZER ---
        let audioCtx = null;

        function getAudioContext() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
            return audioCtx;
        }

        function playSound(type) {
            if (!appState.audioEnabled) return;
            try {
                const ctx = getAudioContext();
                const osc = ctx.createOscillator();
                const gain = ctx.createGain();
                osc.connect(gain);
                gain.connect(ctx.destination);

                const now = ctx.currentTime;

                if (type === 'click') {
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(400, now);
                    osc.frequency.exponentialRampToValueAtTime(200, now + 0.08);
                    gain.gain.setValueAtTime(0.1, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.08);
                    osc.start(now);
                    osc.stop(now + 0.08);
                } else if (type === 'correct') {
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(523.25, now); // C5
                    osc.frequency.setValueAtTime(659.25, now + 0.1); // E5
                    gain.gain.setValueAtTime(0.15, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
                    osc.start(now);
                    osc.stop(now + 0.3);
                } else if (type === 'wrong') {
                    osc.type = 'sawtooth';
                    osc.frequency.setValueAtTime(180, now);
                    osc.frequency.setValueAtTime(120, now + 0.15);
                    gain.gain.setValueAtTime(0.15, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
                    osc.start(now);
                    osc.stop(now + 0.3);
                } else if (type === 'success') {
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(440, now);
                    osc.frequency.setValueAtTime(554.37, now + 0.1);
                    osc.frequency.setValueAtTime(659.25, now + 0.2);
                    osc.frequency.setValueAtTime(880, now + 0.3);
                    gain.gain.setValueAtTime(0.2, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.6);
                    osc.start(now);
                    osc.stop(now + 0.6);
                }
            } catch (e) {
                console.log("Audio playback error", e);
            }
        }

        function toggleAudio() {
            appState.audioEnabled = !appState.audioEnabled;
            saveAppData();
            updateAudioUI();
            if (appState.audioEnabled) playSound('click');
        }

        function updateAudioUI() {
            const iconOn = document.getElementById('audio-icon-on');
            const iconOff = document.getElementById('audio-icon-off');
            if (appState.audioEnabled) {
                iconOn.classList.remove('hidden');
                iconOff.classList.add('hidden');
            } else {
                iconOn.classList.add('hidden');
                iconOff.classList.remove('hidden');
            }
        }

        // --- FULLSCREEN API ---
        function toggleFullscreen() {
            playSound('click');
            if (!document.fullscreenElement) {
                document.documentElement.requestFullscreen().catch(err => {
                    alert("Fullscreen mode tidak didukung browser ini.");
                });
            } else {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                }
            }
        }

        // --- NAVIGATION & VIEWS ---
        function switchView(viewId) {
            playSound('click');
            document.querySelectorAll('.view-section').forEach(sec => sec.classList.add('hidden'));
            document.getElementById(`view-${viewId}`).classList.remove('hidden');
            
            // Highlight nav
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('bg-slate-800', 'text-white'));
            const activeBtn = document.getElementById(`nav-${viewId}`);
            if (activeBtn) activeBtn.classList.add('bg-slate-800', 'text-white');

            window.scrollTo({ top: 0, behavior: 'smooth' });

            if (viewId === 'dashboard') updateDashboardUI();
            if (viewId === 'scores') renderScoreHistory();
        }

        function toggleMobileMenu() {
            playSound('click');
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // --- LEARNING MODULE LOGIC ---
        let currentSubTab = 'subA';

        function switchSubTab(subId) {
            playSound('click');
            currentSubTab = subId;
            document.querySelectorAll('.subtab-content').forEach(c => c.classList.add('hidden'));
            document.getElementById(`content-${subId}`).classList.remove('hidden');

            document.querySelectorAll('.subtab-btn').forEach(b => {
                b.classList.remove('bg-blue-600', 'text-white');
                b.classList.add('bg-slate-100', 'text-slate-700');
            });
            const activeBtn = document.getElementById(`btn-${subId}`);
            activeBtn.classList.remove('bg-slate-100', 'text-slate-700');
            activeBtn.classList.add('bg-blue-600', 'text-white');

            // Sync checkbox state
            const checkbox = document.getElementById('learning-checkbox');
            checkbox.checked = !!appState.learningProgress[subId];
        }

        function navigateSubTab(direction) {
            const subs = ['subA', 'subB', 'subC', 'subD'];
            let idx = subs.indexOf(currentSubTab) + direction;
            if (idx >= 0 && idx < subs.length) {
                switchSubTab(subs[idx]);
            }
        }

        function updateLearningProgress() {
            playSound('click');
            const checkbox = document.getElementById('learning-checkbox');
            appState.learningProgress[currentSubTab] = checkbox.checked;
            saveAppData();
            updateDashboardUI();
        }

        // --- DASHBOARD & LOGIN LOGIC ---
        function updateDashboardUI() {
            // Learning progress percentage
            const progress = appState.learningProgress;
            const completedCount = Object.values(progress).filter(Boolean).length;
            const percent = Math.round((completedCount / 4) * 100);
            
            document.getElementById('dash-learning-percent').innerText = `${percent}% Selesai`;
            document.getElementById('dash-learning-bar').style.width = `${percent}%`;

            // Student login info
            const nameEl = document.getElementById('dash-student-name');
            const schoolEl = document.getElementById('dash-student-school');
            const badgeEl = document.getElementById('dash-login-badge');
            const btnText = document.getElementById('dash-play-btn-text');

            if (appState.studentName) {
                nameEl.innerText = appState.studentName;
                schoolEl.innerText = appState.studentSchool;
                badgeEl.innerText = 'Sudah Login';
                badgeEl.className = 'text-xs font-bold px-2.5 py-1 bg-emerald-50 text-emerald-700 rounded-full';
                btnText.innerText = 'Lanjutkan Bermain';
            } else {
                nameEl.innerText = '-';
                schoolEl.innerText = '-';
                badgeEl.innerText = 'Belum Login';
                badgeEl.className = 'text-xs font-bold px-2.5 py-1 bg-amber-50 text-amber-700 rounded-full';
                btnText.innerText = 'Mulai Bermain / Masuk';
            }

            // Top score
            const topScore = Math.max(appState.scores.matching, appState.scores.dragdrop, appState.scores.quiz, 0);
            document.getElementById('dash-top-score').innerText = topScore;
        }

        function checkLoginAndPlay() {
            playSound('click');
            switchView('play');
            if (appState.studentName) {
                document.getElementById('play-login-card').classList.add('hidden');
                document.getElementById('play-menu-card').classList.remove('hidden');
                document.getElementById('welcome-student-display').innerText = appState.studentName;
                document.getElementById('welcome-school-display').innerText = appState.studentSchool;
                updateGameBadges();
            } else {
                document.getElementById('play-login-card').classList.remove('hidden');
                document.getElementById('play-menu-card').classList.add('hidden');
            }
        }

        function handleStudentLogin() {
            playSound('click');
            const name = document.getElementById('input-student-name').value.trim();
            const school = document.getElementById('input-student-school').value.trim();
            const errBox = document.getElementById('login-error-msg');

            if (!name || !school) {
                playSound('wrong');
                errBox.innerText = "Nama lengkap dan nama sekolah wajib diisi!";
                errBox.classList.remove('hidden');
                return;
            }

            errBox.classList.add('hidden');
            appState.studentName = name;
            appState.studentSchool = school;
            saveAppData();

            document.getElementById('play-login-card').classList.add('hidden');
            document.getElementById('play-menu-card').classList.remove('hidden');
            document.getElementById('welcome-student-display').innerText = name;
            document.getElementById('welcome-school-display').innerText = school;
            updateDashboardUI();
            updateGameBadges();
        }

        function resetStudentLogin() {
            playSound('click');
            appState.studentName = "";
            appState.studentSchool = "";
            saveAppData();
            document.getElementById('input-student-name').value = "";
            document.getElementById('input-student-school').value = "";
            document.getElementById('play-login-card').classList.remove('hidden');
            document.getElementById('play-menu-card').classList.add('hidden');
            updateDashboardUI();
        }

        function updateGameBadges() {
            const mBadge = document.getElementById('score-badge-matching');
            const dBadge = document.getElementById('score-badge-dragdrop');
            const qBadge = document.getElementById('score-badge-quiz');

            if (appState.scores.matching > 0) {
                mBadge.innerText = `Skor: ${appState.scores.matching}`;
                mBadge.className = 'text-xs font-bold px-2.5 py-1 bg-emerald-50 text-emerald-700 rounded-full';
            }
            if (appState.scores.dragdrop > 0) {
                dBadge.innerText = `Skor: ${appState.scores.dragdrop}`;
                dBadge.className = 'text-xs font-bold px-2.5 py-1 bg-emerald-50 text-emerald-700 rounded-full';
            }
            if (appState.scores.quiz > 0) {
                qBadge.innerText = `Skor: ${appState.scores.quiz}`;
                qBadge.className = 'text-xs font-bold px-2.5 py-1 bg-emerald-50 text-emerald-700 rounded-full';
            }
        }

        function closeActiveGame() {
            playSound('click');
            document.getElementById('game-matching-container').classList.add('hidden');
            document.getElementById('game-dragdrop-container').classList.add('hidden');
            document.getElementById('game-quiz-container').classList.add('hidden');
            document.getElementById('play-menu-card').classList.remove('hidden');
            updateGameBadges();
        }

        // --- GAME 1: MATCHING GAME ---
        const matchingPairs = [
            { term: "Cakram", def: "Alat berbentuk piringan yang digunakan dalam nomor lempar cakram." },
            { term: "Lingkaran lempar", def: "Area berdiameter 2,5 meter tempat atlet melakukan gerakan melempar." },
            { term: "Sangkar pelindung", def: "Struktur pengaman berbentuk huruf U di sekitar area lempar." },
            { term: "Sudut pelepasan", def: "Sudut elevasi cakram ketika dilepaskan dari tangan (sekitar 30-35 derajat)." },
            { term: "Sikap akhir", def: "Gerakan menjaga keseimbangan setelah cakram dilepaskan agar tidak keluar lingkaran." }
        ];

        let selectedTerm = null;
        let matchedCount = 0;

        function startMatchingGame() {
            playSound('click');
            document.getElementById('play-menu-card').classList.add('hidden');
            document.getElementById('game-matching-container').classList.remove('hidden');
            initMatchingGame();
        }

        function initMatchingGame() {
            playSound('click');
            selectedTerm = null;
            matchedCount = 0;
            document.getElementById('matching-result-box').classList.add('hidden');

            const shuffledTerms = [...matchingPairs].sort(() => Math.random() - 0.5);
            const shuffledDefs = [...matchingPairs].sort(() => Math.random() - 0.5);

            const termsContainer = document.getElementById('matching-terms-list');
            const defsContainer = document.getElementById('matching-defs-list');
            termsContainer.innerHTML = '';
            defsContainer.innerHTML = '';

            shuffledTerms.forEach((item, idx) => {
                const btn = document.createElement('button');
                btn.className = 'w-full text-left p-3.5 bg-slate-50 hover:bg-slate-100 border border-slate-200 rounded-xl text-sm font-bold text-navy-900 transition-all';
                btn.innerText = item.term;
                btn.dataset.term = item.term;
                btn.onclick = () => selectMatchingTerm(item.term, btn);
                termsContainer.appendChild(btn);
            });

            shuffledDefs.forEach((item, idx) => {
                const btn = document.createElement('button');
                btn.className = 'w-full text-left p-3.5 bg-slate-50 hover:bg-slate-100 border border-slate-200 rounded-xl text-sm font-medium text-slate-700 transition-all';
                btn.innerText = item.def;
                btn.dataset.def = item.def;
                btn.onclick = () => selectMatchingDef(item.def, btn);
                defsContainer.appendChild(btn);
            });
        }

        function selectMatchingTerm(term, btnElem) {
            playSound('click');
            document.querySelectorAll('#matching-terms-list button').forEach(b => b.classList.remove('border-blue-500', 'bg-blue-50'));
            if (btnElem.dataset.matched !== 'true') {
                btnElem.classList.add('border-blue-500', 'bg-blue-50');
                selectedTerm = term;
            }
        }

        function selectMatchingDef(def, btnElem) {
            if (!selectedTerm) return;
            const correctPair = matchingPairs.find(p => p.term === selectedTerm);
            
            if (correctPair && correctPair.def === def) {
                playSound('correct');
                // Correct match
                const termBtn = Array.from(document.querySelectorAll('#matching-terms-list button')).find(b => b.dataset.term === selectedTerm);
                termBtn.classList.remove('border-blue-500', 'bg-blue-50');
                termBtn.classList.add('bg-emerald-50', 'border-emerald-500', 'text-emerald-900');
                termBtn.dataset.matched = 'true';
                termBtn.disabled = true;

                btnElem.classList.add('bg-emerald-50', 'border-emerald-500', 'text-emerald-900');
                btnElem.disabled = true;

                selectedTerm = null;
                matchedCount++;

                if (matchedCount === matchingPairs.length) {
                    playSound('success');
                    const score = 100;
                    appState.scores.matching = score;
                    recordSessionScore();
                    const resBox = document.getElementById('matching-result-box');
                    resBox.innerText = `Luar Biasa! Semua pasangan cocok. Skor Anda: ${score}`;
                    resBox.classList.remove('hidden');
                }
            } else {
                playSound('wrong');
                btnElem.classList.add('bg-rose-50', 'border-rose-500');
                setTimeout(() => btnElem.classList.remove('bg-rose-50', 'border-rose-500'), 500);
            }
        }

        // --- GAME 2: DRAG & DROP / ORDER ARRANGEMENT ---
        const correctStages = [
            { id: 1, text: "1. Memegang cakram (posisi jari dan tangan)" },
            { id: 2, text: "2. Mengambil posisi awal & ayunan pendahuluan" },
            { id: 3, text: "3. Melakukan putaran badan (rotasi) & koordinasi" },
            { id: 4, text: "4. Melepaskan cakram dengan sudut optimal" },
            { id: 5, text: "5. Menjaga keseimbangan (sikap akhir & pemulihan)" }
        ];

        let currentStagesOrder = [];

        function startDragDropGame() {
            playSound('click');
            document.getElementById('play-menu-card').classList.add('hidden');
            document.getElementById('game-dragdrop-container').classList.remove('hidden');
            initDragDropGame();
        }

        function initDragDropGame() {
            playSound('click');
            currentStagesOrder = [...correctStages].sort(() => Math.random() - 0.5);
            document.getElementById('dragdrop-result-box').classList.add('hidden');
            renderDragDropList();
        }

        function renderDragDropList() {
            const container = document.getElementById('dragdrop-list');
            container.innerHTML = '';
            currentStagesOrder.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = 'flex items-center justify-between p-4 bg-slate-50 border border-slate-200 rounded-2xl shadow-sm text-sm font-bold text-navy-900';
                div.innerHTML = `
                    <div class="flex items-center space-x-3">
                        <span class="w-7 h-7 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center text-xs">${index + 1}</span>
                        <span>${item.text}</span>
                    </div>
                    <div class="flex items-center space-x-1">
                        <button onclick="moveStage(${index}, -1)" class="p-2 bg-white hover:bg-slate-200 border border-slate-300 rounded-lg text-slate-700 text-xs" title="Naik">&uarr;</button>
                        <button onclick="moveStage(${index}, 1)" class="p-2 bg-white hover:bg-slate-200 border border-slate-300 rounded-lg text-slate-700 text-xs" title="Turun">&darr;</button>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        function moveStage(index, direction) {
            playSound('click');
            const targetIdx = index + direction;
            if (targetIdx >= 0 && targetIdx < currentStagesOrder.length) {
                const temp = currentStagesOrder[index];
                currentStagesOrder[index] = currentStagesOrder[targetIdx];
                currentStagesOrder[targetIdx] = temp;
                renderDragDropList();
            }
        }

        function checkDragDropAnswer() {
            playSound('click');
            let isCorrect = true;
            for (let i = 0; i < currentStagesOrder.length; i++) {
                if (currentStagesOrder[i].id !== correctStages[i].id) {
                    isCorrect = false;
                    break;
                }
            }

            const resBox = document.getElementById('dragdrop-result-box');
            resBox.classList.remove('hidden');

            if (isCorrect) {
                playSound('success');
                appState.scores.dragdrop = 100;
                recordSessionScore();
                resBox.className = 'p-4 rounded-2xl bg-emerald-50 text-emerald-800 font-bold text-sm text-center';
                resBox.innerText = "Sempurna! Urutan tahapan teknik lempar cakram sudah benar. Skor: 100";
            } else {
                playSound('wrong');
                resBox.className = 'p-4 rounded-2xl bg-rose-50 text-rose-800 font-bold text-sm text-center';
                resBox.innerText = "Urutan belum tepat. Silakan periksa kembali tahapan teknik dari awal hingga pemulihan.";
            }
        }

        // --- GAME 3: QUIZ (10 QUESTIONS) ---
        const quizQuestionsBank = [
            {
                q: "Apa tujuan utama dalam perlombaan lempar cakram?",
                options: ["Melempar sejauh mungkin ke sektor sah", "Melempar setinggi mungkin ke udara", "Menangkap kembali cakram yang dilempar", "Melompati sangkar pelindung"],
                answer: 0,
                explanation: "Tujuan utama lempar cakram adalah mencapai jarak lemparan terjauh yang sah di dalam sektor."
            },
            {
                q: "Berapa sudut standar sektor pendaratan lempar cakram?",
                options: ["45 derajat", "34,92 derajat", "90 derajat", "180 derajat"],
                answer: 1,
                explanation: "Sektor pendaratan lempar cakram resmi membentuk sudut 34,92 derajat dari pusat lingkaran."
            },
            {
                q: "Berapa diameter lingkaran lempar cakram resmi?",
                options: ["1,5 meter", "2,0 meter", "2,5 meter", "3,0 meter"],
                answer: 2,
                explanation: "Lingkaran lempar cakram memiliki diameter dalam 2,5 meter."
            },
            {
                q: "Bagaimana cara memegang cakram yang benar pada ruas jari?",
                options: ["Dipegang erat di telapak tangan", "Diletakkan pada ruas jari-jari terakhir", "Dijepit menggunakan dua jari saja", "Dipegang menggunakan sarung tangan"],
                answer: 1,
                explanation: "Cakram diletakkan pada ruas jari terakhir dengan jari diregangkan menutupi tepi cakram."
            },
            {
                q: "Berapa berat cakram untuk kompetisi resmi kategori senior putra?",
                options: ["1 kg", "1,5 kg", "2 kg", "3 kg"],
                answer: 2,
                explanation: "Berat cakram resmi untuk senior putra adalah 2 kg."
            },
            {
                q: "Berapa berat cakram untuk kompetisi resmi kategori senior putri?",
                options: ["1 kg", "1,5 kg", "2 kg", "0,75 kg"],
                answer: 0,
                explanation: "Berat cakram resmi untuk senior putri adalah 1 kg."
            },
            {
                q: "Berapa kisaran sudut pelepasan (release angle) yang optimal saat melempar cakram?",
                options: ["10 - 15 derajat", "30 - 35 derajat", "60 - 75 derajat", "85 - 90 derajat"],
                answer: 1,
                explanation: "Sudut pelepasan optimal untuk lempar cakram adalah sekitar 30 hingga 35 derajat."
            },
            {
                q: "Kesalahan apa yang menyebabkan atlet didiskualifikasi setelah melempar?",
                options: ["Berteriak saat melempar", "Melangkah keluar melalui garis depan lingkaran", "Memakai pakaian olahraga berwarna cerah", "Melakukan putaran sebanyak dua kali"],
                answer: 1,
                explanation: "Atlet didiskualifikasi jika melangkah keluar melewati garis depan lingkaran lempar."
            },
            {
                q: "Dari mana asal sejarah awal olahraga lempar cakram?",
                options: ["Olimpiade Kuno Yunani", "Festival Romawi Kuno", "Kejuaraan Tradisional Mesir", "Pekan Olahraga Modern Eropa Abad ke-19"],
                answer: 0,
                explanation: "Lempar cakram berasal dari tradisi Olimpiade Kuno di Yunani."
            },
            {
                q: "Apa fungsi utama sangkar pelindung (cage) di area lempar?",
                options: ["Menghias lapangan atletik", "Melindungi penonton dan juri dari lemparan liar", "Mengarahkan angin ke sektor lemparan", "Menyimpan alat cakram"],
                answer: 1,
                explanation: "Sangkar pelindung berfungsi untuk keselamatan penonton, ofisial, dan atlet lain."
            }
        ];

        let activeQuizQuestions = [];
        let currentQuizIndex = 0;
        let currentQuizScore = 0;

        function startQuiz() {
            playSound('click');
            document.getElementById('play-menu-card').classList.add('hidden');
            document.getElementById('game-quiz-container').classList.remove('hidden');
            document.getElementById('quiz-question-card').classList.remove('hidden');
            document.getElementById('quiz-result-card').classList.add('hidden');

            // Randomize question order and options
            activeQuizQuestions = JSON.parse(JSON.stringify(quizQuestionsBank)).sort(() => Math.random() - 0.5);
            currentQuizIndex = 0;
            currentQuizScore = 0;
            renderQuizQuestion();
        }

        function renderQuizQuestion() {
            if (currentQuizIndex >= activeQuizQuestions.length) {
                finishQuiz();
                return;
            }

            const qData = activeQuizQuestions[currentQuizIndex];
            document.getElementById('quiz-progress-indicator').innerText = `Soal ${currentQuizIndex + 1} dari ${activeQuizQuestions.length}`;
            document.getElementById('quiz-score-live').innerText = `Skor: ${currentQuizScore}`;
            document.getElementById('quiz-question-text').innerText = qData.q;

            // Randomize options while keeping track of correct answer
            let optionsWithIndex = qData.options.map((opt, idx) => ({ text: opt, originalIdx: idx }));
            optionsWithIndex.sort(() => Math.random() - 0.5);

            const optionsList = document.getElementById('quiz-options-list');
            optionsList.innerHTML = '';

            optionsWithIndex.forEach((item) => {
                const btn = document.createElement('button');
                btn.className = 'w-full text-left p-4 bg-slate-50 hover:bg-slate-100 border border-slate-200 rounded-2xl text-sm font-semibold text-slate-800 transition-all';
                btn.innerText = item.text;
                btn.onclick = () => handleQuizAnswer(item.originalIdx === qData.answer, btn);
                optionsList.appendChild(btn);
            });
        }

        function handleQuizAnswer(isCorrect, selectedBtn) {
            // Disable all option buttons
            const buttons = document.querySelectorAll('#quiz-options-list button');
            buttons.forEach(b => b.disabled = true);

            if (isCorrect) {
                playSound('correct');
                selectedBtn.classList.remove('bg-slate-50', 'border-slate-200');
                selectedBtn.classList.add('bg-emerald-50', 'border-emerald-500', 'text-emerald-900');
                currentQuizScore += 10;
            } else {
                playSound('wrong');
                selectedBtn.classList.remove('bg-slate-50', 'border-slate-200');
                selectedBtn.classList.add('bg-rose-50', 'border-rose-500', 'text-rose-900');
            }

            setTimeout(() => {
                currentQuizIndex++;
                renderQuizQuestion();
            }, 1200);
        }

        function finishQuiz() {
            playSound('success');
            appState.scores.quiz = currentQuizScore;
            recordSessionScore();

            document.getElementById('quiz-question-card').classList.add('hidden');
            document.getElementById('quiz-result-card').classList.remove('hidden');

            document.getElementById('quiz-final-score-val').innerText = currentQuizScore;
            const percent = Math.round((currentQuizScore / (activeQuizQuestions.length * 10)) * 100);
            document.getElementById('quiz-final-percent-val').innerText = `Persentase benar: ${percent}%`;
        }

        // --- SCORE & HISTORY MANAGEMENT ---
        function recordSessionScore() {
            const total = appState.scores.matching + appState.scores.dragdrop + appState.scores.quiz;
            const now = new Date();
            const dateStr = now.toLocaleDateString('id-ID', { day: '2-digit', month: 'short', year: 'numeric', hour: '2-digit', minute: '2-digit' });
            
            const record = {
                date: dateStr,
                matching: appState.scores.matching,
                dragdrop: appState.scores.dragdrop,
                quiz: appState.scores.quiz,
                total: total
            };

            appState.history.unshift(record);
            saveAppData();
        }

        function renderScoreHistory() {
            document.getElementById('score-view-name').innerText = appState.studentName || "Belum Login";
            document.getElementById('score-view-school').innerText = appState.studentSchool || "-";
            
            const total = Math.max(appState.scores.matching, 0) + Math.max(appState.scores.dragdrop, 0) + Math.max(appState.scores.quiz, 0);
            document.getElementById('score-view-total').innerText = `${total} Poin`;

            const tbody = document.getElementById('score-history-tbody');
            tbody.innerHTML = '';

            if (appState.history.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" class="p-6 text-center text-slate-400 italic">Belum ada riwayat latihan tersimpan.</td></tr>`;
                return;
            }

            appState.history.forEach((item) => {
                const tr = document.createElement('tr');
                tr.className = 'border-b border-slate-100 hover:bg-slate-50 transition-all';
                tr.innerHTML = `
                    <td class="p-3.5 font-semibold text-slate-800">${item.date}</td>
                    <td class="p-3.5">${item.matching}</td>
                    <td class="p-3.5">${item.dragdrop}</td>
                    <td class="p-3.5">${item.quiz}</td>
                    <td class="p-3.5 font-extrabold text-navy-900">${item.total}</td>
                `;
                tbody.appendChild(tr);
            });
        }

        function confirmClearScores() {
            playSound('click');
            if (confirm("Apakah Anda yakin ingin menghapus seluruh riwayat skor?")) {
                playSound('success');
                appState.scores = { matching: 0, dragdrop: 0, quiz: 0 };
                appState.history = [];
                saveAppData();
                renderScoreHistory();
                updateDashboardUI();
            }
        }

        function confirmResetProgress() {
            playSound('click');
            if (confirm("Apakah Anda yakin ingin mereset progres belajar materi?")) {
                playSound('success');
                appState.learningProgress = { subA: false, subB: false, subC: false, subD: false };
                saveAppData();
                updateDashboardUI();
                switchSubTab('subA');
            }
        }

        // --- DEVELOPER INFO BINDING ---
        function initDeveloperInfo() {
            document.getElementById('dev-name').innerText = DEVELOPER_CONFIG.name;
            document.getElementById('dev-nim').innerText = DEVELOPER_CONFIG.nim;
            document.getElementById('dev-prodi').innerText = DEVELOPER_CONFIG.prodi;
            document.getElementById('dev-institution').innerText = DEVELOPER_CONFIG.institution;
        }

        // --- INITIALIZATION ---
        window.onload = function() {
            loadAppData();
            initDeveloperInfo();
            updateAudioUI();
            updateDashboardUI();
            switchSubTab('subA');
        };
    </script>
</body>
</html>
